## CSRF - Cross-Site Request Forgery

- 인증된 유저의 계정을 사용해 유저의 의도와는 무관하게 악의적인 변경 요청을 만들어 보내는 기법

### CSRF 공격과 방지

![image](https://github.com/MisterRuby/spa-restapi-cors/assets/93859705/76da9a32-861b-48a3-937e-40bf8d7f7d68)

- 스프링 시큐리티의 경우 CSRF Filter 를 통해 검사
- 페이지를 제공하는 서버와 데이터를 제공하는 서버가 다를 경우 CSRF 토큰을 포함하지 않는 요청을 허용해야함으로 이를 대체할 방어 전략이 필요하다.

<br/><br/>

## CORS - Cross-Origin Resource Sharing

- 교차 출처 리소스 공유. 추가 HTTP 헤더를 사용하여, 한 출처에서 실행 중인 웹 애플리케이션이 다른 출처의 선택한 자원에 접근할 수 있는 권한을 부여하도록 브라우저에 알려주는 체제

![image](https://github.com/MisterRuby/spa-restapi-cors/assets/93859705/a45e1f88-a850-4eed-a0ba-53c380b664c1)  

### Spring Security CORS Setting

```java
@EnableWebSecurity
@Configuration
@RequiredArgsConstructor
public class SecurityConfig {

    @Bean
    public SecurityFilterChain securityFilterChain(HttpSecurity http) {
        // CORS 허용
        http.csrf(AbstractHttpConfigurer::disable)
            .cors(corsConfigurer -> corsConfigurer.configurationSource(corsConfigurationSource()));

        // 페이지 권한 설정
        http.authorizeHttpRequests(authorizeHttpRequests -> authorizeHttpRequests.anyRequest().permitAll());

        return http.build();
    }

    @Bean
    public CorsConfigurationSource corsConfigurationSource() {
        CorsConfiguration configuration = new CorsConfiguration();
	// 지정한 출처의 애플리케이션의 요청을 허용
        configuration.addAllowedOriginPattern("http://localhost:5173");
        configuration.addAllowedHeader("*");
        configuration.addAllowedMethod("*");

        UrlBasedCorsConfigurationSource source = new UrlBasedCorsConfigurationSource();
        source.registerCorsConfiguration("/**", configuration);
        return source;
    }
}
```
