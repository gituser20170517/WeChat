
更多代码，请参考单元测试类：`me.chanjar.weixin.mp.api.impl.WxMpQrCodeServiceImplTest`

--------------------------------------------------------------------------------------------------

## 获得二维码ticket
```java
// 临时ticket
WxMpQrCodeTicket ticket = wxMpService.getQrcodeService().qrCodeCreateTmpTicket(scene, expire_seconds);
// 永久ticket
WxMpQrCodeTicket ticket = wxMpService.getQrcodeService().qrCodeCreateLastTicket(scene);
```

## 换取二维码图片
```java
WxMpQrCodeTicket ticket = ...;
// 获得在系统临时目录下的文件，需要自己保存使用，注意：临时文件夹下存放的文件不可靠，不要直接使用
File file = wxMpService.getQrcodeService().qrCodePicture(ticket);
```
