## About JMattr
----------
JMattr is a simple meta attribute library for java programs.  
It provides a simple way for java programmers to annotate any java class with  
meta attributes which can be queried by the program at runtime to create dynamic applications which are simple but powerful  JMattr stands for **J**ava **M**eta **attr**ibute 

## A brief example  
---------
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
	

