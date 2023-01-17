# joshua-boot-maven-archetype

Spring Boot 2 多模块的 maven 脚手架/模板，可快速初始化工程代码

## 生成模块

- dto 用于存放数据传输对象
- client 用于给其他项目提供二方包
- service 用于存放业务代码
- start 用于存放 Web 接口

## 集成依赖

| 依赖           | 版本号           | 说明  |
--------------|---------------|-----
spring boot | 2.3.4.RELEASE |  |
fastjson | 1.2.73        |  |
commons-lang3 | 3.11          |  |
commons-collections4 | 4.4           |  |
guava | 29.0-jre      |  |
mybatis | 3.55          |  |
fluent-mybatis | 1.8.3         |  |
lombok | 1.8.12        |  |

## 使用前准备

- [Maven](https://maven.apache.org/) (构建/发布当前项目)
- Java 8 ([Download](https://adoptopenjdk.net/releases.html?variant=openjdk8))

## 构建/安装项目

使用以下命令:

`mvn clean install`

## 使用脚手架创建项目

使用以下命令(注意：替换名时要连同左右大括号一起替换):

```
mvn archetype:generate \
  -DinteractiveMode=false \
  -DarchetypeGroupId=com.mogudiandian \
  -DarchetypeArtifactId=joshua-boot-maven-archetype \
  -DarchetypeVersion=0.0.1-SNAPSHOT \
  -DgroupId={这里换成自己需要的groupId(com.company.business)} \
  -DartifactId={这里换成自己的项目名(project-name)} \
  -Dversion={这里换成自己的项目版本号(x.y.z)} \
  -Dpackage={这里换成自己的项目包名(com.company.business.project)}
```

## 发布项目

修改 `pom.xml` 的 `distributionManagement` 节点，替换为自己在 `settings.xml` 中 配置的 `server`

举例：

`settings.xml`

```xml
<servers>
  <server>
    <id>snapshots</id>
    <username>yyy</username>
    <password>yyy</password>
  </server>
  <server>
    <id>releases</id>
    <username>xxx</username>
    <password>xxx</password>
  </server>
</servers>
```
`pom.xml`

```xml
<distributionManagement>
    <snapshotRepository>
        <id>snapshots</id>
        <url>http://xxx/snapshots</url>
    </snapshotRepository>
    <repository>
        <id>releases</id>
      <url>http://xxx/releases</url>
    </repository>
</distributionManagement>
```
