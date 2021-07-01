# activateOculusQuest2
this is a tutorial for activating Oculus Quest2 without a router.(不使用路由器激活Oculus Quest 2)

实验室买了个Oculus quest 2，卖家和我说他可以帮我激活，但是，作为计算机的学生，怎么还需要他来帮，结果，自己造的孽还得自己来受。以下就是我成功连上外网的过程：

 1. 一个用于fq的服务器地址，没有的话就得买个vpn了
 2. 带无线网卡的电脑
 3. 下载Outline用于翻墙，需要注意，它填写的服务器地址要求：ss://access-key，而我们一般都是一个订阅地址，那么，就可以从那个订阅地址，下载文件，打开，例如我下载了个json文件，里面包含了所有的节点信息：

![server parameters](/images/json.png)

而outline的access key的规则是：ss://method:password@hostname:port
直接对照着规则填好，hostname就是server，port就是server_port，还有一点，method:password这里需要用BASE64编码，也很简单，转一下，Base64 在线编码解码。然后添加服务器就ok了：

![server parameters](/images/outline.png)

到这里测试一下可不可以访问facebook，我遇到的问题是，google可以用，youtube、twitter都可以用，就是facebook不能用，解决方法是，改host文件，地址在C:\Windows\System32\drivers\etc，直接找到facebook对应的section，删掉就好了。（我提前备份了，万一之后有问题再弄回来）

至此，你的电脑可以访问外网。

4. 下载connectify hotspot，用于创建热点。，用于创建热点。win10虽然可以开热点，但是，我试了，开的热点并不能让你访问外网。创建一个个人热点 , 要共享的Internet选成outline client的接口，比如，你开的outline是这样的：

![server parameters](/images/tap0.png)
上图打开方法为设置->网络和Internet->更改适配器选项

那么，再connectify里，就选择

![server parameters](/images/connectify.png)

现在，你用手机连一下这个热点，试试能不能访问facebook，很坑的一点，我在手机上，用Chrome浏览器访问不了facebook，而用safari就可以！

5. 把你的oculus quest2 连上网，至此，联网的问题搞定。


激活后，如果只是想在Oculus的浏览器里看视频网页啥的，那么可以通过配置代理实现，而不需要如以上这样专门开热点，具体方法为：
win10，打开移动热点，Oculus连接该热点，填写好密码后，首先点击高级选项，里面有个host name，填写上你当前电脑所用网络的IPv4地址，还有端口地址填写你翻墙软件使用的端口，如clash是7890，之后点击连接，Oculus就可以访问网页了。