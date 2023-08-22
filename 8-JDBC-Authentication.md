add maven dependency

```html
                <dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-data-jpa</artifactId>
		</dependency>

		<dependency>
			<groupId>com.mysql</groupId>
			<artifactId>mysql-connector-j</artifactId>
			<scope>runtime</scope>
		</dependency>
```

pom file

```html
spring.datasource.url=jdbc:mysql://localhost:3306/employee_directory
spring.datasource.username=springstudent
spring.datasource.password=springstudent

logging.level.org.springframework.jdbc.core=TRACE
```

update config to use jdbc

```java
        @Bean 
	public UserDetailsManager userDetailsManager(DataSource datasource) {
		return new JdbcUserDetailsManager(datasource);
	}
```

B密碼加密 單向加密

<img width="693" alt="image" src="https://github.com/ziuqnnnn44/Spring-MVC-Security/assets/66659394/48324d07-7155-43dd-9638-aeea265d3c34">


run sql script

60 → 68

<img width="664" alt="image" src="https://github.com/ziuqnnnn44/Spring-MVC-Security/assets/66659394/6a618bb4-92d1-4a87-bd21-2a6e2e6d4102">

fun123

<img width="654" alt="image" src="https://github.com/ziuqnnnn44/Spring-MVC-Security/assets/66659394/528cb84b-c56a-4db3-8d0a-3edb7f38d04b">
