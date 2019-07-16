# JSSDK 1.4.0、wx7.0.3网页分享时，Android分享部分不成功，iOS成功的现象

~~~
微信公众号开发里JSSDK 1.4.0分享接口无效
微信公众号开发 里JSSDK 1.4.0分享接口updateAppMessageShareData、updateTimelineShareData 安卓手机调用无效，IOS手机可以调用但没有回调函数，各位大神，这该怎么办，另外旧版分享接口什么时候报废？

谁有解决办法，或者微信技术的客服电话也行，（别沉啊）
~~~


## 小程序•小故事(17)——分享功能调整背后的故事
> 原创： snow，link 微信开发者 7月6日

有时候我们使用一个小程序会遇到以下情形：
我们打开一个小程序，就看见提示“分享到5个群，可以获得一张20元的优惠券”，吸引我们去无脑分享到不同的群里；
打开某个小游戏，提示我“一定要分享到xx个群，才能继续玩游戏”；
……


而我们在群里打开这类小程序，仍然是提示我分享的信息，这类功能无疑打断了我们对小程序/小游戏正常的功能使用。
我们收到了很多用户对这类小程序/小游戏的抱怨。这类分享并非是用户主动自发的，而是受到了某类利益的诱惑，或是被迫分享。这样的内容充斥在群里、小程序里，对用户造成了骚扰，是对分享功能的滥用。 


在原来的分享接口中，用户发起分享动作之后，可以通过 success 、fail、complete等回调来判断用户是否完成了最后的分享动作。通过这个能力，开发者是可以将产品交互在分享这个能力上做得比较自然和顺畅。但却被上述情形的小程序滥用。在我们权衡了分享功能带来的利弊后，我们打算回收这个能力。

调整为：`我们将不再支持分享回调参数 success 、fail 、complete 。即开发者无法判断用户最终是否完成了分享动作，也无法获取到分享成功后的回调参数shareTicket` 。


## resources
- https://www.sunbeyond.com/3108
- https://blog.csdn.net/u012274155/article/details/90716828
- https://developers.weixin.qq.com/community/develop/doc/0004449a2902d0fe1867fa73056c00