# 简单工厂模式
> 简单工厂模式是由一个工厂对象决定创建出哪一种产品类的实例，它是工厂模式家族中最简单实用的模式，可以理解为是不同工厂模式的一个特殊实现。 

### 角色及职责
- **工厂角色** ：简单工厂模式的核心，它负责实现创建所有实例的内部逻辑。工厂类可以被外界直接调用，创建所需的产品对象。
- **抽象产品** ：简单工厂模式所创建的所有对象的父类，它负责描述所有实例所共有的公共接口。
- **具体产品** ：是简单工厂模式的创建目标，所有创建的对象都是充当这个角色的某个具体类的实例。
 
### 谜语生成器
> 实现一个猜哺乳动物名称的谜语生成器，每个谜语包含feature方法和eat方法。
 
``` php
<?php  
/** 
 * SimpleFactory
 * User: Mayer
 * Date: 2016/7/25
 * Time: 15:37
 */  
  
/**
 * 抽象角色(哺乳动物)
 * Interface Mammal  抽象接口 
 */  
interface Mammal {
    /**
     * feature
     * @return mixed 
     */  
    function feature();
  
    /**
     * eat
     * @return mixed 
     */  
    function eat();
}  
  
/**
 * 具体角色 
 * Class Cat  猫(哺乳动物的一种)
 */
class Cat implements Mammal {
    private $number;
  
    function __construct($number = 1) {
        $this->number=$number; 
    }  
  
    function feature() {  
        echo "您好，我是哺乳动物，我每小时能跑百公里，抓到的老鼠能绕地球三圈！\n";
    }  
  
    function eat() {  
        echo "您好，我是哺乳动物，我一分钟能吃掉十只老鼠！\n";
    }  
}  
  
/**
 * 具体角色 
 * Class Dog  狗(哺乳动物的一种)
 */
class Dog implements Mammal {
    private $number;
  
    function __construct($number = 2) {
        $this->number=$number;
    }
  
    function feature() {
        echo "您好，我是哺乳动物，我每小时能跑百公里，盗贼搭了飞机也能追上！\n";
    }
  
    function eat() {
        echo "您好，我是哺乳动物，每天要吃三十斤狗粮！\n";
    }
}
  
/**
 * 具体角色 
 * Class Cow  牛(哺乳动物的一种)
 */
class Cow implements Mammal {
    private $number;
  
    function __construct($number = 3) {
        $this->number=$number;
    }
  
    function feature() {
        echo "您好，我是哺乳动物，我每小时能耕十亩地，而且还累不死！\n";
    }
  
    function eat() {
        echo "您好，我是哺乳动物，每天要吃二十斤青草！\n";
    }
}

/**
 * 工厂角色(谜语生成器)
 * Class RiddleFactory
 */  
class RiddleFactory {
    static function GetRiddle($number) {
        if($number===1) {
            return new Cat;
        }
        if($number===2) {
            return new Dog;
        }
        if($number===3) {
            return new Cow;
        } 
        else {
            return null;
        }
    }  
}

// 测试代码
$number = mt_rand(1,3);
$raddle = RiddleFactory::GetRiddle($number);
$raddle->feature();
$raddle->eat();

?>
```
> 简单工厂的优点：让对象的调用者和对象创建过程分离，当对象调用者需要对象时，直接向工厂请求即可。从而避免了对象的调用者与对象的实现类以硬编码方式耦合，以提高系统的可维护性、可扩展性。简单工厂的缺点：当产品修改时，工厂类也要做相应的修改，违背了开放-封闭原则。
