## JavaScript Spread

이 리포지토리는 JavaScript Spread연산자 사용 방법에 대한 리포지토리입니다. <br />

<a href="https://github.com/devncore/devncore"><strong>더 알아보기 »</strong></a>
 
| Star | License | Activity |
|:----:|:-------:|:--------:|
| <a href="https://github.com/devncore/docs/stargazers"><img src="https://img.shields.io/github/stars/devncore/docs" alt="Github Stars"></a> | <img src="https://img.shields.io/github/license/devncore/docs" alt="License"> | <a href="https://github.com/devncore/docs/pulse"><img src="https://img.shields.io/github/commit-activity/m/devncore/docs" alt="Commits-per-month"></a> |

<br />
 
### Spread 연산자란
- ECMAScript6(2015)에서 새로 추가된 전개 연산자(Spread Operator)란 객체나 배열의 값을 하나 하나 넘기는 용도로 사용할 수 있습니다. 전개 연산자를 사용하는 방법은 점 세개(...)를 붙이면 됩니다.

<br />

1. 사용방법
```jsx
const arr1 = [1, 2, 3];
const arr2 = [4, 5, 6];
const arr3 = [7, 8, 9];
const arrWrap = [...arr1, ...arr2, ...arr3];

console.log(arrWrap); // [1, 2, 3, 4, 5, 6, 7, 8, 9]
```

<br />

2. 배열 아무곳에나 전개연산자를 추가할 수 있습니다.
```jsx
const arr = [4, 5, 6];
const arrWrap = [1, 2, 3, ...arr, 7, 8, 9]

console.log(arrWrap); // [1, 2, 3, 4, 5, 6, 7, 8, 9]
```

<br />

3. 객체에서도 동일합니다.
```jsx
const objA = {a:1, b:2};
const objB = {...objA};

console.log(objB); //{a:1, b:2}
```

<br />

4. 객체 특정 값 변경하기
```jsx
const objA = {a:1, b:2, c:3};
const objB = {...objA, b: 4};

console.log(objB); //{a:1, b:4, c:3}
```

5. 객체 더 깊은 값 변경
```jsx
const object = {
a: {
    b: {
        target: 123,
        c: "cc"
        },
    d: "dd"
e: "ee"
}

//target데이터만 변경

const newObject = {
...object,
a: {
    ...object.a,
    b: {
    ...object.a.b,
    target: 456
    }
}
}
```



