filter可以預處理以及後處理web請求

<img width="699" alt="image" src="https://github.com/ziuqnnnn44/Spring-MVC-Security/assets/66659394/46ecb42a-d080-4772-9492-8ee6583871bf">


驗證：檢查用戶id密碼

授權：是否有授權

1.create project

<img width="676" alt="image" src="https://github.com/ziuqnnnn44/Spring-MVC-Security/assets/66659394/37ec2f90-b69e-4a97-a051-50e26b4e3946">

2.develop controller

```java
package com.luv2code.springboot.demosecurity.controller;

import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.GetMapping;

@Controller
public class DemoController {
	
	@GetMapping("/")
	public String showHome() {
		
		return "home";
	
		
	}

}
```

3.develop thymeleaf page

home.html

```java
<!DOCTYPE HTML>
<html lang="en" >

<head>
    <!-- Required meta tags -->
    <meta charset="utf-8">
   
	<title>Home page</title>
</head>

<body>
    <h2>home page</h2>
    <hr>
    welcome~~~

</body>

</html>
```

output

<img width="704" alt="image" src="https://github.com/ziuqnnnn44/Spring-MVC-Security/assets/66659394/8321919b-137f-4512-9a99-ac26a3d1fc7a">


1.create security configuration

```java
@Configuration
public class DemoSecurityConfig {
}
```

2.add user password and role

```java
package com.luv2code.springboot.demosecurity.security;

import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.security.core.userdetails.User;
import org.springframework.security.core.userdetails.UserDetails;
import org.springframework.security.provisioning.InMemoryUserDetailsManager;

@Configuration
public class DemoSecurityConfig {
	@Bean
	public InMemoryUserDetailsManager userDetailsManager() {
		UserDetails john = User.builder()
				.username("john")
				.password("{noop}test123")
				.roles("Employee")
				.build();
		
		UserDetails mary = User.builder()
				.username("mary")
				.password("{noop}test123")
				.roles("Employee","manager")
				.build();
		
		UserDetails susan = User.builder()
				.username("susan")
				.password("{noop}test123")
				.roles("employee","manager","admin")
				.build();
		
		return new InMemoryUserDetailsManager(john, mary, susan);
	}
}
```
