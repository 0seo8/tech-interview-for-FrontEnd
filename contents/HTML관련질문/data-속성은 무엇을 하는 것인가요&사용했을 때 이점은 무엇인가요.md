# data-속성은 무엇을 하는 것인가요? 사용했을 때 이점은 무엇인가요?

data-\* 속성은 사용자 지정 데이터 특성(custom data attributes)이라는 특성 클래스를 형성함으로써 임의의 데이터를 스크립트로 HTML과 DOM 사이에서 교환할 수 있는 방법입니다.

- html에서는 dashcase로 사용하며, 자바스크립트로 속성을 가져다 쓸 때는 camelCase를 사용합니다.
- `document.getElementById("btn").dataset.codeId;`

HTML5부터 적용되었으며, 데이터 속성을 이용하여 특정 데이터를 DOM요소에 저장해둘 수 있습니다.
