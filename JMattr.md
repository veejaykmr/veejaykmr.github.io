## About JMattr
----------
JMattr is a simple meta attribute library for java programs.  
It provides a simple way for java programmers to annotate any java class with  
meta attributes which can be queried by the program at runtime to create dynamic applications which are simple but powerful

## A brief example  
---------
The below java code snippet shows the usage of JMattr library  
		
        @Provider(
        	name = "sample.SimpleService",
            version = \"1.0\",
            doc = @Doc(
            	shortDoc = "A short documentation about this Service",
                longDoc = "A Long documentation about this service"
            ),
            meta = {
            	@Meta(name = "some_attribute", value = "Some Value which can be queried at runtime...")
            }
        )
        public class SimpleService{
        	
            public void doSomethingMethod(){
            
            }
        }

