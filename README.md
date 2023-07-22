## CSRF - Cross-Site Request Forgery

- 인증된 유저의 계정을 사용해 유저의 의도와는 무관하게 악의적인 변경 요청을 만들어 보내는 기법

### CSRF 공격 방지

![image](https://github.com/MisterRuby/spa-restapi-cors/assets/93859705/76da9a32-861b-48a3-937e-40bf8d7f7d68)

- 스프링 시큐리티의 경우 CSRF Filter 를 통해 검사
- 페이지를 제공하는 서버와 데이터를 제공하는 서버가 다를 경우 CSRF 토큰을 포함하지 않는 요청을 허용해야함으로 이를 대체할 방어 전략이 필요하다.
