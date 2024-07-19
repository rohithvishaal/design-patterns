- [**Creational Patterns**](#creational-patterns)
  - [**Singleton**](#singleton)
    - [**Layman Explanation**](#layman-explanation)
    - [**Professional Explanation**](#professional-explanation)
    - [**Code Examples**](#code-examples)
      - [**Python**](#python)
      - [**Java**](#java)
      - [**Kotlin**](#kotlin)
  - [**Factory**](#factory)
    - [**Layman Explanation**](#layman-explanation-1)
    - [**Professional Explanation**](#professional-explanation-1)
    - [**Code Examples**](#code-examples-1)
      - [**Python**](#python-1)
      - [**Kotlin**](#kotlin-1)
      - [**Java**](#java-1)
  - [**Abstract Factory**](#abstract-factory)
    - [**Layman Explanation**](#layman-explanation-2)
    - [**Professional Explanation**](#professional-explanation-2)
    - [Differences between Factory and Abstract Factory](#differences-between-factory-and-abstract-factory)
    - [**Code Examples**](#code-examples-2)
      - [**Python**](#python-2)
      - [**Java**](#java-2)
      - [**Kotlin**](#kotlin-2)
  - [**Builder**](#builder)
    - [**Layman Explanation**](#layman-explanation-3)
    - [**Professional Explanation**](#professional-explanation-3)
    - [**Code Examples**](#code-examples-3)
      - [**Python**](#python-3)
    - [**Java**](#java-3)
      - [**Kotlin**](#kotlin-3)
  - [**Prototype**](#prototype)
    - [**Layman Explanation**](#layman-explanation-4)
    - [**Professional Explanation**](#professional-explanation-4)
    - [**Code Examples**](#code-examples-4)
      - [**Python**](#python-4)
      - [**Kotlin**](#kotlin-4)
      - [**Java**](#java-4)
- [**Structural Patterns**](#structural-patterns)
  - [**Adapter**](#adapter)
    - [**Layman Explanation**](#layman-explanation-5)
    - [**Professional Explanation**](#professional-explanation-5)
    - [**Code Examples**](#code-examples-5)
      - [**Python**](#python-5)
      - [**Kotlin**](#kotlin-5)
      - [**Java**](#java-5)
  - [**Bridge**](#bridge)
    - [**Layman Explanation**](#layman-explanation-6)
    - [**Professional Explanation**](#professional-explanation-6)
    - [**Code Examples**](#code-examples-6)
      - [**Python**](#python-6)
      - [**Kotlin**](#kotlin-6)
      - [**Java**](#java-6)
  - [**Composite**](#composite)
    - [**Layman Explanation**](#layman-explanation-7)
    - [**Professional Explanation**](#professional-explanation-7)
      - [Key Components:](#key-components)
      - [**Python**](#python-7)
      - [**Kotlin**](#kotlin-7)
      - [**Java**](#java-7)
  - [**Decorator**](#decorator)
    - [**Layman Explanation**](#layman-explanation-8)
    - [**Professional Explanation**](#professional-explanation-8)
      - [**Python**](#python-8)
      - [**Kotlin**](#kotlin-8)
      - [**Java**](#java-8)
  - [**Facade**](#facade)
    - [**Layman Explanation**](#layman-explanation-9)
    - [**Professional Explanation**](#professional-explanation-9)
    - [**Code Examples**](#code-examples-7)
      - [**Python**](#python-9)
      - [**Kotlin**](#kotlin-9)
      - [**Java**](#java-9)
  - [**Flyweight**](#flyweight)
    - [**Layman's Explanation**](#laymans-explanation)
    - [**Professional Explanation**](#professional-explanation-10)
    - [**Code Examples**](#code-examples-8)
      - [**Python**](#python-10)
      - [**Kotlin**](#kotlin-10)
      - [**Java**](#java-10)
  - [**Proxy**](#proxy)
    - [**Layman Explanation**](#layman-explanation-10)
    - [**Professional Explanation**](#professional-explanation-11)
    - [**Code Examples**](#code-examples-9)
      - [**Python**](#python-11)
      - [**Kotlin**](#kotlin-11)
      - [**Java**](#java-11)

## **Creational Patterns**
### **Singleton**

#### **Layman Explanation**
- Imagine you're at a party and there's supposed to be only one DJ. The singleton design pattern is like a special rule that ensures there's only one DJ object created throughout the entire party (your program). This DJ object can play music (perform actions) for everyone at the party (different parts of your code).

**Here's how it works**:

1. **One and Only:** The singleton class makes sure there's only one DJ object ever created. It's like the party host giving the DJ a special badge that says "You're the one and only DJ!"
2. **Global Access:** Everyone at the party (your code) can access the DJ object through a special "Get the DJ" function. It's like having a microphone to announce "Hey everyone, if you want music, go see the DJ with the badge!"

#### **Professional Explanation**
- The singleton design pattern is a creational design pattern that restricts a class to have only one instance and provide a global access point to it.
- It ensures a single object for a class and centralizes access to that object

**Benefits**
- **Global State**: Maintains a single point of access for a shared resource or state.
- **Controlled Access**: Prevents accidental creation of multiple instances
- **Efficiency**: Avoids redundant object creation for performance gains (if creating the object is expensive)

**Drawbacks**
- **Tight Coupling**: Can create tight coupling between code parts that rely on the singleton.
- **Testing Difficulty**: Can be harder to test code that depends on singleton

#### **Code Examples**
##### **Python** 

```python
class DJ:
	# Private attribute to hold the single instance
	__instance = None

	def __new__(cls):
		if not cls.__instance:
			cls.__instance = super(DJ, cls).__new__(cls)
		return cls.__instance
	
	def play_music(self):
		print("DJ is playing music!")

dj = DJ()
dj.play_music()
```

**Explanation**
- The `__new__` method is overridden to control object creation.
- If an instance doesn't exist, it's created. Otherwise, the existing one is returned.
- The `play_music` method is an example of an action the DJ object can perform.

##### **Java**

```java
public class Logger{
	private static Logger instance;
	private Logger() {} //Private constructor to prevent external instantiation
	public static synchronized Logger getInstance() {
		if (instance == null) {
			instance = new Logger();
		}
		return instance;
	}
	
	public void logMessage(String message) {
		System.out.println("Log: " + message);
	}
}

// Usage example
public class MyClass {
	public void doSomething() {
		Logger logger = Logger.getInstance();
		logger.logMessage("This is a log message");
	}
}
```

**Explanation**
- The `Logger` class has a private constructor to prevent external object creation.
- The `getInstance` method is `static` and `synchronized` to ensure thread-safe creation of the single instance
- The `logMessage` method is an example of an action the `Logger` object can perform.

##### **Kotlin**

```kotlin
object DJ {
	private var instance: DJ? = null
	fun getInstance(): DJ {
		if (instance == null) {
			instance = DJ()
		}
		return instance!!
	}
	fun playMusic(){
		println("DJ is playing music")
	}
}

// Accessing the DJ object
val dj = DJ.getInstance()
dj.playMusic()
```

**Explanation**
- The `DJ`  object is declared with the `object` keyword, making it a singleton.
- The `getInstance` method checks for an existing instance and creates one if necessary.
- The `playMusic` method is an example of an action the DJ object can perform.

**In Conclusion** :
The singleton design pattern can be useful when you need a single, globally accessible object for a specific purpose. However, it's important to consider its drawbacks and use it judiciously in your code.

---
### **Factory**
#### **Layman Explanation**
Imagine you have a toy factory that makes different types of toys: cars, dolls and robots. Instead of manually creating each toy yourself every time you need one, you have a machine(a factory) that knows how to make each type of toy. You just tell the machine which toy you want and it gives you the toy. This way, you don't need to worry about the details of how each toy is made; the factory takes care of that for you

In programming, the Factory Design Pattern is like toy factory. Instead of creating objects directly, you use a special method (a factory method) to create objects. This method decides which specific object to create based on some input or conditions. This makes your code simpler and more flexible because you don't need to know the details of how each object is created.

#### **Professional Explanation**
The Factory Design Pattern is a **Creational** Design Pattern that provides an interface for creating objects in a superclass, but allows sub-classes to alter the type of objects that will be created. Instead of instantiating objects directly, the client uses a factory method to create the objects, promoting loose coupling and greater flexibility in the codebase.

The Factory Design Pattern is particularly useful when:
- The exact type of object that needs to be created is determined at runtime.
- The creation process involves a complex logic that should be centralized in one place.
- The system needs to adhere to the Open/Closed Principle, allowing new types to be added without modifying the existing code.

#### **Code Examples**
##### **Python**
```python
from abc import ABC, abstractmethod
class Toy(ABC):
	@abstractmethod
	def create(self):
		pass

# Concrete products
class Car(Toy):
	def create(self):
		return "Car created"

class Doll(Toy):
	def create(self):
		return "Doll created"

class Robot(Toy):
	def create(self):
		return "Robot created"

# Factory class
class ToyFactory:
	@staticmethod
	def get_toy(toy_type: str) -> Toy:
		if toy_type == "car":
			return Car()
		elif toy_type == "doll":
			return Doll()
		elif toy_type == "robot":
			return Robot()
		else:
			raise ValueError("Unknown toy type")

if __name__ == "__main__":
	toy = ToyFactory().get_toy("car")
	print(toy.create())	
```

##### **Kotlin**
```kotlin
// Abstract product
interface toy() { 
	fun create(): String
}

// Concrete products
class Car: Toy {
	override fun create() = "Car created"
}

class Doll: Toy {
	override fun create() = "Doll created"
}

class Robot: Toy {
	override fun create() = "Robot created"
}

// Factory class
object ToyFactory {
	fun getToy(toyType: String): Toy {
		return when(toyType) {
			"car" -> Car()
			"doll" -> Doll()
			"robot" -> Robot()
			else -> throw IllegalArgumentException("Unknown toy type")
		}
	}
}

fun main() { 
	val toy = ToyFactory.getToy("car") 
	println(toy.create()) 
}
```

##### **Java**

```java
// Abstract product
interface Toy {
	String create();
}

// Concrete products

class Car implements Toy {
	@Override 
	public String create() {
		return "Car created";
	}
}

class Doll implements Toy {
	@Override
	public String create() {
		return "Doll created";
	}
}

class Robot implements Toy {
	@Override
	public String create() {
		return "Robot created";
	}
}

//Factory class
class ToyFactory {
	public static Toy getToy(String toyType) {
		switch (toyType) {
			case "car":
				return new Car();
			case "doll":
				return new Doll();
			case "robot":
				return new Robot();
			default:
				throw new IllegalArgumentException("Unknown toy type");
		}
	}
}

public class Main {
	public static void main(String[] args) {
		Toy toy = new ToyFactory().getToy("car");
		System.out.println(toy.create());
	}
}
```

---
### **Abstract Factory**

#### **Layman Explanation**

Imagine you're building different types of houses. Each house can have different types of windows, doors, and roofs. You don't want to decide what specific windows, doors, or roofs to use each time you build a house. Instead, you want a blueprint that you can give you the right type of windows, doors, roofs for a specific house style.

The abstract factory pattern is like having a set of blueprints (factories) for different house styles. Each blueprint knows exactly what components (windows, doors, roofs) are needed for that style, and you just use the blueprint to get all the right parts.

#### **Professional Explanation**

The abstract factory pattern is a **creational** design pattern that provides an interface for creating families of related or dependent objects without specifying their concrete classes. This pattern is useful when a system needs to be independent of how objects are created, composed, and represented

In more technical terms, the abstract factory pattern is about creating a super-factory that creates other factories. It allows you to produce families of related objects without specifying their concrete classes.

#### Differences between Factory and Abstract Factory

| Feature     | Factory Method Pattern                        | Abstract Factory Pattern                                 |
| ----------- | --------------------------------------------- | -------------------------------------------------------- |
| Purpose     | Creates one type of product                   | Creates families of related products                     |
| Complexity  | Simpler, deals with one product at a time     | More complex, handles multiple related products          |
| Flexibility | Less flexible, hard to introduce new products | More flexible, easier to introduce new product families  |
| Use Case    | Use when creation of a single product varies  | Use when creation of families of products varies         |
| Structure   | Single creator class                          | Multiple factory classes implementing a common interface |
#### **Code Examples**

##### **Python**

```python
from abc import ABC, abstractmethod

# Abstract Factory
class FurnitureFactory(ABC):
	@abstractmethod
	def create_chair(self):
		pass
	
	@abstractmethod
	def create_sofa(self):
		pass

# Concrete Factory 1
class VictorianFurnitureFactory(FurnitureFactory):
	def create_chair(self):
		return VictorianChair()

	def create_sofa(self):
		return VictorianSofa()

# Concrete Factory 2
class ModernFurnitureFactory(FurnitureFactory):
	def create_chair(self):
		return ModernChair()
	
	def create_sofa(self):
		return ModernSofa()

# Abstract Products
class Chair(ABC):
	@abstractmethod
	def sit_on(self):
		pass

class Sofa(ABC):
	@abstractmethod
	def lie_on(self):
		pass

# Concrete Products
class VictorianChair(Chair):
	def sit_on(self):
		return "Sitting on a Victorian Chair"

class VictorianSofa(Sofa):
	def lie_on(self):
		return "Lying on a Victorian Sofa"

class ModernChair(Chair):
	def sit_on(self):
		return "Sitting on a Modern Chair"

class ModernSofa(Sofa):
	def lie_on(self):
		return "Lying on a Modern Sofa"

def client_code(factory: FurnitureFactory):
	chair = factory.create_chair()
	sofa = factory.create_sofa()
	print(chair.sit_on())
	print(sofa.lie_on())

client_code(VictorianFurnitureFactory())
client_code(ModernFurnitureFactory())
	
```

##### **Java**

```java
// Abstract Factory
interface FurnitureFactory {
	Chair createChair();
	Sofa createSofa();
}

// Concrete Factory 1
class VictorianFurnitureFactory implements FurnitureFactory {

	public Chair createChair() {
		return new VictorianChair();
	}

	public Sofa createSofa() {
		return new VictorianSofa();
	}
}

// Concrete Factory 2
class ModernFurnitureFactory implements FurnitureFactory {

	public Chair createChair() {
		return new ModernChair();
	}

	public Sofa createSofa() {
		return new ModernSofa();
	}
}

// Abstract Products
interface Chair {
	String sitOn(); 
}

interface Sofa {
	String lieOn();
}

// Concrete Products
class VictorianChair implements Chair {
	public String sitOn() {
		return "Sitting on a Victorian Chair";
	}
}

class VictorianSofa implements Sofa {
	public String lieOn() {
		return "Lying on a Victorian Sofa";
	}
}

class ModernChair implements Chair {
	public String sitOn() {
		return "Sitting on a Modern Chair";
	}
}

class ModernSofa implements Sofa {
	public String lieOn() {
		return "Lying on a Modern Sofa";
	}
}

// Client Code
public class Client {
	public static void main(String[] args) {
		clientCode(new VictorianFurnitureFactory());
		clientCode(new ModernFurnitureFactory());
	}

	public static void clientCode(FurnitureFactory factory) {
		Chair chair = factory.createChair();
		Sofa sofa = factory.createSofa();
		System.out.println(chair.sitOn());
		System.out.println(sofa.lieOn());
	}
}
```

##### **Kotlin**

```kotlin
// Abstract Factory
interface FurnitureFactory {
	fun createChair() : Chair
	fun createSofa() : Sofa
}

// Concrete Factory 1
class VictorianFurnitureFactory : FurnitureFactory {
	
	override fun createChair() : Chair {
		return VictorianChair()
	}
	
	override fun createSofa() : Sofa {
		return VictorianSofa()
	}
	
}

// Concrete Factory 2
class ModernFurnitureFactory : FurnitureFactory {

	override fun createChair() : Chair {
		return ModernChair()
	}
	
	override fun createSofa() : Sofa {
		return ModernSofa()
	}
}

// Abstract Products
interface Chair {
	fun sitOn(): String
}

interface Sofa {
	fun lieOn(): String
}

// Concrete products
class VictorianChair : Chair {
	override fun sitOn() : String {
		return "Sitting on a Victorian Chair"
	}
}

class VictorianSofa : Sofa {
	override fun lieOn() : String {
		return "Lying on a Victorian Sofa"
	}
}

class ModernChair : Chair {
	override fun sitOn() : String {
		return "Sitting on a Modern Chair"
	}
}

class ModernSofa : Sofa {
	override fun lieOn() : String {
		return "Lying on a Modern Sofa"
	}
}

// Client Code
fun clientCode(factory : FurnitureFactory) {
	val chair = factory.createChair()
	val sofa = factory.createSofa()
	println(chair.sitOn())
	println(sofa.lieOn())
}

fun main() {
	clientCode(VictorianFurnitureFactory())
	clientCode(ModernFurnitureFactory())
}
```

---
### **Builder**
#### **Layman Explanation**

Imagine you're ordering a custom pizza. you don't have to tell the chef everything at once (crust, sauce, cheese, toppings). Instead, you can specify each ingredient one by one. The Builder design pattern is similar. It lets you create complex objects step-by-step, customizing them as you go

The builder design pattern works similarly in programming. It's used to construct complex objects step by step. Instead of creating an object all at once, you build it piece by piece, making it easier to manage and understand.

#### **Professional Explanation**

The Builder Design Pattern is a creational design pattern that lets you construct complex objects step by step. The pattern separates the construction of a complex object from its representation, allowing the same construction process to create different representations. It is particularly useful when an object has many optional parameters or when the construction process is complex.

#### **Code Examples**

##### **Python**

```python
class Pizza:
	def __init__(self, crust, cheese, toppings, size):
		self.crust = crust
		self.cheese = cheese
		self.toppings = toppings
		self.size = size

	def __str__(self):
		return f"Pizza: {self.crust} crust, {self.cheese} cheese, {self.toppings}, size {self.size}"

class PizzaBuilder:
	def __init__(self):
		self.crust = None
		self.cheese = None
		self.toppings = []
		self.size = None

	def with_crust(self, crust):
		self.crust = crust
		return self

	def with_sauce(self, sauce):
		self.sauce = sauce
		return self

	def with_cheese(self, cheese):
		self.cheese = cheese
		return self

	def with_toppings(self, topping):
		self.toppings.append(topping)
		return self
	
	def with_size(self, size):
	    self.size = size
	    return self

	def build(self):
		return Pizza(self.crust, self.cheese, self.toppings, self.size)

# Usage
builder = PizzaBuilder()
pizza = builder.with_crust("Thin") \
				.with_cheese("Mozzarella") \
				.with_toppings("Pepperoni") \
				.with_toppings("mushrooms") \
				.with_size("Large") \
				.build()
print(pizza)	
```

#### **Java**
```java
import java.util.*;
public class Pizza {
    private String crust;
    private String cheese;
    private List<String> toppings;
    private String size;

    private Pizza(Builder builder) {
        this.crust = builder.crust;
        this.cheese = builder.cheese;
        this.toppings = builder.toppings;
        this.size = builder.size;
    }

    @Override
    public String toString() {
        return "Pizza: " + crust + " crust, " + cheese + " cheese, " + toppings + ", size " + size;
    }

    public static class Builder {
        private String crust;
        private String cheese;
        private List<String> toppings = new ArrayList<>();
        private String size;

        public Builder setCrust(String crust) {
            this.crust = crust;
            return this;
        }

        public Builder setCheese(String cheese) {
            this.cheese = cheese;
            return this;
        }

        public Builder addTopping(String topping) {
            this.toppings.add(topping);
            return this;
        }

        public Builder setSize(String size) {
            this.size = size;
            return this;
        }

        public Pizza build() {
            return new Pizza(this);
        }
    }

    public static void main(String[] args) {
        Pizza pizza = new Pizza.Builder()
            .setCrust("Thin")
            .setCheese("Mozzarella")
            .addTopping("Pepperoni")
            .setSize("Large")
            .build();
        
        System.out.println(pizza);
    }
}

```

##### **Kotlin**
```kotlin
data class Pizza(val crust: String, val cheese: String, val  toppings: MutableList<String>, val size: String);

class PizzaBuilder {
    
    private var crust: String? = null
    private var cheese: String? = null
    private var toppings: MutableList<String> = mutableListOf()
    private var size: String? = null
    
    fun withCrust(crust: String): PizzaBuilder {
        this.crust = crust
        return this
    }
    
    fun withCheese(cheese: String): PizzaBuilder {
        this.cheese = cheese
        return this
    }
    
    fun withToppings(topping: String): PizzaBuilder {
        this.toppings.add(topping)
        return this
    }
    
    fun withSize(size: String): PizzaBuilder {
    	this.size = size
        return this
    }
    
    fun build(): Pizza {
        return Pizza(crust!!, cheese!!, toppings, size!!)
    }
    
}

fun main() {
    val pizza: Pizza = PizzaBuilder().withCrust("Thin") 
    					.withCheese("Mozarella") 
                        .withToppings("Pepperoni") 
                        .withToppings("Mushrooms") 
                        .withSize("Large")
                        .build()
    println(pizza)
    			
}
```

---
### **Prototype**
#### **Layman Explanation**

Imagine you have a special toy, and you want to make more of the exact same toy. Instead of building each toy from scratch, you can use the first toy as a model and create copies of it. This is what the Prototype Design Pattern does. It allows you to create new objects by copying an existing object, which serves as a prototype.

#### **Professional Explanation**

The Prototype Design Pattern is a **creational** design pattern that allows you to create new objects by copying an existing object, known as the prototype. This pattern is useful when the cost of creating a new object is more expensive than cloning an existing one. The pattern includes a prototype interface which declares a method for cloning itself. Concrete classes implement this interface and provide the actual cloning method.

#### **Code Examples**

##### **Python**

```python
import copy

class Prototype:
    def clone(self):
        return copy.deepcopy(self)

class ConcretePrototype(Prototype):
    def __init__(self, name, value):
        self.name = name
        self.value = value

    def __str__(self):
        return f"Name: {self.name}, Value: {self.value}"

# Usage
original = ConcretePrototype("Original", 42)
clone = original.clone()

print(original)  # Output: Name: Original, Value: 42
print(clone)     # Output: Name: Original, Value: 42

```

##### **Kotlin**

```kotlin

interface Prototype {
    fun clone(): Prototype
}

data class ConcretePrototype(val name: String, val value: Int) : Prototype {
    override fun clone(): Prototype {
        return copy()
    }
}

fun main() {
    val original = ConcretePrototype("Original", 42)
    val clone = original.clone() as ConcretePrototype

    println(original)  // Output: ConcretePrototype(name=Original, value=42)
    println(clone)     // Output: ConcretePrototype(name=Original, value=42)
}

```

##### **Java**

```java

interface Prototype {
    Prototype clone();
}

public class ConcretePrototype implements Prototype {
    private String name;
    private int value;

    public ConcretePrototype(String name, int value) {
        this.name = name;
        this.value = value;
    }

    @Override
    public Prototype clone() {
        return new ConcretePrototype(name, value);
    }

    @Override
    public String toString() {
        return "Name: " + name + ", Value: " + value;
    }

    public static void main(String[] args) {
        ConcretePrototype original = new ConcretePrototype("Original", 42);
        ConcretePrototype clone = (ConcretePrototype) original.clone();

        System.out.println(original);  // Output: Name: Original, Value: 42
        System.out.println(clone);     // Output: Name: Original, Value: 42
    }
}

```
 ---
## **Structural Patterns** 
### **Adapter**
#### **Layman Explanation**

Imagine you have a plug that fits into a specific socket. However, when you travel to a different country, the sockets are different, and your plug doesn't fit. Instead of buying a new device, you use a travel adapter. This adapter has the right plug for the socket and the right socket for your plug. This way, your device works perfectly fine in the new country without any modification.

#### **Professional Explanation**

The Adapter Pattern is a structural design pattern that allows objects with incompatible interfaces to work together. It acts as a bridge between two incompatible interfaces. This pattern involves a single class, which is responsible for joining functionalities of independent or incompatible interfaces. An Adapter wraps an existing class with a new interface so that it becomes compatible with the client’s interface.

#### **Code Examples**

##### **Python**

```python

from abc import ABC, abstractmethod

class Socket(ABC):
    @abstractmethod
    def num_prongs(self):
        pass

class IndianSocket(Socket):
    def num_prongs(self):
        return "Plug with 3 prongs"

class USSocket(Socket):
    def num_prongs(self):
        return "Plug with 2 prongs"

class DualAdapter:
    def __init__(self, source_socket, target_socket):
        self.source_socket = source_socket
        self.target_socket = target_socket
    
    def plug_in(self):
        return f"{self.source_socket.num_prongs()} attached to {self.target_socket.num_prongs()} and plugged into power source"

if __name__ == "__main__":
    indian_socket = IndianSocket()
    us_socket = USSocket()
    print(DualAdapter(indian_socket, us_socket).plug_in())
    print(DualAdapter(us_socket, indian_socket).plug_in())
    
```

##### **Kotlin**

```kotlin

interface Socket {
    fun numProngs():String
}

class IndianSocket: Socket {
    override fun numProngs(): String {
        return "Plug with 3 prongs"
    }
}

class USSocket: Socket {
    override fun numProngs(): String {
        return "Plug with 2 prongs"
    }
}

class DualAdapter(private val sourceSocket: Socket, private val targetSocket: Socket) {
    fun plugIn(): String {
        return "${sourceSocket.numProngs()} attached to ${targetSocket.numProngs()}"
    }
}

fun main() {
    val indianSocket: Socket = IndianSocket()
    val usSocket: Socket = USSocket()
    println(DualAdapter(indianSocket, usSocket).plugIn())
    println(DualAdapter(usSocket, indianSocket).plugIn())
}

```

##### **Java**

```java
interface Socket {
    String numProngs();
}

class IndianSocket implements Socket {
    @Override
    public String numProngs() {
        return "Plug with 3 prongs";
    }
}

class USSocket implements Socket {
    @Override
    public String numProngs() {
        return "Plug with 2 prongs";
    }
}

class DualAdapter implements Socket { // Adapter implements the interface
    Socket sourceSocket;
    Socket targetSocket;

    public DualAdapter(Socket sourceSocket, Socket targetSocket) {
        this.sourceSocket = sourceSocket;
        this.targetSocket = targetSocket;
    }

    @Override
    public String numProngs() {
        return sourceSocket.numProngs() + " attached to " + targetSocket.numProngs(); // Delegate and combine info
    }
}

class Main {
    public static void main(String[] args) {
        Socket adapter = new DualAdapter(new IndianSocket(), new USSocket()); // Use the adapter as a Socket
        System.out.println(adapter.numProngs());
    }
}
```

---
### **Bridge**

#### **Layman Explanation**

Imagine you're building a remote control for various devices (TV, stereo, etc.). You want the remote's buttons (abstraction) to work with different devices (implementation) without needing to modify the buttons themselves.

The Bridge pattern achieves this by separating the "what" (abstraction) from the "how" (implementation). The buttons (abstraction) define what actions to take (e.g., volume up, channel change), while the device-specific code (implementation) handles how those actions are carried out (IR codes, network commands, etc.).

#### **Professional Explanation**

The Bridge pattern is a structural design pattern that decouples an abstraction (what) from its implementation (how) so they can vary independently. This promotes loose coupling, flexibility, and maintainability.

Here are the key elements:

- **Abstraction:** Defines the interface for using an object. It can have subclasses (refined abstractions) that extend the functionality.
- **Implementation:** Defines the operations to be performed. It can have subclasses (concrete implementations) that provide specific implementations.
- **Bridge:** The abstraction holds a reference to an implementation object. It delegates calls to the implementation object to perform the actual work.

#### **Code Examples**

##### **Python**

```python

class RemoteControl:
    def __init__(self, device):
        self.device = device

    def turn_on(self):
        self.device.turn_on()

    def turn_off(self):
        self.device.turn_off()

    def volume_up(self):
        self.device.volume_up()

    # ... other methods for specific actions

class TV:
    def turn_on(self):
        print("TV turned on")

    def turn_off(self):
        print("TV turned off")

    def volume_up(self):
        print("TV volume up")

# ... similar classes for Stereo, etc.

# Usage
tv_remote = RemoteControl(TV())
tv_remote.turn_on()  # Output: TV turned on

```

##### **Kotlin**

```kotlin

interface Device {
    fun turnOn()
    fun turnOff()
    fun volumeUp()
}

class TV : Device {
    override fun turnOn() {
        println("TV turned on")
    }

    override fun turnOff() {
        println("TV turned off")
    }

    override fun volumeUp() {
        println("TV volume up")
    }
}

// ... similar classes for Stereo, etc.

class RemoteControl(private val device: Device) {
    fun turnOn() {
        device.turnOn()
    }

    fun turnOff() {
        device.turnOff()
    }

    fun volumeUp() {
        device.volumeUp()
    }
}

fun main() {
    val tvRemote = RemoteControl(TV())
    tvRemote.turnOn()
}

```

##### **Java**

```java

interface Device {
    void turnOn();
    void turnOff();
    void volumeUp();
}


class TV implements Device {
    @Override
    public void turnOn() {
        System.out.println("TV turned on");
    }

    @Override
    public void turnOff() {
        System.out.println("TV turned off");
    }

    @Override
    public void volumeUp() {
        System.out.println("TV volume up");
    }
}

// ... similar classes for Stereo, etc.

class RemoteControl {
    private final Device device;

    public RemoteControl(Device device) {
        this.device = device;
    }

    public void turnOn() {
        device.turnOn();
    }

    public void turnOff() {
        device.turnOff();
    }

    public void volumeUp() {
        device.volumeUp();
    }
}

class Main {
    public static void main(String[] args) {
        RemoteControl tvRemote = new RemoteControl(new TV());
        tvRemote.turnOn();
    }
}

```

---

### **Composite**

#### **Layman Explanation**

In simple terms, the Composite Design Pattern is like having a tree structure where each branch and leaf can be treated the same way. Imagine you have a folder on your computer that contains files and other folders. Those other folders can also contain files and more folders, and so on. The composite pattern allows you to treat both files and folders uniformly, so you can perform operations like opening, deleting, or moving them, regardless of whether they are individual files or entire folders.

#### **Professional Explanation**

The Composite Design Pattern is a structural pattern that allows you to compose objects into tree structures to represent part-whole hierarchies. It lets clients treat individual objects and compositions of objects uniformly. This pattern provides a way to access and manipulate a hierarchy of objects in a consistent manner, making it easier to work with complex structures of objects.

##### Key Components:

1. **Component**: An abstract class or interface that declares the interface for objects in the composition.
2. **Leaf**: A class that represents leaf objects in the composition. A leaf has no children.
3. **Composite**: A class that represents an object that has children. It implements the component interface and provides methods to add, remove, and access child components.

##### **Python**

```python

from abc import ABC, abstractmethod

class Graphic(ABC):
    @abstractmethod
    def draw(self):
        pass

class Circle(Graphic):
    def draw(self):
        print("Drawing a Circle")

class Square(Graphic):
    def draw(self):
        print("Drawing a Square")

class CompositeGraphic(Graphic):
    def __init__(self):
        self.graphics = []

    def add(self, graphic):
        self.graphics.append(graphic)

    def remove(self, graphic):
        self.graphics.remove(graphic)

    def draw(self):
        for graphic in self.graphics:
            graphic.draw()

# Usage
circle1 = Circle()
circle2 = Circle()
square = Square()

composite_graphic = CompositeGraphic()
composite_graphic.add(circle1)
composite_graphic.add(circle2)
composite_graphic.add(square)

composite_graphic.draw()

```

##### **Kotlin**

```kotlin

interface Graphic {
    fun draw()
}

class Circle : Graphic {
    override fun draw() {
        println("Drawing a Circle")
    }
}

class Square : Graphic {
    override fun draw() {
        println("Drawing a Square")
    }
}

class CompositeGraphic : Graphic {
    private val graphics = mutableListOf<Graphic>()

    fun add(graphic: Graphic) {
        graphics.add(graphic)
    }

    fun remove(graphic: Graphic) {
        graphics.remove(graphic)
    }

    override fun draw() {
        for (graphic in graphics) {
            graphic.draw()
        }
    }
}

// Usage
fun main() {
    val circle1 = Circle()
    val circle2 = Circle()
    val square = Square()

    val compositeGraphic = CompositeGraphic()
    compositeGraphic.add(circle1)
    compositeGraphic.add(circle2)
    compositeGraphic.add(square)

    compositeGraphic.draw()
}

```

##### **Java**

```java

import java.util.ArrayList;
import java.util.List;

interface Graphic {
    void draw();
}

class Circle implements Graphic {
    public void draw() {
        System.out.println("Drawing a Circle");
    }
}

class Square implements Graphic {
    public void draw() {
        System.out.println("Drawing a Square");
    }
}

class CompositeGraphic implements Graphic {
    private List<Graphic> graphics = new ArrayList<>();

    public void add(Graphic graphic) {
        graphics.add(graphic);
    }

    public void remove(Graphic graphic) {
        graphics.remove(graphic);
    }

    public void draw() {
        for (Graphic graphic : graphics) {
            graphic.draw();
        }
    }
}

// Usage
public class CompositePatternDemo {
    public static void main(String[] args) {
        Graphic circle1 = new Circle();
        Graphic circle2 = new Circle();
        Graphic square = new Square();

        CompositeGraphic compositeGraphic = new CompositeGraphic();
        compositeGraphic.add(circle1);
        compositeGraphic.add(circle2);
        compositeGraphic.add(square);

        compositeGraphic.draw();
    }
}

```

---

### **Decorator**

#### **Layman Explanation**

Imagine you have a plain hamburger. It's good, but you might want to add some toppings to customize it. The Decorator pattern lets you do this in your code. You start with a base object (the hamburger) and then "wrap" it with additional functionality (the toppings) without changing the original object itself. These wrappers are called decorators.

Here's the analogy:

1. **Base Object (Hamburger):** This is the core functionality you want to extend. In the hamburger example, it's the basic patty and bun.
2. **Decorators (Toppings):** These are independent classes that add specific features to the base object. Cheese, lettuce, tomato, etc., would be decorators in this case.
3. **Customization (Building the Final Burger):** You can combine different decorators (toppings) in any order to create the exact burger you want. You can have a cheeseburger, a BLT, or a veggie burger, using the same base but with different combinations of decorators.

This approach keeps your code clean and flexible. You can easily add new features (toppings) without modifying the base object (hamburger).

#### **Professional Explanation**

The Decorator design pattern is a structural design pattern that allows you to attach additional responsibilities to an object dynamically, at runtime. This provides a flexible alternative to subclassing for behaviour extension.

**Benefits:**

- **Flexibility:** You can add or remove functionality on an object-by-object basis, making your code more adaptable.
- **Open/Closed Principle:** The base object remains closed for modification, but open for extension through decorators.
- **Code Reusability:** Decorators can be reused with different objects, promoting code efficiency.

**Drawbacks:**

- **Complexity:** Can introduce additional classes and potentially increase code complexity if overused.
- **Performance Overhead:** Adding layers of decorators might have a slight performance impact

##### **Python**

```python

from abc import ABC, abstractmethod

class Pizza(ABC):
    @abstractmethod
    def get_description(self) -> str:
        pass

    @abstractmethod
    def get_cost(self) -> int:
        pass

class BasicPizza(Pizza):
    def get_description(self) -> str:
        return "Basic Pizza"

    def get_cost(self) -> int:
        return 5

class PizzaDecorator(Pizza, ABC):
    def __init__(self, pizza: Pizza):
        self.pizza = pizza

    def get_description(self) -> str:
        return self.pizza.get_description()

    def get_cost(self) -> int:
        return self.pizza.get_cost()

class CheeseDecorator(PizzaDecorator):
    def get_description(self) -> str:
        return f"{self.pizza.get_description()} with Cheese"

    def get_cost(self) -> int:
        return self.pizza.get_cost() + 1

class PepperoniDecorator(PizzaDecorator):
    def get_description(self) -> str:
        return f"{self.pizza.get_description()} with Pepperoni"

    def get_cost(self) -> int:
        return self.pizza.get_cost() + 2

# Create a basic pizza
pizza = BasicPizza()
print(pizza.get_description(), ", Cost:", pizza.get_cost())

# Add cheese to the pizza
pizza = CheeseDecorator(pizza)
print(pizza.get_description(), ", Cost:", pizza.get_cost())

# Add pepperoni to the cheese pizza
pizza = PepperoniDecorator(pizza)
print(pizza.get_description(), ", Cost:", pizza.get_cost())

```

##### **Kotlin**

```kotlin

interface Pizza {
    fun getDescription(): String
    fun getCost(): Int
}

class BasicPizza : Pizza {
    override fun getDescription(): String = "Basic Pizza"
    override fun getCost(): Int = 5
}

open class PizzaDecorator(protected val pizza: Pizza) : Pizza { // Change visibility to 'protected'
    override fun getDescription(): String = pizza.getDescription()
    override fun getCost(): Int = pizza.getCost()
}

class CheeseDecorator(pizza: Pizza) : PizzaDecorator(pizza) {
    override fun getDescription(): String = "${pizza.getDescription()} with Cheese"
    override fun getCost(): Int = pizza.getCost() + 1
}

class PepperoniDecorator(pizza: Pizza) : PizzaDecorator(pizza) {
    override fun getDescription(): String = "${pizza.getDescription()} with Pepperoni"
    override fun getCost(): Int = pizza.getCost() + 2
}

fun main() {
    val basicPizza = BasicPizza()
    println(basicPizza.getDescription() + ", Cost: " + basicPizza.getCost()) // Output: Basic Pizza, Cost: 5

    // Add cheese decoration
    val cheesePizza = CheeseDecorator(basicPizza)
    println(cheesePizza.getDescription() + ", Cost: " + cheesePizza.getCost()) // Output: Basic Pizza with Cheese, Cost: 6

    // Add pepperoni decoration (on top of cheese)
    val pepperoniPizza = PepperoniDecorator(cheesePizza)
    println(pepperoniPizza.getDescription() + ", Cost: " + pepperoniPizza.getCost()) // Output: Basic Pizza with Cheese with Pepperoni, Cost: 7
}

```

##### **Java**

```java

interface Pizza {
    String getDescription();
    int getCost();
}

class BasicPizza implements Pizza {
    @Override
    public String getDescription() {
        return "Basic Pizza";
    }

    @Override
    public int getCost() {
        return 5;
    }
}

abstract class PizzaDecorator implements Pizza {
    protected final Pizza pizza;

    public PizzaDecorator(Pizza pizza) {
        this.pizza = pizza;
    }

    @Override
    public String getDescription() {
        return pizza.getDescription();
    }

    @Override
    public int getCost() {
        return pizza.getCost();
    }
}

class CheeseDecorator extends PizzaDecorator {
    public CheeseDecorator(Pizza pizza) {
        super(pizza);
    }

    @Override
    public String getDescription() {
        return super.getDescription() + " with Cheese";
    }

    @Override
    public int getCost() {
        return super.getCost() + 1;
    }
}

class PepperoniDecorator extends PizzaDecorator {
    public PepperoniDecorator(Pizza pizza) {
        super(pizza);
    }

    @Override
    public String getDescription() {
        return super.getDescription() + " with Pepperoni";
    }

    @Override
    public int getCost() {
        return super.getCost() + 2;
    }
}

public class Main {
    public static void main(String[] args) {
        Pizza basicPizza = new BasicPizza();
        System.out.println(basicPizza.getDescription() + ", Cost: $" + basicPizza.getCost()); // Output: Basic Pizza, Cost: $5

        // Add cheese decoration
        Pizza cheesePizza = new CheeseDecorator(basicPizza);
        System.out.println(cheesePizza.getDescription() + ", Cost: $" + cheesePizza.getCost()); // Output: Basic Pizza with Cheese, Cost: $6

        // Add pepperoni decoration (on top of cheese)
        Pizza pepperoniPizza = new PepperoniDecorator(cheesePizza);
        System.out.println(pepperoniPizza.getDescription() + ", Cost: $" + pepperoniPizza.getCost()); // Output: Basic Pizza with Cheese with Pepperoni, Cost: $8
    }
}

```

---

### **Facade**

#### **Layman Explanation**

Imagine you're at a restaurant. You don't have to deal with the complexities of the kitchen – chopping ingredients, operating grills, and coordinating various tasks. Instead, you simply look at the menu (a simplified interface) and order what you want. The waiter (the Facade) takes care of everything behind the scenes, interacting with the chefs, dishwashers, and other staff (the subsystem) to fulfill your request.

The Facade Design Pattern works similarly in software development. It provides a simplified interface to a complex subsystem, hiding the intricate details of how things work internally. This makes the code easier to use and understand for developers who only need to interact with the high-level functionality.

#### **Professional Explanation**

The Facade Design Pattern is a structural design pattern that simplifies access to a complex subsystem. It introduces a single class (the Facade) that acts as a central point of communication between the client code and the subsystem's components.

**Benefits:**

- **Simplified Interface:** Reduces complexity for clients by providing a concise set of methods to interact with the subsystem.
- **Decoupling:** Isolates the client code from changes within the subsystem, promoting maintainability.
- **Improved Testability:** Facilitates easier testing of the client code as it only interacts with the Facade.
- **Flexibility:** The Facade can provide additional functionalities on top of the subsystem's capabilities.

#### **Code Examples**

##### **Python**

```python

class Light:
    def __init__(self, location):
        self.location = location

    def turn_on(self):
        print(f"{self.location} light is on")

    def turn_off(self):
        print(f"{self.location} light is off")

class Stereo:
    def __init__(self):
        self.volume = 0

    def on(self):
        print("Stereo is on")
    
    def off(self):
        print("Stereo is off")

    def set_volume(self, volume):
        self.volume = volume
        print(f"Stereo volume set to {volume}")

class HomeTheaterFacade:
    def __init__(self, light1, light2, stereo):
        self.lights = [light1, light2]
        self.stereo = stereo

    def watch_movie(self):
        print("Preparing for movie night...")
        for light in self.lights:
            light.turn_off()
        self.stereo.on()
        self.stereo.set_volume(11)  # Adjust volume as needed

    def end_movie(self):
        print("Ending movie night...")
        for light in self.lights:
            light.turn_on()
        self.stereo.off()


# Usage
living_room_light = Light("Living Room")
kitchen_light = Light("Kitchen")
home_theater = HomeTheaterFacade(living_room_light, kitchen_light, Stereo())

home_theater.watch_movie()
# Output:
# Preparing for movie night...
# Living Room light is off
# Kitchen light is off
# Stereo is on
# Stereo volume set to 11

home_theater.end_movie()
# Output:
# Ending movie night...
# Living Room light is on
# Kitchen light is on
# Stereo is off
```

##### **Kotlin**

```kotlin

class Light(val location: String) {

  fun turnOn() = println("$location light is on")

  fun turnOff() = println("$location light is off")
}

class Stereo {

  private var volume = 0

  fun on() = println("Stereo is on")

  fun off() = println("Stero is off")

  fun setVolume(volume: Int) {
    this.volume = volume
    println("Stereo volume set to $volume")
  }
}

class HomeTheaterFacade(val lights: List<Light>, val stereo: Stereo) {
  fun watchMovie() {
    println("Preparing for movie night...")
    lights.forEach { it.turnOff() }
    stereo.on()
    stereo.setVolume(11) // Adjust volume as needed
  }

  fun endMovie() {
    println("Ending movie night...")
    lights.forEach { it.turnOn() }
    stereo.off()
  }
}

fun main() {
  val livingRoomLight = Light("Living Room")
  val kitchenLight = Light("Kitchen")
  val homeTheater = HomeTheaterFacade(listOf(livingRoomLight, kitchenLight), Stereo())

  homeTheater.watchMovie()
  homeTheater.endMovie()
}

```
##### **Java**

```java

import java.util.*;

class Light
{
  private final String location;

  public Light (String location)
  {
	this.location = location;
  }

  public void turnOn ()
  {
	System.out.println (location + " light is on");
  }

  public void turnOff ()
  {
	System.out.println (location + " light is off");
  }
}

class Stereo
{
  private int volume;

  public void on ()
  {
	System.out.println ("Stereo is on");
  }

  public void off ()
  {
	System.out.println ("Stereo is off");
  }

  public void setVolume (int volume)
  {
	this.volume = volume;
	System.out.println ("Stereo volume set to " + volume);
  }
}

class HomeTheaterFacade
{
  private final List < Light > lights;
  private final Stereo stereo;

  public HomeTheaterFacade (List < Light > lights, Stereo stereo)
  {
	this.lights = lights;
	this.stereo = stereo;
  }

  public void watchMovie ()
  {
	System.out.println ("Preparing for movie night...");
  for (Light light:lights)
	  {
		light.turnOff ();
	  }
	stereo.on ();
	stereo.setVolume (11);		// Adjust volume as needed
  }

  public void endMovie ()
  {
	System.out.println ("Ending movie night...");
  for (Light light:lights)
	  {
		light.turnOn ();
	  }
	stereo.off ();
  }
}

class Main
{
  public static void main (String[]args)
  {
	List < Light > lights =
	  Arrays.asList (new Light ("Living Room"), new Light ("Kitchen"));
	Stereo stereo = new Stereo ();
	HomeTheaterFacade homeTheater = new HomeTheaterFacade (lights, stereo);

	  homeTheater.watchMovie ();
	  homeTheater.endMovie ();

  }
}

```

---

### **Flyweight**

#### **Layman's Explanation**

The Flyweight pattern is like a shared library for commonly used items. Imagine you're playing a video game where there are many trees in a forest. Instead of creating a completely new tree object for each tree, the game uses a shared set of tree characteristics (like texture and shape) and only stores the unique information (like position) for each tree. This saves memory and makes the game run faster.

#### **Professional Explanation**

The Flyweight pattern is a structural design pattern that aims to minimize memory usage by sharing as much data as possible with similar objects. It separates the intrinsic state (shared) from the extrinsic state (unique) of an object. The intrinsic state is stored in flyweight objects and can be shared, while the extrinsic state is stored or computed by client objects and passed to the flyweight when needed.

This pattern is particularly useful when:

1. An application uses a large number of objects.
2. Storage costs are high because of the quantity of objects.
3. Most object state can be made extrinsic.
4. Many groups of objects may be replaced by relatively few shared objects once extrinsic state is removed.
5. The application doesn't depend on object identity.

Now, let's look at simple code examples in Python, Kotlin, and Java. We'll use a coffee shop menu as our example, where coffee flavours are flyweights.

#### **Code Examples**

##### **Python**

```python

class CoffeeFlavor:
    def __init__(self, name):
        self.name = name

class CoffeeFlavorFactory:
    flavors = {}

    @staticmethod
    def get_flavor(name):
        if name not in CoffeeFlavorFactory.flavors:
            CoffeeFlavorFactory.flavors[name] = CoffeeFlavor(name)
        return CoffeeFlavorFactory.flavors[name]

class CoffeeOrder:
    def __init__(self, table_number, flavor):
        self.table_number = table_number
        self.flavor = flavor

# Usage
factory = CoffeeFlavorFactory()
orders = [
    CoffeeOrder(1, factory.get_flavor("Cappuccino")),
    CoffeeOrder(2, factory.get_flavor("Espresso")),
    CoffeeOrder(1, factory.get_flavor("Cappuccino")),
    CoffeeOrder(3, factory.get_flavor("Latte")),
]

print(f"Number of flavor objects: {len(factory.flavors)}")

```

##### **Kotlin**

```kotlin

class CoffeeFlavor(val name: String)

object CoffeeFlavorFactory {
    private val flavors = mutableMapOf<String, CoffeeFlavor>()

    fun getFlavor(name: String): CoffeeFlavor {
        return flavors.getOrPut(name) { CoffeeFlavor(name) }
    }
}

data class CoffeeOrder(val tableNumber: Int, val flavor: CoffeeFlavor)

// Usage
fun main() {
    val orders = listOf(
        CoffeeOrder(1, CoffeeFlavorFactory.getFlavor("Cappuccino")),
        CoffeeOrder(2, CoffeeFlavorFactory.getFlavor("Espresso")),
        CoffeeOrder(1, CoffeeFlavorFactory.getFlavor("Cappuccino")),
        CoffeeOrder(3, CoffeeFlavorFactory.getFlavor("Latte"))
    )

    println("Number of flavor objects: ${CoffeeFlavorFactory.getFlavor("").javaClass.declaredFields.size}")
}

```

##### **Java**

```java

import java.util.HashMap;
import java.util.Map;

class CoffeeFlavor {
    private final String name;

    CoffeeFlavor(String name) {
        this.name = name;
    }

    public String getName() {
        return name;
    }
}

class CoffeeFlavorFactory {
    private Map<String, CoffeeFlavor> flavors = new HashMap<>();

    public CoffeeFlavor getFlavor(String name) {
        return flavors.computeIfAbsent(name, CoffeeFlavor::new);
    }
}

class CoffeeOrder {
    private final int tableNumber;
    private final CoffeeFlavor flavor;

    CoffeeOrder(int tableNumber, CoffeeFlavor flavor) {
        this.tableNumber = tableNumber;
        this.flavor = flavor;
    }
}

public class Main {
    public static void main(String[] args) {
        CoffeeFlavorFactory factory = new CoffeeFlavorFactory();
        CoffeeOrder[] orders = {
            new CoffeeOrder(1, factory.getFlavor("Cappuccino")),
            new CoffeeOrder(2, factory.getFlavor("Espresso")),
            new CoffeeOrder(1, factory.getFlavor("Cappuccino")),
            new CoffeeOrder(3, factory.getFlavor("Latte"))
        };

        System.out.println("Number of flavor objects: " + factory.getFlavor("").getClass().getDeclaredFields().length);
    }
}

```

---

### **Proxy**

#### **Layman Explanation**

Imagine you want to buy a concert ticket, but you don’t want to deal with the hassle of finding and purchasing the ticket yourself. Instead, you hire an agent (a proxy) who buys the ticket for you. The agent handles all the complicated details and only gives you the ticket when it's ready. This way, you get what you need without any hassle, thanks to the proxy.

#### **Professional Explanation**

The Proxy design pattern is a structural design pattern that provides a surrogate or placeholder for another object to control access to it. This pattern allows you to:

- **Add an extra layer of control:** The proxy can intercept requests to the real object, performing security checks, logging actions, or managing access based on permissions.
- **Optimize performance:** The proxy can cache results from the real object, reducing the need for repeated expensive operations.
- **Lazy initialization:** The proxy can delay creating the real object until it's actually needed, saving memory and resources.
- **Encapsulation:** The proxy can hide the complexity of the real object's interface, simplifying client code.

#### **Code Examples**

##### **Python**

```python

from abc import ABC, abstractmethod

class Subject(ABC):
    @abstractmethod
    def request(self):
        pass

class RealSubject(Subject):
    def request(self):
        print("RealSubject: Handling request.")

class Proxy(Subject):
    def __init__(self, real_subject: RealSubject):
        self._real_subject = real_subject

    def request(self):
        if self.check_access():
            self._real_subject.request()
            self.log_access()

    def check_access(self) -> bool:
        print("Proxy: Checking access prior to firing a real request.")
        return True

    def log_access(self):
        print("Proxy: Logging the time of request.")

# Usage
real_subject = RealSubject()
proxy = Proxy(real_subject)
proxy.request()

```

##### **Kotlin**

```kotlin

interface Subject {
    fun request()
}

class RealSubject : Subject {
    override fun request() {
        println("RealSubject: Handling request.")
    }
}

class Proxy(private val realSubject: RealSubject) : Subject {
    override fun request() {
        if (checkAccess()) {
            realSubject.request()
            logAccess()
        }
    }

    private fun checkAccess(): Boolean {
        println("Proxy: Checking access prior to firing a real request.")
        return true
    }

    private fun logAccess() {
        println("Proxy: Logging the time of request.")
    }
}

// Usage
fun main() {
    val realSubject = RealSubject()
    val proxy = Proxy(realSubject)
    proxy.request()
}

```

##### **Java**

```java

interface Subject {
    void request();
}

class RealSubject implements Subject {
    public void request() {
        System.out.println("RealSubject: Handling request.");
    }
}

class Proxy implements Subject {
    private RealSubject realSubject;

    public Proxy(RealSubject realSubject) {
        this.realSubject = realSubject;
    }

    public void request() {
        if (checkAccess()) {
            realSubject.request();
            logAccess();
        }
    }

    private boolean checkAccess() {
        System.out.println("Proxy: Checking access prior to firing a real request.");
        return true;
    }

    private void logAccess() {
        System.out.println("Proxy: Logging the time of request.");
    }
}

// Usage
public class Main {
    public static void main(String[] args) {
        RealSubject realSubject = new RealSubject();
        Proxy proxy = new Proxy(realSubject);
        proxy.request();
    }
}

```