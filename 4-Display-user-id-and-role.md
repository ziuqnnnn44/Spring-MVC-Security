1.Display user id

```html
<!DOCTYPE HTML>
<html lang="en" xmlns:th="http://www.thymeleaf.org"
                xmlns:sec="http://www.thymeleaf.org/extras/spring-security">
<head>
    <!-- Required meta tags -->
    <meta charset="utf-8">
   
	<title>Home page</title>
</head>

<body>
    <h2>home page</h2>
    <hr>
    <p>
    welcome~~~
    </p>
    
    <hr>
    
    <p>
        User: <span sec:authentication="principal.username"></span>
        Role(s): <span sec:authentication="principal.authorities"></span>
    </p>
    
    <hr>
    
    <form action="#" th:action="@{/logout}" method="POST">
       <input type="submit" value="logout">
    </from>

</body>

</html>
```

2.Display role

ROLE_Employee 固定寫

<img width="617" alt="image" src="https://github.com/ziuqnnnn44/Spring-MVC-Security/assets/66659394/6d6f0524-f9c3-4fdb-8b68-a487bc058bac">
