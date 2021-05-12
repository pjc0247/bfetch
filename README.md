# bfetch

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
