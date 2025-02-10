---
date created: 26.08.2023 01:58
date modified: 18.08.2024 13:48
---
Spring config can be used to enable debug logging with 
```yml
logging:  
  level:  
    org.springframework.security: DEBUG
```
in an application.yml file (or application.property)

## Backend Configuration

For every component an own implementation can be provided by the beans.
```java
@Configuration  
@EnableWebSecurity  
public class SecurityConfig {  
	// Defines how user details are loaded
	// Here it's the InMemory Version, should be replaced by Ldap Server or something else for production
    @Bean  
    public UserDetailsService userDetailsService(PasswordEncoder passwordEncoder) {  
        InMemoryUserDetailsManager manager = new InMemoryUserDetailsManager();  
        manager.createUser(User.withUsername("user")  
                .password(passwordEncoder.encode("userPass"))  
                .roles("USER")  
                .build());  
        manager.createUser(User.withUsername("oschdi")  
                .password(passwordEncoder.encode("lolistlol1"))  
                .roles("USER", "ADMIN")  
                .build());  
        return manager;  
    }  

	// This component defines the actual authentification 
	// Needs an PasswordEncoder and a UserDetailsService
    @Bean  
    public AuthenticationManager authenticationManager(HttpSecurity http, PasswordEncoder passwordEncoder, UserDetailsService userDetailsService)  
            throws Exception {  
        return http.getSharedObject(AuthenticationManagerBuilder.class)  
                .userDetailsService(userDetailsService)  
                .passwordEncoder(passwordEncoder)  
                .and()  
                .build();  
    }  

	// Defines the filters for different paths
	// Lots of different options for different roles and unauthentifcated users (e.g. login page)
    @Bean  
    public SecurityFilterChain filterChain(HttpSecurity http) throws Exception {  
        http  
                .csrf().disable()  
                .cors().configurationSource(corsConfigurationSource())  
            .and()  
                .authorizeHttpRequests((authz) -> authz  
                        .requestMatchers(HttpMethod.POST).hasRole("ADMIN");
                        .requestMatchers(HttpMethod.DELETE, "/adminPath/**").hasRole("ADMIN")
                        .anyRequest().permitAll()  
                )  
                //this defines that the basic authentification protocll is used
                .httpBasic(withDefaults()) 
                .csrf(AbstractHttpConfigurer::disable);
                //this defines the session management (sometimes brwoser data has to be deleted if another user is needed)
                .sessionManagement()  
                .sessionCreationPolicy(SessionCreationPolicy.STATELESS);  
        return http.build();  
    }  

	// This defines the CORS behaviour. Different origins, methods and headers can be allowd/blocked
	// replace allowOriginPatterns by allowOrigins for specific origins
    CorsConfigurationSource corsConfigurationSource() {  
        CorsConfiguration configuration = new CorsConfiguration();  
        List<String> allowOriginPatterns = Arrays.asList("*");  
        configuration.setAllowedOriginPatterns(allowOriginPatterns);  
        configuration.setAllowedMethods(singletonList("*"));  
        configuration.setAllowedHeaders(singletonList("*"));  
        //in case authentication is enabled this flag MUST be set, otherwise CORS requests will fail  
        configuration.setAllowCredentials(true);  
        UrlBasedCorsConfigurationSource source = new UrlBasedCorsConfigurationSource();  
        source.registerCorsConfiguration("/**", configuration);  
        return source;  
    }  
    
    @Bean  
    public PasswordEncoder passwordEncoder() {  
        return new BCryptPasswordEncoder();  
    }  
  
}
```

## Frontend Requests

The changes are the authorization header and the withCredentials option.
```typescript
public async secureGet() {  
  const encodedCredentials = btoa('admin:adminPass');  
  let headers = new HttpHeaders() 
    .set('Authorization', `Basic ${encodedCredentials}`);  
  await lastValueFrom(this.httpClient.post(this.backendURL + "/recipe",  
    { responseType: "text", 'headers':headers, withCredentials: true })).then( () => {  
    console.log("success");  
  });  
}
```