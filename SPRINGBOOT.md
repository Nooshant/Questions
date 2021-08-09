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
