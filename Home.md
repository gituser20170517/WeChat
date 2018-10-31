# 微信Java SDK开发文档

## 分模块开发文档
1. [微信公众号开发文档（包含网页授权登录相关接口）](https://github.com/Wechat-Group/weixin-java-tools/wiki/%E5%85%AC%E4%BC%97%E5%8F%B7%E5%BC%80%E5%8F%91%E6%96%87%E6%A1%A3)
1. [微信企业号/企业微信开发文档](https://github.com/Wechat-Group/weixin-java-tools/wiki/%E4%BC%81%E4%B8%9A%E5%8F%B7%E5%BC%80%E5%8F%91%E6%96%87%E6%A1%A3)
1. [微信支付开发文档](https://github.com/Wechat-Group/weixin-java-tools/wiki/%E5%BE%AE%E4%BF%A1%E6%94%AF%E4%BB%98%E5%BC%80%E5%8F%91%E6%96%87%E6%A1%A3)
1. [微信开放平台开发文档](https://github.com/Wechat-Group/weixin-java-tools/wiki/%E5%BE%AE%E4%BF%A1%E5%BC%80%E6%94%BE%E5%B9%B3%E5%8F%B0%E5%BC%80%E5%8F%91%E6%96%87%E6%A1%A3)
1. [微信小程序开发文档](https://github.com/Wechat-Group/weixin-java-tools/wiki/%E5%B0%8F%E7%A8%8B%E5%BA%8F%E5%BC%80%E5%8F%91%E6%96%87%E6%A1%A3)

## 常见异常问题的解决办法

1. [加解密时出现`Illegal key size`异常的处理办法](https://github.com/Wechat-Group/weixin-java-tools/wiki/加解密的异常处理办法)
1. [发生`java.security.KeyException`的解决办法](https://github.com/Wechat-Group/weixin-java-tools/wiki/java.security.KeyException)
1. [出现`NoClassDefFoundError`、`NoSuchFieldError`、`NoSuchMethdError`或`ClassNotFoundException`的解决办法](https://github.com/Wechat-Group/weixin-java-tools/wiki/NoClassDefFoundError%E3%80%81NoSuchMethdError%E6%88%96ClassNotFoundException%E7%9A%84%E8%A7%A3%E5%86%B3%E5%8A%9E%E6%B3%95)

## 其他常见问题
1. **在微信后台设置安全域名时，注意不要将http等字符带入，首先要理解域名的含义，应该是`www.abcde.com`类似这样的**
1. [WxConsts常用常量定义](https://binarywang.github.io/weixin-java-common-javadoc/me/chanjar/weixin/common/api/WxConsts.html)
1. [Http框架的选用说明](https://github.com/Wechat-Group/weixin-java-tools/wiki/http%E6%A1%86%E6%9E%B6%E7%9A%84%E9%80%89%E7%94%A8%E8%AF%B4%E6%98%8E)
1. [HttpClient参数配置（寻找超时等相关参数设置方法的，请点击进入）](https://github.com/Wechat-Group/weixin-java-tools/wiki/HttpClient相关参数的设置方法)
1. [对Maven不熟的，建议学习此视频](http://www.imooc.com/learn/443)
1. [几个内网端口映射（穿透）服务网站(可以实现将内网服务暴露给外网访问)](https://github.com/Wechat-Group/weixin-java-tools/wiki/%E5%87%A0%E4%B8%AA%E5%86%85%E7%BD%91%E7%AB%AF%E5%8F%A3%E6%98%A0%E5%B0%84%E6%9C%8D%E5%8A%A1%E7%BD%91%E7%AB%99)
1. [下载maven jar包出现问题时请设置maven镜像库](https://github.com/Wechat-Group/weixin-java-tools/wiki/%E4%B8%8B%E8%BD%BDmaven-jar%E5%8C%85%E5%87%BA%E7%8E%B0%E9%97%AE%E9%A2%98%E6%97%B6%E8%AF%B7%E8%AE%BE%E7%BD%AEmaven%E9%95%9C%E5%83%8F%E5%BA%93)
1. [Emoji表情字符存储有问题，或者遇到保存字符串到数据库里出现`\xF0\x9F\x92\x94`类似问题时，请尝试使用这个工具，或者自行修改数据库存储编码为utf8mb4](https://github.com/binarywang/java-emoji-converter)
1. [httpclient 4.3.1 版本有bug，请不要使用](https://github.com/Wechat-Group/weixin-java-tools/wiki/httpclient-4.3.1-%E7%89%88%E6%9C%AC%E6%9C%89bug-%E8%AF%B7%E4%B8%8D%E8%A6%81%E4%BD%BF%E7%94%A8)
1. [Session](https://github.com/Wechat-Group/weixin-java-tools/wiki/WxSession)
1. [配置日志](https://github.com/Wechat-Group/weixin-java-tools/wiki/配置日志)
1. [消息排重](https://github.com/Wechat-Group/weixin-java-tools/wiki/消息排重)
