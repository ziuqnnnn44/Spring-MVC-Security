1.create controller code and view page

home.html

```java
    <p>
       <a th:href="@{/leaders}">Leadership Meeting</a>
       (Only for Manager Page)
    </p>
```

DemoController

```java
@Controller
public class DemoController {
	
	@GetMapping("/")
	public String showHome() {
		
		return "home";
				
	}
	
	@GetMapping("/leaders")
	public String showLeaders() {
		
		return "leaders";
				
	}
}
```

leaders.html

```java
<!DOCTYPE HTML>
<html lang="en" xmlns:th="http://www.thymeleaf.org"
                xmlns:sec="http://www.thymeleaf.org/extras/spring-security">
<head>
    <!-- Required meta tags -->
    <meta charset="utf-8">
   
	<title>Leader Home page</title>
</head>

<body>
    <h2> leader home page</h2>
    
    <hr>
    
    <p>
    welcome~~~
    </p>
    
    <a th:href="@{/}">Back to home page</a>
    
</body>

</html>
```

2.restrict access based on roles

```java
@Bean
	public SecurityFilterChain filterChain(HttpSecurity http) throws Exception {
		http.authorizeHttpRequests(configurer ->
		    configurer
				      
				      .requestMatchers("/").hasRole("Employee")
				      .requestMatchers("/leaders/**").hasRole("manager")
				      .requestMatchers("/systems/**").hasRole("admin")
				      .anyRequest().authenticated()
		    )
		    .formLogin(form->
		    form
		        .loginPage("/showMyLoginPage")
		        .loginProcessingUrl("/autheticateTheUser")
		        .permitAll()
		    )
		    .logout(logout->
		       logout.permitAll()
		    );
		return http.build();
```
