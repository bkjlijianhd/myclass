
什么是cookie文件？它有什么用？存储在哪？
Kartyusha | 浏览 20789 次 问题未开放回答
推荐于2016-02-27 09:17:08
最佳答案

cookie是一种程序，当它放到硬盘后，就成为一个个扩展名为TXT的纯文本文件。
cookie的大小并不相同，有的是几十个字节，有的则是2K左右。cookie的内容用一般的文本编辑器都可以看到。但是，大多数cookie的内容看上去都是乱糟糟的，让人不知所云，但这 看起来乱糟糟的内容，却蕴藏着天机： 有的cookie中包含了上次访问的时间、信用卡信息等数据信息；还有的cookie甚至包含了Email地址和访问过的站点地址。
Cookie一般来说，其位置都是放置在C:\WINDOWS\cookie目录下面，只要打开这个目录就可以看到了。不过，也有些cookie并没有在这个目录下面。这些cookie就只能通过搜索系统 的注册表来查找了。
当第一次登录到某个站点时，远端服务器就会传过来一个cookie，里面包含一个随机产生的字符序列，称为用户ID，用来唯一标识用户，当然这个用户就是了。与此同时，服务器 也把这个用户ID记录到自己的数据库中，每当这个被标识过的用户在站点上进行操作，譬如在各个连接之间跳转，或是下载了某些东西，在哪里哪里逗留了多久等，这些有关的操作信息就会 被记录到数据库中。当这个用户再一次登录该站点时，只要他上一次访问时收到的cookie还存在，浏览器就会把相应cookie中的信息上传给远端的服务器，服务器便能依据cookie中的信息查 到数据库中相应的记录，然后对将要下传的数据进行处理之后再传到远方用户的电脑中，浏览器再把这些数据显示给用户





Session:在计算机中，尤其是在网络应用中，称为“会话控制”。Session 对象存储特定用户会话所需的属性及配置信息。这样，当用户在应用程序的 Web 页之间跳转时，存储在 Session 对象中的变量将不会丢失，而是在整个用户会话中一直存在下去。当用户请求来自应用程序的 Web 页时，如果该用户还没有会话，则 Web 服务器将自动创建一个 Session 对象。当会话过期或被放弃后，服务器将终止该会话。Session 对象最常见的一个用法就是存储用户的首选项。


session和cookie的区别
1. 由于HTTP协议是无状态的协议，所以服务端需要记录用户的状态时，就需要用某种机制来识具体的用户，这个机制就是Session.典型的场景比如购物车，当你点击下单按钮时，由于HTTP协议无状态，所以并不知道是哪个用户操作的，所以服务端要为特定的用户创建了特定的Session，用用于标识这个用户，并且跟踪用户，这样才知道购物车里面有几本书。这个Session是保存在服务端的，有一个唯一标识。在服务端保存Session的方法很多，内存、数据库、文件都有。集群的时候也要考虑Session的转移，在大型的网站，一般会有专门的Session服务器集群，用来保存用户会话，这个时候 Session 信息都是放在内存的，使用一些缓存服务比如Memcached之类的来放 Session。2. 思考一下服务端如何识别特定的客户？这个时候Cookie就登场了。每次HTTP请求的时候，客户端都会发送相应的Cookie信息到服务端。实际上大多数的应用都是用 Cookie 来实现Session跟踪的，第一次创建Session的时候，服务端会在HTTP协议中告诉客户端，需要在 Cookie 里面记录一个Session ID，以后每次请求把这个会话ID发送到服务器，我就知道你是谁了。有人问，如果客户端的浏览器禁用了 Cookie 怎么办？一般这种情况下，会使用一种叫做URL重写的技术来进行会话跟踪，即每次HTTP交互，URL后面都会被附加上一个诸如 sid=xxxxx 这样的参数，服务端据此来识别用户。3. Cookie其实还可以用在一些方便用户的场景下，设想你某次登陆过一个网站，下次登录的时候不想再次输入账号了，怎么办？这个信息可以写到Cookie里面，访问网站的时候，网站页面的脚本可以读取这个信息，就自动帮你把用户名给填了，能够方便一下用户。这也是Cookie名称的由来，给用户的一点甜头。所以，总结一下：Session是在服务端保存的一个数据结构，用来跟踪用户的状态，这个数据可以保存在集群、数据库、文件中；Cookie是客户端保存用户信息的一种机制，用来记录用户的一些信息，也是实现Session的一种方式。
