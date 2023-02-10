# 1.session和cookie的生命周期？

- 一般都是**一次会话**期间
- **持久化存储**
  - Cookie的默认有效期是20分钟。默认情况下，Cookie存储在浏览器内存中，当浏览器关闭，内存释放，则Cookie被销毁（生命周期一次会话期间）。可以通过setMaxAge()持久化存储（使Cookie不随着浏览器关闭而被销毁）
  - Session默认30分钟（默认值是在Tomcat的web.xml配置文件中写死的），这个失效时间，是可以通过配置进行修改的在项目的web.xml中配置）
    - 钝化：在服务器正常关闭后，Tomcat会自动将Session数据写入硬盘的文件中（服务器重启后，session数据会被保存）
    - 活化：再次启动服务器后，从文件中加载数据到Session中

---

- Cookie的原理分析

  对于Cookie的实现原理是基于HTTP协议的,其中设计到HTTP协议中的两个请求头信息:

  * 响应头:set-cookie
  * 请求头: cookie

  ![1629393289338](Pic/1629393289338.png)

  * 对于AServlet响应数据的时候，Tomcat服务器都是基于HTTP协议来响应数据
  * 当Tomcat发现后端要返回的是一个Cookie对象之后，Tomcat就会在响应头中添加一行数据==`Set-Cookie:username=zs`==
  * 浏览器获取到响应结果后，从响应头中就可以获取到`Set-Cookie`对应值`username=zs`,并将数据存储在浏览器的内存中
  * 浏览器再次发送请求给BServlet的时候，浏览器会自动在请求头中添加==`Cookie: username=zs`==发送给服务端BServlet
  * Request对象会把请求头中cookie对应的值封装成一个个Cookie对象，最终形成一个数组
  * BServlet通过Request对象获取到Cookie[]后，就可以从中获取自己需要的数据

- Session是基于Cookie实现的，Session是如何保证在一次会话中获取的Session对象是同一个呢?

![1629430754825](Pic/1629430754825.png)

(1)demo1在第一次获取session对象的时候，session对象会有一个唯一的标识，假如是`id:10`

(2)demo1在session中存入其他数据并处理完成所有业务后，需要通过Tomcat服务器响应结果给浏览器

(3)Tomcat服务器发现业务处理中使用了session对象，就会把session的唯一标识`id:10`当做一个cookie，添加`Set-Cookie:JESSIONID=10`到响应头中，并响应给浏览器

(4)浏览器接收到响应结果后，会把响应头中的coookie数据存储到浏览器的内存中

(5)浏览器在同一会话中访问demo2的时候，会把cookie中的数据按照`cookie: JESSIONID=10`的格式添加到请求头中并发送给服务器Tomcat

(6)demo2获取到请求后，从请求头中就读取cookie中的JSESSIONID值为10，然后就会到服务器内存中寻找`id:10`的session对象，如果找到了，就直接返回该对象，如果没有则新创建一个session对象

(7)关闭打开浏览器后，因为浏览器的cookie已被销毁，所以就没有JESSIONID的数据，服务端获取到的session就是一个全新的session对象

# 2.lambda+Stream

```java
List<DishFlavor> flavors = dishDto.getFlavors();
flavors = flavors.stream().map((item) -> {
    item.setDishId(dishId);
    return item;
}).collect(Collectors.toList());
```

Stream 执行流程:
 * ① Stream的实例化

   ```java
   flavors.stream()
   
   java.util.Collection<E> @Contract(pure = true) 
   public java.util.stream.Stream<E> stream()
   Returns a sequential Stream with this collection as its source.
   ```

 * ② 一系列的中间操作（过滤、映射、...)

   ```java
   .map((item) -> {
       item.setDishId(dishId);
       return item;
   })
        
   映射：
   //map(Function f)——接收一个函数作为参数，将元素转换成其他形式或提取信息，该函数会被应用到每个元素上，并将其映射成一个新的元素。
   public abstract <R> Stream<R> map(java.util.function.Function<? super T, ? extends R> mapper)
   Returns a stream consisting of the results of applying the given function to the elements of this stream.
   ```

 * ③ 终止操作

   ```java
   .collect(Collectors.toList());
   
   收集：
   //collect(Collector c)——将流转换为其他形式。接收一个 Collector接口的实现，用于给Stream中元素做汇总的方法
   ```