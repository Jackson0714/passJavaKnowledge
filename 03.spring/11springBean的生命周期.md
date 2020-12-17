# spring bean的 生命周期

class-> beanDefinition->
 --> 推断构造方法->
 new Bean()->依赖注入属性(注入\循环依赖) 
 -> aware -> 初始化方法(前,中,后)->context
