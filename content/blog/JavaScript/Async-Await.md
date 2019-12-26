---
title: 'async/await'
date: 2019-10-04 22:37:43
category: 'Javascript'
---

비동기 처리 방안이 Promise로 만족하지 못하고 더 좋은 방법을 고안했다(사실 async/await는 promise기반). 절차적 언어에서 작성하는 코드와 같이 사용법도 간단하고 이해하기도 쉽다. function 키워드 앞에 async를 붙여주면 되고 function 내부의 promise를 반환하는 비동기 처리 함수 앞에 await를 붙여주기만 하면 된다. async/await의 가장 큰 장점은 Promise보다 비동기 코드의 겉모습을 더 깔끔하게 한다는 것이다.

```js
async function() {
	await fn(); // await 뒤에 위치할 함수의 반환값이 resolve일 경우에는 promise여야 한다.
}
```

`await`의 역할은 함수의 동작이 `resolve`나 `reject`가 되어서 동작이 마칠때까지 정확히 기다린다.
(**그래서 async/await 구문을 쓸때는 await의 정확한 타이밍을 아는 것이 중요하다.**)
`const baz = await fn();` 이와 같이 변수에 할당해서 활용할 수 있다.

- async/await 에서 비동기 작업하면서 `try`, `catch`는 `Promise`의 `then`,`catch`에서 error를 잡아내는 것과 일맥상통하게 동작한다.

- promise로 구현

```js
function makeRequest() {
  return getData()
    .then(data => {
      if (data && data.needMoreRequest) {
        return makeMoreRequest(data)
          .then(moreData => {
            console.log(moreData)
            return moreData
          })
          .catch(error => {
            console.log('Error while makeMoreRequest', error)
          })
      } else {
        console.log(data)
        return data
      }
    })
    .catch(error => {
      console.log('Error while getData', error)
    })
}
```

- async/await 구현

```js
async function makeRequest() {
  try {
    const data = await getData()
    if (data && data.needMoreRequest) {
      const moreData = await makeMoreRequest(data)
      console.log(moreData)
      return moreData
    } else {
      console.log(data)
      return data
    }
  } catch (error) {
    console.log('Error while getData', error)
  }
}
```
