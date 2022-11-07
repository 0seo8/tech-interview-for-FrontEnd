# CSS를 이용한 브라우저 렌더링 최적화

## 브라우저 렌더링과정

사용자가 브라우저를 통해 사이트를 접속했을 때 네트워크 통신이 끝난 후 화면에 어떻게 렌더링이 되게 될까?

**Parse**

- HTML문서를 통해 HTML parser와 CSS parser가 DOM tree와 CSSOM(Object Model)을 작성합니다.
- 이 두가지 데이터를 기반으로 Render Tree가 작성되면, 이 Render Tree에는 문서의 각 구조와 각 노드의 Style속성들이 입력되게 됩니다.

**Layout(Reflow)**

- Layout단계에서는 상대적인 크기, 예를 들어 rem, vh, vw와 같은 단위들을 px단위를 변환합니다. 이 데이터를 기반으로 어떤 위치에 Layout이 표시되고 어떤 크기로 출력되어야 하는지 작성하여 Layout Tree를 생성합니다.

**Paint(Repaint)**

- 앞서 작성된 Layout Tree에서 사이즈와 크기를 제외한 CSS속성을 적용합니다. 예를 들어 배경화면 색, 이미지, 선, 그림자와 같은 속성들을 Layout Tree기반으로 작성하게 됩니다.

**Composite**

- Layout Tree를 기반으로 생성된 Layer들을 기준으로 순차적으로 레스터화(픽셀로 변환하는 과정)를 시도하여 사용자의 화면에 순서대로 출력합니다.

## Reflow를 방지하는 방법은?

브라우저 렌더랑 과정 중 Reflow는 Repaint의 상위 과정이기 때문에, DOM요소의 변경이 일어나면 즉, Reflow가 일어나면 자연스럽게 Repaint도 함께 발생해 자원을 더 소모하게 됩니다.

Reflow는 top, bottom, left, right와 같은 특성들을 transform: translate로 변경하는 작업을 통해 방지할 수 있습니다.

또한 transform : translate(x,y) 속성을 transform: traslate3d(x,y,z)을 통해 성능을 개선할 수도 있습니다.

이를 이해하기 위해서는 브라우저 렌더링 과정 중 composite단계를 조금 더 자세히 알아봐야합니다.

Layer Tree가 생성된 후 이 레이어를 이미지로 변환하여 GPU로 합성 후 출력하게 됩니다.

composite단계에서는 이 Layer들이 `Paint Layer`과 `Graphics Layer` 두가지로 나뉘게 됩니다.

`Graphics Layer`의 경우 GPU를 활용하여 이미지로 변환되며, 병렬처리에 특화되어 있어 더 빠르게 변환이 가능합니다. 기존 레이어에서 새롭게 분리되어 주변 레이어에 영향 없이 해당 레이어만 빠르게 그리고 출력할 수 있습니다.

GPU에서 작업이 이뤄져 CPU와 그래픽 작업을 분리할 수 있어, 저사양 기기에서의 CPU부담을 덜어줄 수 있습니다.

`Graphics Layer`의 분리조건으로는 `<video>`,`<canvas>`태그 또는 animation또는 transition이 적용되어 있고, opacity, transform, filter속성이 적용되어 있는 경우, `backtrop-filter`, `will-change`속성이 적용된 경우입니다.
