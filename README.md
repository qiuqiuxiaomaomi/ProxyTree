# ProxyTree
静态代理，动态代理技术研究

java的动态代理机制详解
https://www.cnblogs.com/xiaoluo501395377/p/3383130.html

![](https://i.imgur.com/L6WIuSZ.png)

![](https://i.imgur.com/RyOE6vM.png)

![](https://i.imgur.com/ZQurV7K.png)

![](https://i.imgur.com/aSsPtPf.png)

<pre> 
动态技术原理：

      在Java的动态代理机制中，有两个重要的类或接口，一个是InvocationHandler(接口)，
      Proxy(类)，这一个类和接口是实现动态代理所必须用到的。

      每一个动态代理类都必须要实现InvocationHandler这个接口，并且每个代理类的实例都关联到
      了一个handler，当我们通过代理对象调用一个方法的时候，这个方法的调用就会被转发为由
      InvocationHandler这个接口的 invoke 方法来进行调用

      Object invoke(Object proxy, Method method, Object[] args) throws Throwable
             proxy:指代所代理的那个真实对象。
             method:指代所要调用的真实对象的某个方法的Method对象。
             args:指代调用真实对象某个方法时接受的参数。

      Proxy的 newProxyInstance方法：
           这个方法的作用就是得到一个动态的代理对像。

      public static Object newProxyInstance(ClassLoader loader, Class<?>[]
             interfaces, InvocationHandler h) throws IllegalArgumentException

             loader:一个ClassLoader对象，定义了由哪个ClassLoader对象来对生成的代理对象
                    进行加载。
             interfaces:一个Interface对象的数组，表示将要给我需要代理的对象提供一组什么
                    接口，如果我们提供了一组接口给它，那么这个代理对象就宣称实现了该接口
                    ，这样我们就能调用这组接口中的方法了。
             h:一个InvocationHandler对象，标识当前我这个动态代理对象在调用方法的时候，
               会关联到哪一个InvocationHandler对象。
</pre>

![](https://i.imgur.com/2x3MI0J.png)

<pre>
静态代理：

      优点：可以做到不对目标对象进行修改的前提下，对目标对象进行功能的扩展和拦截。
      缺点：因为代理对象，需要实现与目标对象一样的接口，会导致代理类十分繁多，不易维护，同
           时一旦接口增加方法，则目标对象和代理类都需要维护。
</pre>

![](https://i.imgur.com/kbSukAO.png)

![](https://i.imgur.com/RUATn9h.png)

<pre>
JDK动态代理：

      JDK动态代理是由Java内部的反射机制来实现的，需要实现类通过接口定义业务方法，利用JDK
      的API动态的在内存中构建代理对象。

      实现InvocationHandler接口，重写public Object invoke(Object proxy, Method method, Object[] args)方法。

      使用Proxy的static Object newProxyInstance(ClassLoader loader, Class<?>[] 
      interfaces,InvocationHandler h )方法实现代理。ClassLoader loader指定当前目标对
      象使用类加载器；Class<?>[] interfaces是目标对象实现的接口的类型；
      InvocationHandler h是事件处理，执行目标对象的方法时,会触发事件处理器的方法，会把当
      前执行目标对象的方法作为参数传入。

      总结：代理对象不需要实现接口，但是目标对象一定要实现接口，否则不能用动态代理。
</pre>

![](https://i.imgur.com/E9RNLgX.png)

![](https://i.imgur.com/u7aC2SJ.png)

<pre>
CGLIB动态代理：

      静态代理和JDK动态代理都要求目标对象是实现一个接口的目标对象，但是有时候目标对象只是
      一个单独的对象，并没有实现任何的接口，这个时候就可以使用目标对象子类的方式实现代理。
      CGLIB是针对类来实现代理的，它的原理是对指定的目标类生成一个子类，并覆盖其中方法实现
      增强，因为采用的是继承，所以不能对final修饰的类进行代理。
</pre>