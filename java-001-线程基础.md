---


---

<h1 id="线程安全">线程安全</h1>
<h2 id="基础含义">基础含义</h2>
<blockquote>
<p>当多个线程访问同一个类【对象或者方法】的时候，这个类始终都能表现出正确的行为，则这个类是线程安全的。<br>
java中可以使用  synchronized 进行加锁生成 互斥区【临界区】<br>
一个线程想要执行 synchronized方法，首先尝试拿到锁，如果拿到锁，执行修饰区域的代码内容；如果拿不到，则会一直尝试去获取锁；多个线程竞争这把锁。</p>
</blockquote>
<h2 id="多个线程多个锁">多个线程多个锁</h2>
<blockquote>
<p>多个线程，每个线程都可以拿到自己指定的锁，分别获得锁之后，执行synchronized方法体的内容。<br>
synchronized 一般为对象级锁<br>
静态方法添加synchronized时，使用的为类锁</p>
</blockquote>
<h2 id="同步">同步</h2>
<pre><code>- 由于共享产生的同步
</code></pre>
<h2 id="异步">异步</h2>
<h2 id="脏读">脏读</h2>
<h3 id="数据不一致性">数据不一致性</h3>
<ul>
<li>
<p>考虑业务整体性，避免脏读的出现，使用synchronized对set以及get方法</p>
</li>
<li>
<p>acid数据库特性-ACID，指数据库事务正确执行的四个基本要素的缩写。包含：原子性（Atomicity）、一致性（Consistency）、隔离性（Isolation）、持久性（Durability）</p>
</li>
<li>
<p>synchronized 可重入:一个线程中获取到对象的锁中，再次请求此对象的时候可以再次获取对象锁</p>
<blockquote>
<p>当线程请求一个由其它线程持有的对象锁时，该线程会阻塞，而当线程请求由自己持有的对象锁时，如果该锁是重入锁,请求就会成功,否则阻塞。</p>
</blockquote>
<blockquote>
<p>java中获取锁的操作的粒度是“线程”，而不是“调用”，即不是每一次调用都是建立一个锁。</p>
</blockquote>
<blockquote>
<p>重入锁的一种实现方法是为每个锁关联一个线程持有者和计数器，当计数器为0时表示该锁没有被任何线程持有，那么任何线程都可能获得该锁而调用相应的方法；当某一线程请求成功后，JVM会记下锁的持有线程，并且将计数器置为1；此时其它线程请求该锁，则必须等待；而如果同一个线程再次请求这个锁，就可以再次拿到这个锁，同时计数器会递增；当线程退出同步代码块时，计数器会递减，如果计数器为0，则释放该锁</p>
</blockquote>
</li>
</ul>
<h2 id="synchronized-其他">synchronized 其他</h2>
<h3 id="对象锁、类锁">对象锁、类锁</h3>
<h3 id="尽量不要对string常量加锁">尽量不要对string常量加锁</h3>
<h3 id="在synchronized中不要对对象锁进行修改">在synchronized中不要对对象锁进行修改</h3>
<h1 id="volatile">volatile</h1>
<h2 id="含义">含义</h2>
<blockquote>
<p>使得变量在多个线程之间均可见，并不具备原子性，可以使用atomic类的系列对象<br>
性能比syncgronized强很多，但是不会造成阻塞，并不具有同步性<br>
原始实现方式：使用对像或者方法加锁<br>
jdk1.5之后，对于每一个线程均存在一个独立的内存空间，将主线程中的对象引用拷贝到自己的独立的内存空间。<br>
使用volatile注释之后，线程强制线程执行引擎到主内存中读取数据</p>
</blockquote>

