# bfetch

네트워크 통신이 아니라 앱 개발을 위한 fetch

__Failure Decision__<br/>
서버 프로토콜에 따라, http status code가 아닌 body의 내용에 따라서 에러로 처리해야하는 경우가 있습니다.<br/>
```jsx
bfetch.onResponse = (e) => {
  // statusCode를 사용할 경우
  if (e.statusCode >= 400)
    throw new SOME_ERROR();
    
  // 내부 메세지를 사용할 경우
  if (e.body.status === 'error')
    throw new SOME_ERROR();
};
```

__Global Error Handling__
```jsx
bfetch.onError = (e, retry) => {
  if (prompt('retry?') === 'yes')
    retry();
};
```

__Loading Counter__
```jsx
bfetch.activeRequests
```
```jsx
bfetch.onActiveRequestsChange = (activeRequests) => {
  showLoading(activeRequests > 0);
};
```
