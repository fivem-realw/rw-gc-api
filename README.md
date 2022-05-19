```diff
- 해당 API는 테스트 버전 입니다. Production 버전에서 이용하지 마십시오.
- 해당 API는 테스트 단계이므로 API서버에 접속이 원활하지 않을 수 있습니다.
```

# RW-GiftCertificate API

## 소개

RW-GiftCertificate API는 RealWorld 에서 제공하는 상품권 API 입니다.<br>
컬쳐랜드 문화상품권 PIN번호 검증 및 자동충전 서비스를 제공합니다.<br>

- [lua-sdk](https://github.com/fivem-realw/RW-API/tree/main/lua)
- [node-sdk](https://github.com/fivem-realw/RW-API/tree/main/node)
  <br><br>

## API 엔드포인트

- 메인 노드

```
https://api.realw.kr/gc/v1
```

### 엔드포인트에 대한 일반 정보

- `GET` 엔드포인트의 경우 매개변수를 `query string` 으로 전송할 수 있습니다.
- `POST`, `PUT` 및 `DELETE` 끝점의 경우 매개변수는 `application/json` 요청으로 전송될 수 있습니다.
- 매개변수는 어떤 순서로든 보낼 수 있습니다.

### HTTP 반환 코드

- HTTP 4XX 반환 코드는 잘못된 요청에 사용됩니다. 문제는 호출자 측에 있습니다.
- HTTP 403 반환 코드는 WAF 제한(웹 응용 프로그램 방화벽)을 위반했을 때 사용됩니다.
- HTTP 429 반환 코드는 요청 속도 제한을 위반할 때 사용됩니다.
- HTTP 418 반환 코드는 코드를 받은 후 요청을 계속 보내기 위해 IP가 자동 금지되었을 때 사용됩니다.
- HTTP 5XX 반환 코드는 내부 오류에 사용됩니다. 문제는 API 서버측입니다.

## API 목록

- 모든 API 호출에는 `X-API-Credential` 헤더가 포함되어야 합니다.

### 상품권 PIN번호 체크

```
GET /checkNumber
```

- 매개변수
<table>
  <thead>
    <tr>
      <td>매개변수 명</td>
      <td>매개변수 타입</td>
      <td>필수값</td>
      <td>설명</td>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>value</td>
      <td>STRING</td>
      <td>예</td>
      <td></td>
    </tr>
    <tr>
      <td>type</td>
      <td>INT</td>
      <td>아니요</td>
      <td>1: 컬쳐랜드 문화상품권 (기본값: 1)</td>
    </tr>
  </tbody>
</table>
<br>

### 컬쳐랜드 로그인 토큰 얻기

```
POST /cl/getToken
```

- 매개변수
<table>
  <thead>
    <tr>
      <td>매개변수 명</td>
      <td>매개변수 타입</td>
      <td>필수값</td>
      <td>설명</td>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>username</td>
      <td>STRING</td>
      <td>예</td>
      <td>컬쳐랜드 로그인 아이디</td>
    </tr>
    <tr>
      <td>password</td>
      <td>STRING</td>
      <td>예</td>
      <td>컬쳐랜드 로그인 비밀번호</td>
    </tr>
  </tbody>
</table>
<br>

### 컬쳐랜드 계정에 충전

```
POST /cl/payment
```

- 매개변수
<table>
  <thead>
    <tr>
      <td>매개변수 명</td>
      <td>매개변수 타입</td>
      <td>필수값</td>
      <td>설명</td>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>number</td>
      <td>STRING</td>
      <td>예</td>
      <td></td>
    </tr>
    <tr>
      <td>username</td>
      <td>STRING</td>
      <td>아니요</td>
      <td>컬쳐랜드 로그인 아이디</td>
    </tr>
    <tr>
      <td>password</td>
      <td>STRING</td>
      <td>아니요</td>
      <td>컬쳐랜드 로그인 비밀번호</td>
    </tr>
    <tr>
      <td>token</td>
      <td>STRING</td>
      <td>아니요</td>
      <td>컬쳐랜드 로그인 토큰</td>
    </tr>
  </tbody>
</table>

### 컬쳐랜드 계정에 여러개 일괄 충전

```
POST /cl/paymentBulk
```

- 매개변수
<table>
  <thead>
    <tr>
      <td>매개변수 명</td>
      <td>매개변수 타입</td>
      <td>필수값</td>
      <td>설명</td>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>numbers</td>
      <td>ARRAY</td>
      <td>예</td>
      <td></td>
    </tr>
    <tr>
      <td>username</td>
      <td>STRING</td>
      <td>아니요</td>
      <td>컬쳐랜드 로그인 아이디</td>
    </tr>
    <tr>
      <td>password</td>
      <td>STRING</td>
      <td>아니요</td>
      <td>컬쳐랜드 로그인 비밀번호</td>
    </tr>
    <tr>
      <td>token</td>
      <td>STRING</td>
      <td>아니요</td>
      <td>컬쳐랜드 로그인 토큰</td>
    </tr>
  </tbody>
</table>
