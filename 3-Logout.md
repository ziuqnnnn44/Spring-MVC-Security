1.add logout support to config

```html
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
		    )
		    .logout(logout->
		       logout.permitAll()
		    );
		return http.build();
	}
```

2.add logout buttom

home.html

```html
<body>
    <h2>home page</h2>
    <hr>
    <p>
    welcome~~~
    </p>
    
    <form action="#" th:action="@{/logout}" method="POST">
       <input type="submit" value="logout">
    </from>

</body>
```

<img width="512" alt="image" src="https://github.com/ziuqnnnn44/Spring-MVC-Security/assets/66659394/8466eac1-ccdc-4285-adce-438a7a386892">

3.update login form to display “logout”

```html
<!--Check for logout-->
     <div th:if="${param.logout}">

           <div class="alert alert-success col-xs-offset-1 col-xs-10">
                you have been logouted
           </div>

     </div>
```

<img width="682" alt="image" src="https://github.com/ziuqnnnn44/Spring-MVC-Security/assets/66659394/f60786d8-b376-44f1-a5e8-ba29ce66fe59">
