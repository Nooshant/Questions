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
