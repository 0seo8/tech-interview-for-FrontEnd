# require와 import의 차이점

- require의 경우 node.js에서 사용되는 내장 키워드이고, import의 경우 ES6모듈에서 도입된 키워드입니다.
- require의 경우 코드 어느 지점에서나 호출이 가능하지만 import의 경우 코드 맨 위에서만 실행이 가능합니다.
- 대신 import의 경우 from을 통해 필요한 모듈만 불러올 수 있습니다.

정리,
require는 node.js에서 쓰는 키워드이고, import는 ES6에서 도입된 키워드입니다.
특징으로는 import의 경우 항상 맨 위에서만 사용을 해야하고 원하는 모듈만 from을 통해 불러 올 수 있습니다.
require의 경우 모듈을 항상 다 불러와야하지만, 코드 어느지점에서나 호출이 가능합니다.
