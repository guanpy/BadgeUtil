# BadgeUtil
Android 不同Launcher添加桌面角标Util
## 需求分析
原生Android系统不具备添加桌面角标功能，所以很多厂家效仿ios都自己定义了该功能，
这个功能和手机品牌没有直接的关系，而是和手机当前使用的launcher有直接关系。比如三星的手机我安装Asus桌面，这时候我们就不能适配三星launcher而要去适配华硕launcher。
## 在开发中问题总结
这次角标功能需求主要针对一些大的厂家launcher做适配，fork [BadgeUtil](https://github.com/lixiangers/BadgeUtil)角标设置开源库，自己做了一些适配性修改，下面是launcher的适配情况
### 主要测试launcher
* **华为：** Emui4.1开始支持第三方app角标[华为桌面角标介绍](http://developer.huawei.com/cn/consumer/wiki/index.php?title=%E5%8D%8E%E4%B8%BA%E6%A1%8C%E9%9D%A2%E8%A7%92%E6%A0%87%E4%BB%8B%E7%BB%8D)，但是开放范围有限，只对较大型的纯即时通讯类应用（例：聊天工具、邮箱）和大型企业的内部办公应用开放，暂时无法支持

* **小米：** miui6以上开始支持第三方app角标[小米桌面角标介绍](http://dev.xiaomi.com/doc/p=3904/index.html)，有两个注意点：
  * 小米中count 并不是所有notification的总和。二是要传入当前notificationId 对应的count（就是**不能直接设置角标总量**，是通过每次发送通知+这条通知角标量，然后miui系统这个应用所有通知角标量后得出的总量）
  * 实际测试中发现apk第一次安装时，发送通知，角标会正常显示；再次进入发送通知，不会显示角标，这个问题网上发现普遍存在，暂时没找到解决方案
* **三星：** 测试通过
### 其他launcher（结论为网上得到）
 * nova launcher 的免费版本是没有桌面角标的功能,nova launcher prime版本才有(需要收费且国内各大应用市场没有提供下载)。
 * apex launcher 也是需要收费。
 * adw launcher 是免费的功能正常，但是ui太难看。
 * asus launcher 是免费的功能正常，但是发现如果连续发送未读消息，角标显示有延迟。
 * htc launcher 没有机器没测试
 * sony launcher 没有机器没有测试
 * LG launcher 没有机器没有测试
 * meizu 目前不支持(在Flyme4.5测试微信)
 * 联想 VIBE ui目前不支持(在VIBE UIV3.1测试微信)
 * 锤子 launcher 目前不支持第三方app的角标(但是微信有，应该是给单独适配了微信)
 * oppo等其他手机没有测试


