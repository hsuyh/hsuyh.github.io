---
layout: post
title: 安裝maven 在 Raspberry pi 3
---

最近想要安裝物聯網平台OM2M在Raspberry pi上，
OM2M官網上面所提供的eclipse無法直接在Raspberry pi 上去使用，
所以我必須以command line 方式來編譯om2m，
在編譯之前我必須安裝Maven在Raspberry pi上。

### 安裝Maven

1. 到[Maven官網](http://maven.apache.org/download.cgi)下載 binary tar.gz archive。 我這邊是下載3.3.9版本。
2. 將Maven 解壓縮到/opt裡

```c
$ cd /opt
$ sudo tar -xzvf /home/pi/Downloads/apache-maven-3.3.9-bin.tar.gz     //我是下載到Downloads資料夾，所以這邊路徑為Download資料夾路徑下
```

3.必須告訴你的系統shell去哪裡讀取Maven

```c
$ sudoedit /etc/profile.d/maven.sh
```

4.接著輸入

```
export M2_HOME=/opt/apache-maven-3.3.9
export PATH=$PATH:$M2_HOME/bin
```

5.之後登出後，再登入並輸入

```c
$ mvn -version
```

看到以下內容即表示成功安裝！

```
Apache Maven 3.3.9 (bb52d8502b132ec0a5a3f4c09453c07478323dc5; 2015-11-11T00:41:47+08:00)
Maven home: /opt/apache-maven-3.3.9
Java version: 1.8.0_65, vendor: Oracle Corporation
Java home: /usr/lib/jvm/jdk-8-oracle-arm32-vfp-hflt/jre
Default locale: en_US, platform encoding: ANSI_X3.4-1968
OS name: "linux", version: "4.4.11-v7+", arch: "arm", family: "unix"
```
