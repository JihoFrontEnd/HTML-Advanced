###### 001

# `<form>`의 onsubmit 결과가 `boolean` 값일 경우

###### jihogrammer. 20220225.

`form`에서 submit 이벤트가 발생했을 때 `action`을 취한다.
이때, action을 취하기 전에 입력값의 검증 등을 수행할 필요성이 있다.
이러한 흐름을 굳이 JS로 처리하지 않도록 HTML 자체에서 제공하는 기능을 사용할 수 있다.

form 속성 중 `onsubmit`을 사용하여 그 결과가 `boolean`을 반환하게 하면,
onsubmit에 넘긴 callback이 참이면 action을 취하고 거짓이면 아무런 동작을 하지 않는다.

```html
<script>
  function falseCallback() {
    console.log('false');
    return false;
  }
</script>

<form action="/001/isSuccess.html" onsubmit="return true;">
  <input type="submit" value="TRUE" />
</form>

<form action="/001/isSuccess.html" onsubmit="return falseCallback();">
  <input type="submit" value="FALSE" />
</form>
```

엄밀히 말하면 onsubmit 안에 return문으로 callback의 결과를 반환하는 형태에서 동작한다.
onsubmit 자체가 함수이기 때문인 것으로 보인다.
화살표 함수도 먹히지 않아 살짝 싫다.

하지만 JS로 이 작업을 처리하기에는 더 복잡해진다. 존재하는 것에 감사하자.

##### References

- https://kim22036.tistory.com/entry/onsubmit-return-false의-의미
