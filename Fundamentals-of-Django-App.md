# Django app设计的原则

对于初学者来说，django app的定义不是那么让人容易理解和接受，在进入这个章节之前，有必要谈一些基本的定义

- A Django project Django开发组开发的一种web服务框架
- Django apps 可以理解为:app为一个个模块化的库，组成了一个大型的django项目。 通常一个django project由n多app组成。这些app可以由你自己来编写，也有很多第三方的库来实现
- INSTALLED_APPS 你编写的或者你download的第三方的app库，只有在INSTALLED_APPS中才会有用
- Third-party Django packages 第三方库，一般都是可以被复用的，作为工具穿插在project中


## 黄金法则

Django一个核心开发者 James Bennett， 他认为一个优秀的Django app设计，可以遵循:

> “The art of creating and maintaining a good Django app is that it should follow the
truncated Unix philosophy according to Douglas McIlroy: ‘Write programs that do one
thing and do it well.”’

一句话概述就是，一个app干就干一个事儿，干到极致

这句话概括下其实我就没啥写的，也就是说你要不搞的一个project就一个app，一个app包揽了全部的活儿，那么也可以，就是不好呗。就好像你一个工程就一个类，一个方法，里面各种岔道。
不好不好。


作者举例依然是一个冰激凌商店，一个叫"Two Scoops"的ice cream shop..

- flavors app 

 