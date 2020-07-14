## [spring boot 使用spring-data-jpa让数据访问更简单、更优雅](https://github.com/timebusker/spring-boot/tree/master/spring-boot-10-SpringData/)  

![image](https://github.com/timebusker/spring-boot/raw/master/static/10/spring-data-jpa.png?raw=true)  

- ### 关于spring-data-jpa  
   + 在实际开发过程中，对数据库的操作无非就“增删改查”。就最为普遍的单表操作而言，除了表和字段不同外，语句都是类似的，开发人员需要写大量类似而枯燥的语句来完成业务逻辑。  
   + 为了解决这些大量枯燥的数据操作语句，我们第一个想到的是使用ORM框架，比如：Hibernate。通过整合Hibernate之后，我们以操作Java实体的方式最终将数据改变映射到数据库表中。  
   + 为了解决抽象各个Java实体基本的“增删改查”操作，我们通常会以泛型的方式封装一个模板Dao来进行抽象简化，但是这样依然不是很方便，我们需要针对每个实体编写一个继承自泛型模板Dao的接口，再编写该接口的实现。虽然一些基础的数据访问已经可以得到很好的复用，但是在代码结构上针对每个实体都会有一堆Dao的接口和实现。  
   + 由于模板Dao的实现，使得这些具体实体的Dao层已经变的非常“薄”，有一些具体实体的Dao实现可能完全就是对模板Dao的简单代理，并且往往这样的实现类可能会出现在很多实体上。Spring-data-jpa的出现正可以让这样一个已经很“薄”的数据访问层变成只是一层接口的编写方式。  

- ### spring-data-jpa常用注解
   + [**@Entity**]() ： 指明该类是一个实体Bean，可以通过jpa与数据库表建立映射关系，每个成员代表数据库字段名称，实体Bean的每个实例代表数据表中的一行数据  
   + [**@Table**]() : 为被@Entity注释的类所要映射带数据库表，其中@Table.name()用来指定映射表的表名。如果缺省@Table注释，系统默认采用类名作为映射表的表名  
   + [**@Id**]() ： 指定表的主键属性
   + [**@GeneratedValue**]() ： 定义了标识字段生成规则，详细内容参考[ @GeneratedValue 用法](http://blog.csdn.net/fancylovejava/article/details/7438660)
   + [**@Entity**]()
   + [**@Entity**]()
   + [**@Entity**]()
   + [**@Entity**]()
   + [**@Entity**]()
   + [**@Entity**]()
   + [**@Entity**]()
 
- ### JPA实体关系映射
   实体关系是指实体与实体之间的关系，从方向上分为单向关联和双向关联，从实体数量上分为一对一、一对多、多对多等。对于任何两个实体，都要从这两个方面区分它们之间的关系。  
   单向关联是一个实体中引用了另外一个实体，也即通过一个实体可以获取另一个实体对象的引用；双向关联是两个实体之间可以相互获取对方对象的引用。  
   + #### 一对一  
     学生和身份证是一对一的关系，下面将从单向关联和双向关联来分析。
     * 单向关联
       假设在学生实体中可以获取身份证对象的引用；反之，不能在身份证实体中获取学生对象的引用，则学生和身份证是一对一的单向关联关系，关系映射如下:    
       **注：**[@OneToOne]()只能确定实体与实体的关系是一对一的关系，不能指定数据库表中的保存的关联字段，所以要结合[@JoinColumn]()来指定关联字段。
       在默认情况下，关联实体（IDCard）的主键一般是用来做外键的。但如果此时不想将关联实体的主键作为外键，而是将其他字段作为关联字段（外键可以关联到其他表的主键上，也可以关联到其他表的非空字段上），此时需要设置@JoinColumn的referencedColumnName属性。
     * 双向关联
     * 主键关联  
       既让两个实体对象具有相同的主键值，以表明它们之间的一一对应的关系；而数据库不会有额外的字段来维护它们之间的关系，仅仅通过表的主键来关联，主键的值需要程序来显示维护，映射如下
     
   + #### 一对多
   + #### 多对多
   + 