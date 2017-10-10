# 自定义配置

## 添加Spring Security依赖
build.gradle中添加如下依赖：
```
compile('org.springframework.boot:spring-boot-starter-security')
```
启动应用后的默认安全配置只有一个用户，用户名是user，密码则需要在启动日志中查找如下输出随机生成密码：
```
Using default security password: 40a1ed5d-4057-4ff5-b02b-2bd97ca809f7
```
## 自定义安全配置
- 扩展`WebSecurityConfigurerAdapter`实现自定义的安全配置类[SecurityConfig](src/main/java/com/manning/readinglist/SecurityConfig.java)，并在其中重写confgure()自定义安全策略。
- 通过@EnableWebSecurity注解开启Spring Security的功能
- 继承WebSecurityConfigurerAdapter，并重写它的方法来设置一些web安全的细节:
	- configure(HttpSecurity http)方法
		- 通过authorizeRequests()定义哪些URL需要被保护、哪些不需要被保护。例如以上代码指定了/和/home不需要任何认证就可以访问，其他的路径都必须通过身份验证。
	- 通过formLogin()定义当需要用户登录时候，转到的登录页面。
	- configureGlobal(AuthenticationManagerBuilder auth)方法，在内存中创建了一个用户，该用户的名称为user，密码为password，用户角色为USER。

## 配置参数的优先级
<Spring Boot实战>P50描述了配置参数的优先级顺序。
