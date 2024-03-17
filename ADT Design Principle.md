#Java #OO 
___
#  Exposed Methods
一个我们设计的类，或者说ADT（Abstract Data Type），
其对外部开放的方法包括四类（MIT 6.031），其功能与设计规范可被归纳为：
t means other args
T means target ADT
- creator : t* → T
- producer : T+, t* → T
- observer : T+, t* → t
- mutator : T+, t* → void | t | T

在ADT方法设计层面，存在一个重要的理念：就是类本身的方法不要做过度复杂的操作，而是提供非常简单的方法功能即可，让用户将简单的原子方法进行组织来实现复杂功能

因此，在进行原子方法的设计时，只需要遵循提及的四类最基本的原子方法设计规范即可，对于方法组合实现复杂功能交给外部；当然也可以提供少量已经封装好的二级/复杂方法（由类内部调用原子方法实现）

## demo
from BUAA-2024-OOP-Unit1
```java
public class Lexer{
	// Observer
	public Token get() {
	}
	
	// Mutator
	public void next() {
	}
	
	public Token getAndNext() {  
	    Token token = this.get();  
	    this.next();  
	    return token;  
	}
}
```

# Core idea: Immutable 
> MIT 6.031:
>  **immutable types are safer from bugs, easier to understand, and more ready for change**

使用mutable的危险主要在以下两个场景，会产生*alias*：
1. Passing mutable values as params
2. Return mutable variable

在ADT的设计时，为了保证满足我们代码工程的易于维护、可理解性、debug的便利，一定尽量将ADT设计为Immutable的。这一点并不是说要让每个类的对象必然不可变化，如果这样我们完全没必要设计mutator方法，这极大牺牲了程序的可扩展性

设计一个Immutable ADT应该：
1. 尽量使用不可变的变量与数据类型，如String而非StringBuilder
2. 应该尽量保证在方法调用与参数传递过程中，只传递不可变对象，或者保证方法不会修改可变对象；只保留以及暴露给外部部分的参数，这也是封装思想的一种体现。

## When we use mutable variable?
Immutable并不意味着mutable变量完全不可用，使用不可变只是为了让我们的程序在跨类、跨层次、跨方法的交互中更加安全，但是这一点是在牺牲了性能后实现的

我们的代码中其实也常常使用如HashMap，ArrayList，StringBuilder等对象

它们的使用原则其实可以总结如下：
1. 当mutable仅仅使用在方法内部，其生存期仅在某个方法内部
2. 当mutable被很好的**封装**，创建的对象仅会存在于类的内部且仅仅能在类的内部被修改

