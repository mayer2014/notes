# 工厂模式
> 工厂方法模式核心工厂类不再负责所有产品的创建，而是将具体创建的工作交给子类去做，成为一个抽象工厂角色，仅负责给出具体工厂类必须实现的接口。

### 角色及职责
- **抽象工厂** ：是工厂方法模式的核心，任何在模式中创建的对象的工厂类必须实现这个接口。
- **工厂角色** ：这是实现抽象工厂接口的具体工厂类，包含与应用程序密切相关的逻辑，并且受到应用程序调用以创建产品对象。
- **抽象产品** ：简单工厂模式所创建的所有对象的父类，它负责描述所有实例所共有的公共接口。
- **具体产品** ：是简单工厂模式的创建目标，所有创建的对象都是充当这个角色的某个具体类的实例。
 
### 谜语生成器
> 实现一个猜哺乳动物名称的谜语生成器，每个谜语包含feature方法和eat方法。
 
``` php
<?php  
/** 
 * Factory
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
    public function feature();
  
    /**
     * eat
     * @return mixed 
     */  
    public function eat();
}  
  
/**
 * 具体角色 
 * Class Cat  猫(哺乳动物的一种)
 */
class Cat implements Mammal {
    private $number;
  
    public function __construct($number = 1) {
        $this->number=$number; 
    }  

    /**
     * 输出动物特征
     */
    public function feature() {  
        echo "您好，我是哺乳动物，我每小时能跑百公里，抓到的老鼠能绕地球三圈！\n";
    }  

    /**
     * 输出动物吃相
     */
    public function eat() {  
        echo "您好，我是哺乳动物，我一分钟能吃掉十只老鼠！\n";
    }  
}  
  
/**
 * 具体角色 
 * Class Dog  狗(哺乳动物的一种)
 */
class Dog implements Mammal {
    private $number;
  
    public function __construct($number = 2) {
        $this->number=$number;
    }
  
    /**
     * 输出动物特征
     */
    public function feature() {
        echo "您好，我是哺乳动物，我每小时能跑百公里，盗贼搭了飞机也能追上！\n";
    }

    /**
     * 输出动物吃相
     */
    public function eat() {
        echo "您好，我是哺乳动物，每天要吃三十斤狗粮！\n";
    }
}
  
/**
 * 具体角色 
 * Class Cow  牛(哺乳动物的一种)
 */
class Cow implements Mammal {
    private $number;
  
    public function __construct($number = 3) {
        $this->number=$number;
    }

    /**
     * 输出动物特征
     */
    public function feature() {
        echo "您好，我是哺乳动物，我每小时能耕十亩地，而且还累不死！\n";
    }

    /**
     * 输出动物吃相
     */
    public function eat() {
        echo "您好，我是哺乳动物，每天要吃二十斤青草！\n";
    }
}

/**
 * 抽象工厂(定义接口)
 * Interface RiddleFactory
 */  
interface RiddleFactory {
    static public function GetRiddle();
}

/**
 * 具体工厂(实现不同接口)
 * Class CatRiddleFactory
 */
class CatRiddleFactory implements RiddleFactory {
    static public function GetRiddle() {
        return new Cat;
    }
}

/**
 * 具体工厂(实现不同接口)
 * Class DogRiddleFactory
 */
class DogRiddleFactory implements RiddleFactory {
    static public function GetRiddle() {
        return new Dog;
    }
}

/**
 * 具体工厂(实现不同接口)
 * Class CowRiddleFactory
 */
class CowRiddleFactory implements RiddleFactory {
    static function GetRiddle() {
        return new Cow;
    }
}

// 测试代码
$catRiddleFactory = CatRiddleFactory::GetRiddle();
$dogRiddleFactory = DogRiddleFactory::GetRiddle();
$cowRiddleFactory = CowRiddleFactory::GetRiddle();
$catRiddleFactory->feature();
$dogRiddleFactory->feature();
$cowRiddleFactory->feature();

?>
```
> 
- **工厂模式的优点**：克服了简单工厂模式违背开放-封闭的原则，保持了封装对象创建过程的优点。
- **工厂模式的缺点**：当增加产品时，就得增加一个产品工厂的类，增加额外的开发量。避免不了分支判断的问题。
