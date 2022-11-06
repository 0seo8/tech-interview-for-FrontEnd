# CORS

## 1. CORS가 무엇이며 어떻게 해결을 할 수 있는가?

CORS(Cross Origin Resource Sharing)으로, 한국말로 해석하면 교차 출처 리소스 공유라고 해석 할 수 있습니다.
서로 다른 도메인에서 자원을 공유하는 것을 의미하며, 대부분의 브라우저는 보안상의 이유로 제한이 되어있습니다.

요청이 받아드려지기 위해서는 Origin이 같이야 하는데 여기서 Origin은 Protocal+Host+Port(`HTTPS://` `www.domain.com` `:3000`)를 합친것을 의미합니다.

React와 같은 라이브러리를 이용해 개발을 하는 경우, Chrome 확장프로그램 (`Allow CORS: Access-Control-Allow-Origin`)을 이용하여 로컬(localhost) 환경에서 발생하는 CORS문제를 해결할 수 있습니다.

또한 개발환경에서 Webpack이나 vite에 직접 proxy설정을 하여 문제를 해결 할 수도 있습니다.

하지만 가장 정석적이고 근본적인 해결책은 서버에서는 응답 헤더에 특정 헤더를 포함하는 방법입니다. Access-Control-Allow-Origin을 통해 특정 브라우저가 리소스에 접근이 가능하도록 허용할 수 있습니다.

---

## 2. NodeJS 기반의 웹 서버에서 CORS를 어떻게 설정하나요?

`nodeJS`

nodeJS에서는 cors미들웨어 패키지를 설치 후 reqiure해온뒤app.use에 cors를 넣어 모든요청을 허용해줄수도 있고, app.use 안에 넣은 cors에 객체형태로 origin에 url을 할당한 변수를 넣어 특정 url만 허용해줄수도 있습니다.

---

## 3. CORS에러와 관련된 경험이 있나요?

- 백앤드와 협업 프로젝트를 진행을 하며 경험해본 적이 있습니다. 프론트단에서는 `credentials`옵션에 `include`를 설정하고, 백앤드에서 CORS허용을 \* 로 해두어 에러가 발생한 경험이 있습니다.

  - fetch: `credentials: 'include`, axios: `withCredentials:true`, RKT-query :`setcredentials: true`
  - credentials 옵션을 사용하여 요청에 인증정보가 담겨있는 상태에서 다른 출처의 리소스를 요청하는 경우 `Access-Control-Allow-Origin`에 모든 요청을 허용하는 \*를 사용할 수 없으며 응답 헤더에는 반드시 `Access-Control-Allow-Credentials: true`가 존재해야합니다.

- 공공데이터를 이용한 미세먼지 알림이 프로젝트를 만들때 CORS문제를 경험한 적이 있습니다. 이 당시에는 vite에 proxy설정을 하여 문제를 해결하였습니다.

---

## 추가 공부

외부 공격으로부터 서버를 보호하기 위해 특정 도메인/IP 이외의 경로로 들어오는 요청을 차단하는게 CORS에러. 즉, CORS는 보안 정책 중 하나이지만, 보호의 대상은 서버가 아닙니다.
