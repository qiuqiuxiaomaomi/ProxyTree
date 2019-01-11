# ProxyTree
静态代理，动态代理技术研究

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

<pre>
静态代理：

      
</pre>