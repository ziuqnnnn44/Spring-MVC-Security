1.config page for access deny

```java
.exceptionHandling(configurer ->
		    configurer.accessDeniedPage("/acess-denied"));
```

2.create controller code and view page

```java
@GetMapping("/access-denied")
	public String showAccessPage() {
		return "access-denied";
	}
```

access-denied.html

```html
<!DOCTYPE HTML>
<html lang="en" xmlns:th="http://www.thymeleaf.org"
                xmlns:sec="http://www.thymeleaf.org/extras/spring-security">
<head>
    <!-- Required meta tags -->
    <meta charset="utf-8">
   
	<title>Denied page</title>
</head>

<body>
    <h2> Access Denied</h2>
    
    <hr>

    <a th:href="@{/}">Back to home page</a>
    
</body>

</html>
```

<img width="481" alt="image" src="https://github.com/ziuqnnnn44/Spring-MVC-Security/assets/66659394/f4ab0af2-341d-47bd-981f-aec0b6f23e12">
