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
spring.config.import=configserver:http://localhost:8888

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
