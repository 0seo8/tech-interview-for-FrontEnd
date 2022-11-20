# CSS애니메니션과 JS애니메이션의 차이

## CSS 애니메이션

- Transition과 Animation 속성이 존재
- Transition은 hover나 click과 같은 이벤트 트리거에 의해 동작
  해당 element의 변화를 일정 기간동안 일어나게 함
- Animation은 이벤트를 포함하여 시작, 정지, 반복까지 제어 가능
-

## JS 애니메이션

- setInterval()과 같은 함수를 활용해 element에 변화를 줌.

## 차이점

1. CSS 애니메이션은 IE를 잘 지원하지 않는다는 단점. 크로스 브라우징측면에서는 JS 애니메이션이 선호된다.
2. JS는 style.top, style.left와 같이 요소 하나하나와 동작을 관리해줘야한다. css는 css만 관리하면 되기 때문에 관리가 용이하다. 대신 JS는 세밀한 동작까지 변형을 줄 수가 있음.
