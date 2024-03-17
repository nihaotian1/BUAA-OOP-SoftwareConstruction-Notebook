#Java #OO
___
# Split Mission
肢解任务为多个子任务，使用这一方法可以很好地：
1. 降低耦合程度
2. 降低复杂度

# Test-first Programming
对于一个类、方法的设计：
1. 先写specification，只要specs写好了，就假定这个方法已经被实现好了
2. 根据specs设计好测试样例UnitTest
3. 书写完所有的specs后，再去完成具体的实现

# Smooth Debugging
设置部分调试相关的全局变量，在config中设置Mode.class
在代码中对于Debug信息，使用以下模式：
```java
if (Mode.DEBUG) {
	System.out.println("ERROR; Demo.class, line 13; Wrong input Type");
}
```