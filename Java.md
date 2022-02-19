**一个.java里面只能有一个public的class且名字必须与.java的文件名一样** 

## 运算符
### &与&&的区别
1、如果&&只有左边为true时，才会执行右边的  
2、&当左右不为boolean时也表示按位与

## 条件
### switch
```java
switch(a){
  case value1:
       //do something
       break;
  default:
        //do something
        break;
}
```

这里的a应该是int（比int范围小的比如byte short可以隐形转换）  高版本jdk1.7后的string类型也可以  

## 主数据类型
### 1、小类型不能装大类型（如要需要强制转换）
### 2、char类型可以储存中文（因为char储存的时unicode编码）

## 静态(static)
- 静态变量
重点：两个字“共享”，可直接用类名调用
- 静态方法  
重点：不被实例变量影响，可直接用类名调用  

## 抽象(abstract)
- 抽象类  
重点：与具体类唯二的区别  1、不能被new 2、具体类不能有抽象方法   （必须被extend）
- 抽象方法  
重点：抽象方法无实体，必须在子类中实现
```java
public abstract void eat();  //后面无方法体
```

### 抽象类与接口区别

