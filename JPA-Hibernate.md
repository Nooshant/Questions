
- If you are using Hibernate's proprietary API, you'll need the `hibernate.cfg.xml`. If you are using JPA i.e. Hibernate EntityManager, you'll need `the persistence.xml`.
- If you are using Hibernate then in hibernate.cfg.xml
```
<?xml version='1.0' encoding='utf-8'?>
<!DOCTYPE hibernate-configuration PUBLIC "-//Hibernate/Hibernate Configuration DTD 3.0//EN"
                            "http://www.hibernate.org/dtd/hibernate-configuration-3.0.dtd">

<hibernate-configuration>
   <session-factory>

       <property name="hibernate.dialect">org.hibernate.dialect.OracleDialect</property>
       <property name="hibernate.connection.driver_class">oracle.jdbc.driver.OracleDriver</property>
       <property name="hibernate.connection.url">jdbc:oracle:thin:@localhost:1521:db12c</property>
       <property name="hibernate.connection.username">simplehr2</property>
       <property name="hibernate.connection.password">12345</property>
       <property name="hibernate.show_sql">true</property>
       <property name="hibernate.connection.release_mode">auto</property>
       <property name="current_session_context_class">thread</property>
       <property name="hibernate.connection.autoReconnect">true</property>


       <mapping class="org.o7planning.tutorial.hibernate.entities.Department" />
       <mapping class="org.o7planning.tutorial.hibernate.entities.Employee" />
       <mapping class="org.o7planning.tutorial.hibernate.entities.SalaryGrade" />
       <mapping class="org.o7planning.tutorial.hibernate.entities.Timekeeper" />

   </session-factory>
 
</hibernate-configuration>
```

- `<mapping class="org.o7planning.tutorial.hibernate.entities.Department" /> ` is to map the Entity class.
- `<property name="hibernate.hbm2ddl.auto">create</property>` adding this property create the table automatically in database when session-factory is getting
   created during application start up.

- Possible value of `hibernate.hbm2ddl.auto`
   - create-drop:
   - update
   - validate
   - none



![Untitled](https://user-images.githubusercontent.com/29571875/137528133-eeb8b80b-e402-4d83-acdd-7caa9f10caa4.png)

- Column annotated with @JoinColumn is another column in that entity table which it is declared.
- https://en.wikibooks.org/wiki/Java_Persistence/OneToMany

