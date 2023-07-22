## CSRF - Cross-Site Request Forgery

- 인증된 유저의 계정을 사용해 유저의 의도와는 무관하게 악의적인 변경 요청을 만들어 보내는 기법

### CSRF 공격 방지

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a79b5d55-f88b-4a91-96c7-280a390113ad/Untitled.png)

- 스프링 시큐리티의 경우 CSRF Filter 를 통해 검사
- 페이지를 제공하는 서버와 데이터를 제공하는 서버가 다를 경우 CSRF 토큰을 포함하지 않는 요청을 허용해야함으로 이를 대체할 방어 전략이 필요하다.
