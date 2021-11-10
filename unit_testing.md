
# How to test Factory design pattern ?

```
public abstract class AppleFactory {
    public Apple createInstance(final String str);
}

public class AppleFactoryImpl implements AppleFactory {
    public Apple createInstance(final String str) { // Implementation }
}
```

```
@RunWith(MockitoJUnitRunner.class)
public class MyClassTest {

    @Mock
    private AppleFactory appleFactoryMock;

    @Mock
    private Apple appleMock;

    @InjectMocks 
    MyClass myClass;

    @Before
    public void setup() {
        when(appleFactoryMock.createInstance(Matchers.anyString()).thenReturn(appleMock);
    }

    @Test
    public void myMethod(){
     ...
     ...
     ...
    }
}
```
