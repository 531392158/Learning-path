## 如何理解 AOP 和 DI
### AOP 控制反转
AOP 是一种设计里面，交由第三方来管理和控制对象
设想一下，在往常我们的代码学习中，如果类 A 要生成一个 B 类的对象，那么最初始的方法就应该是

`A Aobject = new B()`

但是如果说我们的项目足够大的时候，有一千个类都需要生成 B 对象，这个时候我们因为某种原因需要把所有的 B 对象全部换成新的更好的 C 对象，那么就需要在源代码中进行一千次修改，其次修改之后代码还需要进行重新编译，这样对我们的项目开发是不好的。

如果我们使用了 spring，在程序运行的过程中动态创建对象，A类只需要使用 bean id 通过 getbean 方法获取到一个aop容器，这个容器具体指代哪个类， A 类是不知道的，那么我们就可以在配置文件中设置这个 bean id 所对应的类，那么再出现上述那种情况的时候，我们只需要在 xml 文件里面修改 bean id 对应的 class 路径就可以了

`A Aobject = applicationContext.getBean("beanIDforB")`
`<bean id="beanIDforB" class="com.Spring.Service.ClassB">`

