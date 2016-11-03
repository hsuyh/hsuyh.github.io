---
layout: post
title: Maven 筆記
---

## Maven簡介
他是一種project management的工具，可以使用慣例pattern來建立project架構，可以幫助你對java做自動化編譯。

##POM
pom.xml 是Maven project configuration的核心，它可以說是一個樣板，你可以在這裡填上build project的資訊，Maven就會依照這個檔案來幫你編譯

* project: top-level element in pom.xml
* modelversion: POM 使用的版本
* groupId: 建立這個project的組織的unique ID，通常會是組織的FQDN
* artifactId: 代表 這個project 產生的artifact的unique base name
* packaging: the package type to be used by this artifact(JAR, WAR...) 預設為JAR
* version: artifact的版本
* name: project的display name
* description: project的基本敘述
* parent: 表明你的parent project的資訊，所謂的parent project就是你是在這個parent project之下的sub-project
* modules: 在parent project你就必須詳述你的subproject在modules element下
* prerequisites: 描述project的必要條件
* build: 會描述需要什麼資訊來build這個project。 這裡看[詳細](https://goo.gl/NvdP8B)



這裡看更多的[project description](https://maven.apache.org/components/ref/3.3.9/maven-model/maven.html)


## POM 常用指令

```c
mvn compile
```

編譯成功的class會被放到 ${basedir}/target/classes，這是Maven一個慣例，你不需要跟Maven說你需要的資源在哪裡、指定你的結果要在哪裡產生。

  ${basedir} 通常是指pom.xml所在的地方


``````
mvn package
```
根據packaging 這個element看是要製造成怎樣的格式，預設為製造jar


```c
mvn install
```
安裝artifact（也就是你產生的jar）在你自己的repository

```
mvn clean
```
他會刪掉target下面被建立的東西
```
mvn eclipse:eclipse
```
把妳的Maven專案 轉成eclipse可以import的格式
