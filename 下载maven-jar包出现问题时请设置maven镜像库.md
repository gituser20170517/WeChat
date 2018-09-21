推荐使用国内的镜像库，
1 .aliyun
修改maven配置文件setting.xml，替换原有mirrors部分，或添加相应内容：
```
  <mirrors>
    <mirror>
      <id>aliyun</id>
      <name>aliyun</name>
      <url>http://maven.aliyun.com/nexus/content/groups/public/</url>
      <mirrorOf>central</mirrorOf>
    </mirror>
  </mirrors>
```
2. 163

```
<mirror>
    <id>nexus-163</id>
    <mirrorOf>*</mirrorOf>
    <name>Nexus 163</name>
    <url>http://mirrors.163.com/maven/repository/maven-public/</url>
</mirror>
```

更多信息可以查看http://mirrors.163.com/.help/maven.html