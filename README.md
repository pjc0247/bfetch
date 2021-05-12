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


__Preset__
```jsx
const DefaultModification = {
};
```

per-API<br/>
API 실행별로 정책을 지정할 수 있습니다.<br/>
몇몇 API는 성공하던, 실패하던 아예 중요하지 않을 수 있습니다. 이런 API들에 대해 글로벌 정책을 무시하고 아무런 메세지도 띄우지 않도록 할 수 있습니다.
```jsx
const TrivialApiPolicy = {
  onError: () => {},
};

bfetch('POST', '/heartbeat', TrivialApiPolicy);
```
