# bootproj02-dependencyinjection-strategydp


# **Code**
```Java
package com.vehicle.sbeans;

import org.springframework.stereotype.Component;

@Component("cEngine")
public final class CNGEngine implements IEngine {

	@Override
	public void startEngine() {
		System.out.println("CNGEngine.startEngine()");

	}

	@Override
	public void stopEngine() {
		System.out.println("CNGEngine.stopEngine()");

	}

}
package com.vehicle;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.context.ConfigurableApplicationContext;

import com.vehicle.sbeans.Vehicle;

@SpringBootApplication
public class BootProj02DependencyInjectionStrategyDpApplication {

    public static void main(String[] args) {
        //get IOC container
        ConfigurableApplicationContext ctx=SpringApplication.run(BootProj02DependencyInjectionStrategyDpApplication.class, args);
        //get target spring bean class obj ref
        Vehicle vehicle=ctx.getBean("vehicle",Vehicle.class);
        //invoke the b.method
        vehicle.journey("hyd", "goa");

        //close the container
        ctx.close();

    }

}

package com.vehicle.sbeans;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.beans.factory.annotation.Qualifier;
import org.springframework.stereotype.Component;

@Component("vehicle")
public class Vehicle {
    @Autowired
    @Qualifier("dEngine")
    private IEngine engine;

    //b,mehthod
    public   void  journey(String  startPlace,String destPlace) {
        System.out.println("Vehicle.journey()");
        engine.startEngine();
        System.out.println("Joueney started from ::"+startPlace);
        System.out.println("Journey is going on.........");

        engine.stopEngine();
        System.out.println("Joueney ended at ::"+destPlace);


    }



}

package com.vehicle.sbeans;

import org.springframework.stereotype.Component;

@Component("pEngine")
public final class PetrolEngine implements IEngine {

    @Override
    public void startEngine() {
        System.out.println("PetrolEngine.startEngine()");

    }

    @Override
    public void stopEngine() {
        System.out.println("PetrolEngine.stopEngine()");

    }

}

package com.vehicle.sbeans;

public interface IEngine {
    public  void startEngine();
    public  void stopEngine();
}

package com.vehicle.sbeans;

import org.springframework.stereotype.Component;

@Component("dEngine")
public final class DieselEngine implements IEngine {

    @Override
    public void startEngine() {
        System.out.println("DieselEngine.startEngine()");

    }

    @Override
    public void stopEngine() {
        System.out.println("DieselEngine.stopEngine()");

    }

}

```


## **_POM_**
```xml
<dependencies>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter</artifactId>
		</dependency>

		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-test</artifactId>
			<scope>test</scope>
		</dependency>
	</dependencies>
```
## **_Logs_**

## **Tables created**
![JOB_SEEKER_INFO_SEQ](/src/main/resources/UML.png)