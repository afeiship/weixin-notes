# 001-login-out-auth-invalide

### 设备
- Windows10 
- 微信版本： 2.6.8.65 (当前最新版)

### 测试内容：
1. 用户在登录之后，把信息存在 localStorage/Cookie 中
2. 用户把微信退出(关机或者主动退出)
3. 发现用户的 Cookie/localStorage 信息均被销毁
直接关掉网页，再打开：local/cookie 均会被保存
退出微信再登录，打开网页：local/cookie 均会被清除
任务管理器Kill微信，再登录，打开网页：local/cookie 均会被清除

<img width="400" src="http://ww3.sinaimg.cn/large/006tNc79ly1g64tnd8zvqj30a403m3yd.jpg" />


| 存储方式                             | localStorage | cookie |
| ------------------------------------ | ------------ | ------ |
| 直接关掉网页，再打开                 | true         | true   |
| 退出微信再登录，打开网页             | null         | null   |
| 任务管理器Kill微信，再登录，打开网页 | null         | null   |




### 设备
- MacOs
- 微信版本：Version 2.3.25 (12481)

直接关掉网页，再打开：Cookie被清除，LocalStorage 保留
Cdm +Q  Kill微信，再登录，打开网页：Cookie被清除，LocalStorage 保留

| 存储方式                             | localStorage | cookie |
| ------------------------------------ | ------------ | ------ |
| 直接关掉网页，再打开                 | true         | null   |
| 任务管理器Kill微信，再登录，打开网页 | true         | null   |




### 设备
- IOS 12.4
- 目前最新微信版本
- 测试的是：微信里的h5网页
清除缓存：会清除 Cookie 而会保留 localStorage；
退出微信：会将 Cookie/LocalStorage 同时清除掉

| 存储方式                 | localStorage | cookie |
| ------------------------ | ------------ | ------ |
| 直接关掉网页，再打开     | true         | null   |
| 退出微信再登录，打开网页 | null         | null   |



### 设备
- Android
- 目前最新版微信

直接关掉网页，再打开：保留 local/cookie
清除缓存：这个会删除所有的信息，暂时不测试
退出微信，再登录: local/cookie 均会被清除

| 存储方式                 | localStorage | cookie |
| ------------------------ | ------------ | ------ |
| 直接关掉网页，再打开     | true         | true   |
| 退出微信再登录，打开网页 | null         | null   |


## 结论
- localstorage/cookie 在特定场景下，都会被清除
- 但 localStorage 会相对更好
- 当 localStorage 被清除的时候， Cookie 也一定被清除了


## resources
- https://www.cnblogs.com/flyfly/p/4739565.html
- https://segmentfault.com/q/1010000016524408/a-1020000016526519
