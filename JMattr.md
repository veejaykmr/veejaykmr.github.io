## About JMattr
------
JMattr is a simple meta attribute library for java programs.  

It provides a simple way for java programmers to annotate any java class with meta attributes which can be queried by the program at runtime. This provides a simple but effective way to create loosely coupled applications which are simple but powerful 

JMattr stands for **J**ava **M**eta **attr**ibute

## A brief example  
------
The below java code snippet shows the usage of JMattr library  
		
        @Provider(
        	value = "sample.SimpleService", 
        	doc = "sample service documentation",
	        meta = {
	      	   @Meta(name = "some_attribute", value = "attribute_value1")
	        }
        )
        public class SimpleService{
        	
            public void doSomethingMethod(){
            
            }
        }

The client code snippet is shown below  
	
	//The class path scanner which loads the annotated classes in the classpath
	MetaScanner scanner = DefaultScannerFactory.getDefaultScanner();

	//post scanning get the Registry from the scanner  
	Registry registry = scanner.getRegistry();
        
	//Query the registry about the service
	SimpleService impl1 = registry.lookup("sample.SimpleService",SimpleService.class);
	impl1.doSomethingMethod();

  	
##What problem does JMattr solve?
-----
One of the key quality characteristic which is expected of a software program is the idea of a loosely coupled system.  This is a desired characteristic since a high degree of loose coupling indicates that the system is flexible to adapt to support unforeseen future requirements.

The java language has many constructs which helps the programmer to design and implement loosely coupled systems. However it is left to the programmer to design and implement such systems.  

One of the key design/architectural patterns which promotes loose coupling is **Service Oriented Design**. 

Service Oriented Design emphasizes design by contracts which helps avoid tight coupling. Along with **Abstraction** and **Encapsulation**  the programmer has the necessary tools to build loosely coupled systems.  

The key constructs advocated by Service Oriented Design are,

	1. Service
	2. Service Registry 
	3. Service Provider

The JMattr library provides these constructs and is meant to help the programmer implement **Service Oriented Design** within the JVM.  

In essence JMattr is simply a library which helps the programmer do the following,

	1. Annotate POJOs (Plain Old Java Objects) with Interfaces (or Services)
	2. Automatically register them during application startup 
	3. Lookup the registered Services  

In addition to the above JMattr allows the programmer to annotate additional Meta data about the services and later lookup using these Meta attributes. The attributes are just key value pairs which can be queried during lookup to achieve sophisticated dynamic behavior.  

One can build even sophisticated dependency injection frameworks over JMattr if they choose to.  

##Design of JMattr
----

