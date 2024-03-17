#Java #OO 
___
# Template
```java
/**
 * Method Type
 * effect: (Overall)
 * req: (Overall)
 * @param args, req:(pre-condition)
 * @return discription, req:(post-condition)
 */
 public int tem(int args){
 }
```

# demo
```java
/**  
 * Observer 
 * effect: iter all coef in HashMap, and return a big mutual coef 
 * req: call this method Only when poly.size() >= 2
 * @param args, (req)
 * @return gcd of all coef, (req)  
 */
 public BigInteger calGcd() {
 }
```

# Details
## Method Type
沿用MIT6.031中四类方法定义，遵守其对应协议(见ADT Design Principle)：
- Creator,  Crt
- Producer, Prod
- Observer, Obs
- Mutator,  Mut

## Effect
一个对于方法效果的描述，需要注意的是细致程度，不涉及算法的具体实现，但是要对不同情况返回值说明确清楚（覆盖所有情况），需要做到：**当specs写好时，可以完全地认为该方法已经被实现。**
学习Java Docs的写法
demo
```java
/**  
 * Observer
 * effect: check curPoly's type to be simplified
 * -1 ERROR 
 * 0 -- single factor 
 * 1 -- coef * x ^ num || coef * exp()  (coef > 0) 
 * 2 -- the only way to shorten is use gcd 
 * @return if cur can be express as a factor
 */
 public int checkPolyType() {
 }
```

## Req(Overall)
有时某些方法的调用时需要某些与kwargs无关的pre-condition，这个时候就需要使用全局的req，在demo部分已经展示了一个

## @params args: (req)
这里需要给出一些参数的信息：
- 参数的含义描述
- pre-condition：这个参数的值需要满足的要求（值域/有序性/...）
- 基于Immutable理念：除非对于传入参数特殊说明，否则不应对其实现更改

> MIT6.031
> If the _effects_ do not explicitly say that an input can be mutated, then mutation of the input is implicitly disallowed.

## @return: (req)
这里需要给出关于返回值的信息：
- 返回值的含义描述
- post-condition：返回值需要满足的要求（值域/有序性/...）
