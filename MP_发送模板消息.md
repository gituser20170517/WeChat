```java
WxMpTemplateMessage templateMessage = WxMpTemplateMessage.builder()
.toUser(...)
.templateId(...)
.url(...)
.build();

templateMessage.addData(new WxMpTemplateData(name1, value1, color2));
templateMessage.addData(new WxMpTemplateData(name2, value2, color2));

wxMpService.getTemplateMsgService().sendTemplateMsg(templateMessage);
```
更详细的使用方法请参考单元测试代码：
`/weixin-java-mp/src/test/java/me/chanjar/weixin/mp/api/impl/WxMpTemplateMsgServiceImplTest.java`

或者参考在线的javadoc：
https://binarywang.github.io/weixin-java-mp-javadoc/me/chanjar/weixin/mp/api/impl/WxMpTemplateMsgServiceImpl.html