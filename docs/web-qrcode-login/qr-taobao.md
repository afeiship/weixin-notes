# taobao-qrcode-login
> Web 扫码登录.

## steps:
1. 首先拿到二维码的字符串 URL： https://login.m.taobao.com/qrcodeCheck.htm?lgToken=e20115f0e33f373f6be958ca54a60b56&tbScanOpenType=Notification
    - 这关键的就是lgToken，这是网页的一个唯一ID
    - tbScanOpenType=Notification 其它参数就按这个来
2. 另外，开启一个轮轮询接口：当打开了二维码登录后，我们通过chrome控制台看网路请求，会发现： 
    - 网页在轮询调用接口：https://qrlogin.taobao.com/qrcodelogin/qrcodeLoginCheck.do?lgToken=e20115f0e33f373f6be958ca54a60b56&defaulturl=&_ksTS=1530178881213_61&callback=jsonp62，即拿上面二维码里的lgToken去请求服务
    - lgToken=e20115f0e33f373f6be958ca54a60b56 这个就是上一步取得的结果 

3. 扫码的几种情况：

    3.1 如果没有扫码，返回的是：
    ```json
    {
        "code": "10000",
        "message": "login start state",
        "success": true
    }
    ```
    3.2 如果扫了码，但是手机上没点击“确认登录”的话，界面显示的是：
    - <img width="300" src="https://ws1.sinaimg.cn/large/006tNc79ly1fzhein3re7j30a50aht95.jpg" />
    - 轮询接口返回的是
    ```json
    {
        "code": "10001",
        "message": "mobile scan QRCode success",
        "success": true
    }
    ```

    3.3 如果长时间未扫码，网页端会停止轮询，并显示： 
    - <img width="300" src="https://ws3.sinaimg.cn/large/006tNc79ly1fzheltkq5jj30a90a4aaj.jpg"/>

    3.4 当手机端确认登录后，接口返回的是
    - 返回结果如下：
    ```json
    {
        "code": "10006",
        "success": true,
        "url": "https://login.taobao.com/member/loginByIm.do?uid=cntaobaoxxx&token=ff82fc0d1d395a33d3b38ec5a4981336&time=1530179143250&asker=qrcodelogin&ask_version=1.0.0&defaulturl=https://www.taobao.com&webpas=0b7aed2d43f01825183e4a49c6cae47d1479929926"
    }
    ```
