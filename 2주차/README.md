### Q. 아래 코드를 보고 node.js 환경과 브라우저 환경 각각의 결과 값과 해당 결과 값이 나오는 이유를 설명해주세요.

```jsx
const person = {
  'last-name': 'Lee',
};
person.last - name;
```

    A.
        - node.js : ReferenceError : name is not defined
            - person.last-name = undefined - name ⇒ name 식별자가 존재하지 않는다
        - 브라우저 : NaN
            - person.last - name = undefined - '' = NaN
            - 전역 변수 name은 window의 이름을 가리키며 기본 값은 빈 문자열이다

</br>

### 아래 코드를 보고 결과 값과 해당 결과 값이 나오는 이유를 설명해주세요.

```jsx
const o = { x: { y: 1 } };

const c1 = { ...o };

console.log(c1 === o); // 1.결과 값은?
console.log(c1.x === o.x); // 2.결과 값은?
```

    A.
        - 스프레드 문법을 이용해 o를 얕은 복사하여 새로운 객체 c1 생성
        - c1은 새롭게 생성된 객체이므로 참조 값이 다른 별개의 값이다. 따라서 1번은 false
        - 하지만 { y: 1 }은 깊은 복사가 아닌 얕은 복사가 일어나 한 단계까지만 복사가 일어났기 때문에 2번은 true

</br>

### Q. script 태그의 async와 defer 어트리뷰트를 비교하여 설명해주세요.

    A.
        - script 태그는 src 어트리뷰트를 통해 외부 자바스크립트 파일을 로드하는 경우 사용하는 태그입니다.
        - async 어트리뷰트 사용 시 HTML의 파싱과 자바스크립트 파일의 로드가 비동기적으로 동시에 진행됩니다. 자바스크립트 파일 로드가 완료된 직후에 자바스크립트의 파싱과 실행이 일어나며, 이때 HTML 파싱은 중단되게 됩니다.
        - defer 어트리뷰트 사용 시 async 어트리뷰트와 동일하게 HTML의 파싱과 자바스크립트 파일의 로드가 비동기적으로 동시에 진행됩니다. 하지만 자바스크립트의 파싱과 실행은 HTML 파싱이 완료된 이후 즉, DOM 생성이 완료된 직후 진행됩니다.

</br>

### Q. 리액트 가상 DOM과 재조정(Reconciliation)에 대해 설명해주세요.

    A.
        - 가상 DOM(Virtual DOM)
            - 동적으로 데이터가 변화했을 때 직접적으로 DOM을 조작하는 것이 아니라 DOM의 사본이라고 할 수 있는 새로운 가상 DOM을 생성한다.
            - 새로 생성된 가상 DOM과 이전에 저장된 가상 DOM을 비교해 변경된 부분의 DOM 만을 변경한다. 이 과정을 재조정(reconciliation)이라고 한다.
        - 재조정(Reconciliation)
            - DOM 엘리먼트의 타입이 다른 경우 : 이전 트리를 버리고 완전히 새로운 트리를 구축
            - DOM 엘리먼트의 타입이 같은 경우 : 변경된 속성들에 대해서만 갱신
            - key prop : key를 식별자로 사용하면서 추가된 엘리먼트만 갱신
