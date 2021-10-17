# LOG4J

A Log4J Alternative
Alternatively, if we use Log4J2, we can set the log level in the log4j2-spring.xml file within src/test/resources:

```
<Configuration>
    <Appenders>
        <Console name="Console" target="SYSTEM_OUT">
            <PatternLayout
                    pattern="%d{HH:mm:ss.SSS} [%thread] %-5level %logger{36} - %msg%n" />
        </Console>
    </Appenders>

    <Loggers>
        <Logger name="com.baeldung.testloglevel" level="debug" />

        <Root level="info">
            <AppenderRef ref="Console" />
        </Root>
    </Loggers>
</Configuration>
```
We can set the path of our Log4J configuration by setting the logging.config property in ``application.properties``:

``logging.config=classpath:log4j-testloglevel.xml``


# SWAGGER

```
@Configuration
public class SwaggerDocumentationConfig {

	ApiInfo apiInfo() {
		return new ApiInfoBuilder().title("Container REST API - Interface").description(
				"Container REST API - Interface")
				.license("LICENCE NAME")
				.licenseUrl("https://LOCALHOST/us/en/home.html")
				.version("1.0").contact(new Contact("dEEPAK", "", "")).build();
	}

	@Bean
	public Docket customImplementation() {
		
		return new Docket(DocumentationType.SWAGGER_2).select()
				.apis(RequestHandlerSelectors.basePackage(Container2SpringBoot.class.getPackage().getName())).build();
	}
}
```

```
@Configuration
@EnableSwagger2
public class SwaggerConfig {

	public static final Contact DEFAULT_CONTACT = new Contact("abc", "sample.com", "abc@g.com");
	@SuppressWarnings("deprecation")
	public static final ApiInfo DEFAULT = new ApiInfo("SP boot rest api Documentation", "Spring boot Rest call Api Documentation", "1.0", "urn:tos",
			"Apache 2.0", "http://www.apache.org/licenses/LICENSE-2.0", "");
	private static final Set<String> DEFAULT_PRODUCE_AND_CONSUME = new HashSet<String>(Arrays.asList("application/json","application/xml"));

	@Bean
	public Docket api() {
		return new Docket(DocumentationType.SWAGGER_2).apiInfo(DEFAULT).produces(DEFAULT_PRODUCE_AND_CONSUME)
				.consumes(DEFAULT_PRODUCE_AND_CONSUME).select().apis(RequestHandlerSelectors.any())
				.paths(PathSelectors.any()).build();
	}
}
```

Use of it.
```
@Entity
@ApiModel(description = "All the details about user.")
public class User { //user->post->user(X)
	
	public User() {
		super();
	}

	@Id
	@GeneratedValue
	private Integer id;
	
	@ApiModelProperty(notes="Name should have atleast 2 characters.")
	private String name;
	
	@ApiModelProperty(notes="Birth date should be in past date.")
	private Date birthDate;
```

# Custom Exception Handling

```
@ControllerAdvice
@RestController
public class CustomizedResponseEntityExceptionHandler extends ResponseEntityExceptionHandler {
	
	
	@ExceptionHandler(Exception.class)
	public final ResponseEntity<Object> handleAllException(Exception ex, WebRequest request) {
		ExceptionResponse response = new ExceptionResponse(new Date(), ex.getMessage(), request.getDescription(false));
		return new ResponseEntity<Object>(response, HttpStatus.INTERNAL_SERVER_ERROR);
	}

	@ExceptionHandler(UserNotFoundException.class)
	public final ResponseEntity<Object> handleUserNotFoundException(UserNotFoundException ex, WebRequest request) {
		ExceptionResponse response = new ExceptionResponse(new Date(), ex.getMessage(), request.getDescription(false));
		return new ResponseEntity<Object>(response, HttpStatus.NOT_FOUND);
	}
}
```

- Application.properties
```
#spring.cloud.config.import-check.enabled=true
spring.application.name=limits-service
spring.config.import=configserver:http://localhost:8888  (Registered to Config Server)

spring.profiles.active=qa,dev #To enable both profiles
limits-service.minimum=2
limits-service.maximum=998
```

-  Cloud Config Server

```
spring.application.name=spring-cloud-config-server
server.port=8888

spring.cloud.config.server.git.uri=file:///C:/Users/thakurde/mircoservices/git-localconfig-repo/ 
```


**https://www.java4s.com/web-services/restful-web-services-jax-rs-formparam-example/#:~:text=By%20using%20%40FormParam%20annotation,would%20be%20the%20best%20choice.**

# MCs Architecture

![image](https://user-images.githubusercontent.com/29571875/137614591-38e1d21e-bbb2-405e-8e01-6c687080d803.png)


**DEPARTMENT-MICROSERVICE**

![image](https://user-images.githubusercontent.com/29571875/137614856-c806c5e8-cf3e-4ebd-97a3-5e3fb7c994fc.png)

**Similarly USER-MICROSERVICE**

![image](https://user-images.githubusercontent.com/29571875/137614948-4f2d3a18-35d2-4ca0-b0a0-a34088b733d3.png)


![image](https://user-images.githubusercontent.com/29571875/137615191-d354c1de-9688-4d55-9958-2945a97cf02e.png)


![image](https://user-images.githubusercontent.com/29571875/137615065-02aaaf41-cef5-403b-b7e5-19f9d954ba96.png)
 - Once MCs is register to Eureka, now call the another MC from Current MC doesn't require to pass the `hostname+port`.
   There could be a change to have multiple instance of same MCs running then calling the MC will get confuse and throw error.
   To Overcome from this, Loadbalancer comes into picture.

![image](https://user-images.githubusercontent.com/29571875/137615212-68991624-45ac-4ee2-86fb-c2c56e562709.png)


 **Cloud-Gateway Service**


   ![image](https://user-images.githubusercontent.com/29571875/137615287-81f81f7c-6a8c-435f-ac0b-7a0d1daf2581.png)

     - First enable the Eureka Client so it would be registered to Eureka server.
     - Now configure the application.yml or properties to route the MCs call based on the MCs name.
     
       ![image](https://user-images.githubusercontent.com/29571875/137615387-c1c47ad5-b0d8-420f-844c-a11b89cddd6f.png)
        - lb:/    -> indicate Loadbalanced
 
  - In case of MCs is down and when user trying to communicate then he should see the proper reason why he is not able to access it.
    For that, Hyristrix dashboard is configured at the Gateway MCs
    
    ![image](https://user-images.githubusercontent.com/29571875/137615648-49bdc2c8-3723-4a06-a4f9-2473db57b29f.png)

Create a new Controller class and then method for each MC call eg.. in Gateway-Microservice

![image](https://user-images.githubusercontent.com/29571875/137615695-c7390432-8a71-40bb-8d54-156676f2a42f.png)

- *Now configure this path in application.yml* 

![image](https://user-images.githubusercontent.com/29571875/137615736-d3687151-39c4-46f9-b6ce-37dbec683087.png)

- User `filters` keyword to map the circuit breaker and route the MCs call to fallBackUri path to give user the proper message, in case could hit the correct MCs.

    *Hystrix Dashboard Configuration in Gateway service*

![image](https://user-images.githubusercontent.com/29571875/137616183-53a4dc55-4c6b-41e4-aadd-5f02c726179d.png)

**Hystrix Dashboard MCs**

![image](https://user-images.githubusercontent.com/29571875/137616247-8e2d7b35-de73-4fd2-9391-c3b4897ba404.png)

![image](https://user-images.githubusercontent.com/29571875/137616307-e9922b3d-4a92-4199-8a7e-cbbf6b50d341.png)


```
#Allow access to the dashboard's web pages
hystrix:
  dashboard:
    #You can also specify a specific domain name | ip
    proxy-stream-allow-list: "*"

```


![image](https://user-images.githubusercontent.com/29571875/137625512-0f423271-6f38-44f1-8eff-a98f0f130a6e.png)

![image](https://user-images.githubusercontent.com/29571875/137625569-256a74a8-95c4-4929-a6b7-36f8a0f5aadc.png)



# CLOUD-CONFIG-SERVER

![image](https://user-images.githubusercontent.com/29571875/137625600-78baa333-65b5-4afc-b56e-0651c6fc0dc3.png)

- Now create a repository in Github and put the common `eureka configuration` in `application.yml` and confire the github location in
  in cloud-config-server.

![image](https://user-images.githubusercontent.com/29571875/137625788-9ebc789d-6ce7-4cc2-be1d-44ff57ec74ef.png)

- Now create a `bootstrap.yml` file put the cloud config server configuration in this in all MCs. and remove the eureka configuration from
  each MCs.

![image](https://user-images.githubusercontent.com/29571875/137625900-a5c91cca-e924-42a8-a078-0908f8855f09.png)

# Zipkin and Sleuth for all MCs logging like TraceId

- First download the Zipkin jar and start it.
- Add the below Zipkin configuration in all MCs.

![image](https://user-images.githubusercontent.com/29571875/137626021-48f76ce1-4093-450f-891e-4286347fd1a5.png)

Now start and run the below uri to see the traces

![image](https://user-images.githubusercontent.com/29571875/137626057-5509423a-9eb2-4a3c-923f-05bce7f30c57.png)


