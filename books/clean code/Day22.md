# *Clean Code* by *Robert Cecil Martin*

## DAY 22 - 10/Feb/2022
## Real-world examples of writing cleaner code

### Original Code
- This code was written in a final group project from my very first bootcamp back in 2015 - where users could search restaurants, rate, review and interact with the owners.

<a name="original_code"></a>
```js
function DownloadView() {
  setContentType("application/download);charset=utf-8");
}
// DetailController에서 전달해주는 모델값을 처리해주는 메소드
// 1.뷰에게 전달되는 Map객체(Model객체) 2.request 3.response객체

function renderMergedOutputModel(model, request, response) {
  // TODO Auto-generated method stub
  var file = (File) model.get("downloadFile");
  // 클라이언트가 받을 수 있도록 환경설정
  response.setContentType(getContentType());// 다운로드 화면
  response.setContentLength(file.length());// 다운로드 받은 파일의 길이
  // 브라우저의 종류 한글처리
  var userAgent = request.getHeader("User-Agent");// 브라우저 정보
  var ie = userAgent.indexOf("MSIE") > -1;
  var filename = null;// 다운로드 받을 파일명
  // IE라면
  if (ie) {
    filename = URLEncoder.encode(file.getName(), "utf-8");
  } else {// chrom,,, (영어->Iso-8859-1
    filename = new String(file.getName().getBytes("utf-8"), "iso-8859-1");

  }
  // 대화상자(위치경로, 파일명)
  response.setHeader("Content-Disposition", "attachment;filename=\"" + filename + "\";");
  response.setHeader("Content-Transfer-Encoding", "binary");// 이진파일
  var out = response.getOutputStream();
  var fis = null;

  try {
    fis = new FileInputStream(file);// 위치/파일정보
    // 파일전송->복사->FileCopyUtil이용
    FileCopyUtils.copy(fis, out);// 입력받는쪽,출력하는쪽
  } catch (IOException e) {
    e.printStackTrace();
  } finally { // 메모리를 해제하는 코딩
    if (fis != null) {
      try {
        fis.close();
      } catch (IOException e) {
        e.printStackTrace();
      }
    }
  }
  out.flush();// 출력하라(flush()->무조건 출력)
}
```

### CLEAN CODE!!!
<a name="refactored_code"></a>
```js
const getBrowserInfo = (req) => {
  return req.getHeader("User-Agent");
};

const getFileName = (req, file) => {
  const userBrowser = getBrowserInfo(req);
  const IE = userBrowser.indexOf("MSIE") > -1;
  const fileName = file.getName();

  return IE
    ? URLEncoder.encode(fileName, "utf-8")
    : new String(fileName.getBytes("utf-8"), "iso-8859-1");
};

const setContentData = (res, file) => {
  const contentType = "application/download;charset=utf-8";
  const contentLength = file.length();

  res.setContentType(contentType);
  res.setContentLength(contentLength);
};

const setResHeader = (res, fileName) => {
  res.setHeader("Content-Disposition", `attachment;filename="${fileName}";`);
  res.setHeader("Content-Transfer-Encoding", "binary");
};

const setResponseData = (req, res, file) => {
  const fileName = getFileName(req, file);

  setContentData(res, file);
  setResHeader(res, fileName);
};

const getInputStream = (file) => {
  return magicalInputStreamFinder(file);
};

const forcePrintStream = (fileStream) => {
  fileStream?.outputStream?.flush();
};

const handleError = (error) => {
  error.printStackTrace();
};

const copyFile = (inputStream, outputStream) => {
  FileCopyUtils.copy(inputStream, outputStream);
};

const releaseMemory = (inputStream) => {
  if (inputStream != null) {
    try {
      inputStream.close();
    } catch (error) {
      handleError();
    }
  }
};

const setHeaderAndCopy = (req, res, fileStream) => {
  const { downloadedFile, inputStream, outputStream } = fileStream;

  setResponseData(req, res, downloadedFile);
  copyFile(inputStream, outputStream);
};

const createFileStream = (res, downloadedFile, inputStream) => {
  const outputStream = res.getOutputStream();
  return {
    downloadedFile,
    inputStream,
    outputStream,
  }
};

const renderMergedOutputModel = (req, res, model) => {
  const downloadedFile = model.get("downloadFile");
  const inputStream = getInputStream(downloadedFile);
  const fileStream = createFileStream(res, downloadedFile, inputStream);

  try {
    setHeaderAndCopy(req, res, fileStream);
  } catch (error) {
    handleError();
  } finally {
    releaseMemory(inputStream);
  }
  forcePrintStream(fileStream);
};

```

### Applications
---
> 1. Single method in `try ~ catch` error handling.

From:
```js
try {
  fis = new FileInputStream(file);// 위치/파일정보
  // 파일전송->복사->FileCopyUtil이용
  FileCopyUtils.copy(fis, out);// 입력받는쪽,출력하는쪽
} catch (IOException e) {
  e.printStackTrace();
} finally { // 메모리를 해제하는 코딩
  if (fis != null) {
    try {
      fis.close();
    } catch (IOException e) {
      e.printStackTrace();
    }
  }
}
out.flush();// 출력하라(flush()->무조건 출력)
```
Refactored to:
```js
try {
  setHeaderAndCopy(req, res, fileStream);
} catch (error) {
  handleError();
} finally {
  releaseMemory(inputStream);
}
forcePrintStream(fileStream);
```
---
> 2. No comments unless absolutely necessary - the names should be self-explanatory.

From:
```js
// 브라우저의 종류 한글처리
var userAgent = request.getHeader("User-Agent");// 브라우저 정보
var ie = userAgent.indexOf("MSIE") > -1;
var filename = null;// 다운로드 받을 파일명
// IE라면
if (ie) {
  filename = URLEncoder.encode(file.getName(), "utf-8");
} else {// chrom,,, (영어->Iso-8859-1
  filename = new String(file.getName().getBytes("utf-8"), "iso-8859-1");
```
Refactored to:
```js
const getBrowserInfo = (req) => {
  return req.getHeader("User-Agent");
};

const getFileName = (req, file) => {
  const userBrowser = getBrowserInfo(req);
  const IE = userBrowser.indexOf("MSIE") > -1;
  const fileName = file.getName();

  return IE
    ? URLEncoder.encode(fileName, "utf-8")
    : new String(fileName.getBytes("utf-8"), "iso-8859-1");
};
```
---
> 3. A single function should handle a single concept.

From:
[Original Code](#original_code) (Single function to handle all different concepts)

To:
[Refactored Code](#refactored_code) (Broke down into smaller functions)
