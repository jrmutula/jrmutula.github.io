<h1><strong>Setter and Getter Methods and Encapsulation In Java</strong></h1>
To make the state of the managed bean accessible, you need to add setter and getter methods for that state. The createSalutation method calls the bean’s greet method, and the getSalutation method retrieves the result.

Once the setter and getter methods have been added, the bean is complete. The final code looks like this:

~~~Java
package greetings;

import javax.inject.Inject;
import javax.enterprise.context.RequestScoped;
import javax.inject.Named;

@Named
@RequestScoped
public class Printer {

    @Inject @Informal Greeting greeting;
    
    private String name;
    private String salutation;

    public void createSalutation() {
        this.salutation = greeting.greet(name);
    }

    public String getSalutation() {
        return salutation;
    }

    public void setName(String name) {
       this.name = name;
    }
    
    public void setSalutation(String salutation) {
       this.salutation = salutation;
    }

    public String getName() {
       return name;
    }
    
    public static void main(String args[]){
    Printer obj = new Printer();
    obj.setName("Jeff");
    obj.setSalutation("Hello");
    System.out.println(obj.getSalutation() + obj.getName());
    }
}

~~~
<h2><strong>Output:</strong></h2>
~~~Java
Hello Jeff
~~~