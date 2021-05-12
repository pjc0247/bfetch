# bfetch

네트워크 통신이 아니라 앱 개발에 특화된 fetch

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
