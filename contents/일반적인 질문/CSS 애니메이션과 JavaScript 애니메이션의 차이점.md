# CSS 애니메이션과 JS 애니메이션의 차이점

## CSS애니메이션

- 간단하게 처리하는 애니메이션의 경우 CSS로 처리합니다.
- transform 의 translate 를 사용해서 구현할 수 있는 애니메이션을 JavaScript의 style.top 과 style.left 속성을 변화 시키게 되면
- 브라우저 렌더링 과정에서 layout 이나 paint 단계를 거쳐야 할 경우가 생길 수 있기 때문에 성능 개선에 효율적이지 않을 수 있습니다.
