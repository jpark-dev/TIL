# *Clean Code* by *Robert Cecil Martin*

## DAY 11 - 31/Jan/2022
## Mini project - Code refactoring

> Refactor the code below.

```
const merry = document.querySelector(".js-clock");

function getClock() {
const christmas = new Date("2021, 12, 25");
const date = new Date();
const timeGap = christmas - date;

const xDay = Math.floor(timeGap / (1000 * 60 * 60 * 24));
const xHours = Math.floor(
(timeGap - xDay * 1000 * 60 * 60 * 24) / (1000 * 60 * 60)
);
const xMinutes = Math.floor((timeGap % (60 * 60 * 1000)) / (60 * 1000));
const xSeconds = Math.floor((timeGap % (60 * 1000)) / 1000);

const day = String(xDay).padStart(2, "0");
const hours = String(xHours).padStart(2, "0");
const minutes = String(xMinutes).padStart(2, "0");
const seconds = String(xSeconds).padStart(2, "0");

merry.innerText = `${day}d ${hours}h ${minutes}m ${seconds}s`;
}

getClock();
setInterval(getClock, 1000);
```


Refactored to:

```
const timeContainer = document.querySelector(".js-clock");

const SECOND = 1000;
const MINUTE = SECOND * 60;
const HOUR = MINUTE * 60;
const DAY = HOUR * 24;

const SPECIAL_DAYS = {
  CHRISTMAS: '12-25',
};

const getCurrentTime = () => {
  return new Date();
}

const getYear = (time) => {
  return time.getFullYear();
};

const getThisYearsDate = (time, targetDate) => {
  const timeSuffix = 'T00:00:00';  
  return new Date(`${time}-${targetDate}${timeSuffix}`);
};

const getTimeLeft = () => {
  const now = getCurrentTime();
  const thisYear = getYear(now);
  const targetTime = getThisYearsDate(thisYear, SPECIAL_DAYS.CHRISTMAS);

  return targetTime - now;
};

const convertTimeFormat = (time) => {
  const days = Math.floor(time / DAY);
  const hours = Math.floor((time % DAY) / HOUR);
  const minutes = Math.floor((time % HOUR) / MINUTE);
  const seconds = Math.floor((time % MINUTE) / SECOND);

  return { days, hours, minutes, seconds };
}

const convertNumToTwoDigitString = (number) => {
  return number >= 10 ? number.toString() : `0${number}`;
};

const convertTimeToCustomText = ({ days, hours, minutes, seconds }) => {
  const dayText = convertNumToTwoDigitString(days);
  const hourText = convertNumToTwoDigitString(hours);
  const minuteText = convertNumToTwoDigitString(minutes);
  const secondText = convertNumToTwoDigitString(seconds);

  return `${dayText}d ${hourText}h ${minuteText}m ${secondText}s`
}

const displayTime = () => {
  const timeLeft = getTimeLeft();
  const formattedTimeLeft = convertTimeFormat(timeLeft);
  const textToDisplay = convertTimeToCustomText(formattedTimeLeft);
  
  timeContainer.innerText = textToDisplay;
}

setInterval(displayTime, 1000);
```
