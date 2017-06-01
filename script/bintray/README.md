# 使用指南
Bintray申请部分就不说了，网上一堆，只是新版多了个组织和仓库步骤，申请后其他按照脚本配置快速搞定一切。
另外该网站较慢，所以一定要耐心。[传送门](https://bintray.com)

## 1.工程添加插件（根目录的build.gradle）
```
//maven 打包
classpath 'com.github.dcendents:android-maven-gradle-plugin:1.4.1'
//bintray 上传
classpath 'com.jfrog.bintray.gradle:gradle-bintray-plugin:1.7'
```

## 2.配置参数 (工程根目录的gradle.properties)
```
ROJ_ORG= //项目组织 （新版bintay需要在某个组织下，并创建一个仓库）
PROJ_REPO=  //项目仓库名
PROJ_GROUP= //groupid
PROJ_ARTIFACTID= //包名（最终提供给用户的）
PROJ_VERSION= //版本号
PROJ_NAME= //项目名（显示给别人看的，javadoc等）
PROJ_DESCRIPTION= //项目描述
PROJ_WEBSITEURL= //项目地址
PROJ_VCSURL= //项目版本库地址
DEVELOPER_ID= //开发者Id
DEVELOPER_NAME= //开发者名称
DEVELOPER_EMAIL= //开发者邮箱
```

## 3.添加本地隐藏参数（工程目录的local.properties）
```
//bintray用户名
bintray.user=
//bintray APIKEY
bintray.apikey=
```
## 4.在需要生成库的module library中应用插件
```
//下载放到根目录
apply from: project.rootDir.absolutePath+File.separator+'bintray.gradle'
```
或者
```
//直接在线使用（打包上传前避免网络检测可以先注释掉，打包时再放开）
apply from: 'https://raw.githubusercontent.com/CodingService/codingservice.github.io/master/script/bintray/bintray.gradle';
```
