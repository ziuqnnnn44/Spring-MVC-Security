<img width="564" alt="image" src="https://github.com/ziuqnnnn44/Spring-MVC-Security/assets/66659394/1e58b895-1720-4fb5-987f-a60e7a207637">


```java
@Bean
	public SecurityFilterChain filterChain(HttpSecurity http) throws Exception {
		http.authorizeHttpRequests(configurer ->
		    configurer
				      .anyRequest().authenticated()
		    )
		    .formLogin(form->
		    form
		        .loginPage("/showMyLoginPage")
		        .loginProcessingUrl("/autheticateTheUser")
		        .permitAll()
		    );
		return http.build();
	}
```

2.develop controller to show customer login

```java
@Controller
public class LoginController {

	@GetMapping("/showMyLoginPage")
	public String showMyLoginPage() {
		return "plain-ogin";
	}
}
```

3.login form

```java
<!DOCTYPE HTML>
<html lang="en" xmlns:th="http://www.thymeleaf.org">

<head>
    <!-- Required meta tags -->
    <meta charset="utf-8">
   
	<title>Custom Login page</title>
</head>

<body>
    <h2>my custom home page</h2>
<form action="#" th:action="@{/autheticateTheUser}" method="POST">

    <p>
       User name :<input type="text" name="username" />
    </p>

    <p>
       Password :<input type="password" name="password" />
    </p>
    
    <input type="submit" value="Login" />
    
</form>

</body>

</html>
```

Error message

```java
    <!-- check error -->
    <div th:if="${param.error}">
       <i>sorry! you entered invalid username/password</i>
    </div>
```

<img width="647" alt="image" src="https://github.com/ziuqnnnn44/Spring-MVC-Security/assets/66659394/9d03364f-f86e-4cf5-b660-cb4c601e82be">


```html
<head>
    <!-- Required meta tags -->
    <meta charset="utf-8">
   
	<title>Custom Login page</title>
	
	<style>
	     .failed{
	       color: red;
	     }
	</style>
	
</head>

<body>
    <h2>my custom home page</h2>
<form action="#" th:action="@{/autheticateTheUser}" method="POST">

    <!-- check error -->
    <div th:if="${param.error}">
       <i class="failed">sorry! you entered invalid username/password</i>
    </div>
```

<img width="659" alt="image" src="https://github.com/ziuqnnnn44/Spring-MVC-Security/assets/66659394/2b0dbb80-f698-4a47-95b6-915e54cabadb">
