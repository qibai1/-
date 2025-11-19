# Android Studio配置环境及镜像

## Android Studio配置环境

[Android Studio配置环境](https://blog.csdn.net/Y74364/article/details/96121530?spm=1001.2014.3001.5506)参考该链接进行

## Android Studio配置镜像

[Android Studio配置镜像](https://blog.csdn.net/m0_72158265/article/details/146478807?spm=1001.2014.3001.5506)参考该链接进行

1. 配置镜像地址：点击Android Studio界面左上角File->Settings->Appearance & Behavior->System Settings->HTTP Proxy，填写阿里云镜像地址：

```Kotlin
https://mirrors.aliyun.com/android.googlesource.com/
```

---

![](https://zcnokd8idi6c.feishu.cn/space/api/box/stream/download/asynccode/?code=NzMxNWY4NjQ4ZGRiZjA5ODYwZTg4NTk2ZTA3NWQ3OWFfNUVyTnNPWU9VQUcyNmdVUkZyb1hHVXlWTmEzZkREUlRfVG9rZW46TWRkemJFWHZBb083dkJ4VHF4cGNUMW1EbkdOXzE3NjM1NjQyMTc6MTc2MzU2NzgxN19WNA)

2. 修改gradle-wrapper.properties
   
   ```
   在项目路径中找到【  项目名】->gradle->wrapper->gradle-wrapper.properties文件，修改distributionUrl的值为镜像地址加原来的gradle版本号：
   ```

```Kotlin
#原默认地址
#distributionUrl=https\://services.gradle.org/distributions/gradle-8.11.1-bin.zip
 
#修改后地址
distributionUrl=https://mirrors.aliyun.com/macports/distfiles/gradle/gradle-8.13-all.zip
```

```Kotlin
#Tue Nov ​18​ ​00:46:05​ CST ​2025
distributionBase=GRADLE_USER_HOME
distributionPath=wrapper/dists
#distributionUrl=https\://services.gradle.org/distributions/gradle-8.13-bin.zip
distributionUrl=https://mirrors.aliyun.com/macports/distfiles/gradle/gradle-8.13-all.zip
networkTimeout=10000
validateDistributionUrl=true
zipStoreBase=GRADLE_USER_HOME
zipStorePath=wrapper/dists
```

3. 配置`settings.gradle.kts`

在项目根目录下找到`settings.gradle.kts文件，分别在`pluginManagement和dependencyResolutionManagement的repositories中进行如下[阿里云镜像](https://so.csdn.net/so/search?q=%E9%98%BF%E9%87%8C%E4%BA%91%E9%95%9C%E5%83%8F&spm=1001.2101.3001.7020)配置：

```Kotlin
pluginManagement {
    repositories {

        // 添加的阿里云镜像
        maven { url = uri("https://maven.aliyun.com/repository/google") }
        maven { url = uri("https://maven.aliyun.com/repository/central") }
        maven { url = uri("https://maven.aliyun.com/repository/spring") }
        maven { url = uri("https://mirrors.aliyun.com/gradle/") }
        maven { url = uri("https://mirrors.aliyun.com/macports/distfiles/gradle/") }
        maven { url = uri("https://maven.aliyun.com/nexus/content/groups/public/") }
        maven { url = uri("https://maven.aliyun.com/nexus/content/repositories/jcenter") }
        maven { url = uri("https://maven.aliyun.com/nexus/content/repositories/google") }
        maven { url = uri("https://maven.aliyun.com/nexus/content/repositories/gradle-plugin") }


        google {
            content {
                includeGroupByRegex("com\\.android.*")
                includeGroupByRegex("com\\.google.*")
                includeGroupByRegex("androidx.*")
            }
        }
        mavenCentral()
        gradlePluginPortal()
    }
}
dependencyResolutionManagement {
    repositoriesMode.set(RepositoriesMode.FAIL_ON_PROJECT_REPOS)
    repositories {


        // 添加的阿里云镜像
        maven { url = uri("https://maven.aliyun.com/repository/google") }
        maven { url = uri("https://maven.aliyun.com/repository/central") }
        maven { url = uri("https://maven.aliyun.com/repository/spring") }
        maven { url = uri("https://mirrors.aliyun.com/gradle/") }
        maven { url = uri("https://mirrors.aliyun.com/macports/distfiles/gradle/") }
        maven { url = uri("https://maven.aliyun.com/nexus/content/groups/public/") }
        maven { url = uri("https://maven.aliyun.com/nexus/content/repositories/jcenter") }
        maven { url = uri("https://maven.aliyun.com/nexus/content/repositories/google") }
        maven { url = uri("https://maven.aliyun.com/nexus/content/repositories/gradle-plugin") }


        google()
        mavenCentral()
    }
}

rootProject.name = "My Application"
include(":app")
```

4. 清除配置缓存重启项目

点击Android Studio界面左上角File->Invalidate Caches，选择重启选项后点击Invalidate and Restart，等待重启重新编译即可。

---

![](https://zcnokd8idi6c.feishu.cn/space/api/box/stream/download/asynccode/?code=ZDhmYmU3M2MyNTg2NmIxYzQ0Y2I3Y2Y4NTNiMDhhZjdfSTZxVmdDcElMYmIxSWxmS013VE11OUJIb2d3cGtPVjhfVG9rZW46VFY4N2JjdWltb3hmcFB4dVVJQ2N3OGlCbkRmXzE3NjM1NjQyMTc6MTc2MzU2NzgxN19WNA)

## 新建设备模拟器

[新建设备模拟器](https://blog.csdn.net/Y74364/article/details/96121530?spm=1001.2014.3001.5506)参考该链接进行

1. 点击该图标新建模拟器

---

![](https://zcnokd8idi6c.feishu.cn/space/api/box/stream/download/asynccode/?code=M2Y0ODI5ZjZiZjRhZDUzMWY5NTFiMjc5N2E3Y2E3NDBfWWJ4SzNwZmFGQkk2WmlMeWF6R2FPSmpETEdoekpMQU5fVG9rZW46V0RiemJvbTcybzFMcFZ4cHN5aGNKb2k4bjdjXzE3NjM1NjQyMTc6MTc2MzU2NzgxN19WNA)

2. 点击加号图标新建模拟器

---

![](https://zcnokd8idi6c.feishu.cn/space/api/box/stream/download/asynccode/?code=YmI5OWQ4OWMyYjAwZjIxYTlmNTAwZWJkMmE3NmExNDRfYlFqd0lDRXcxMVIwWWlpY0VQSFlHUDk5bndsV0NWNFpfVG9rZW46UEJzemI4WlVtb3I4Ulp4UnNqa2NDTk45bmJkXzE3NjM1NjQyMTc6MTc2MzU2NzgxN19WNA)

3. 选择创建虚拟设备

---

![](https://zcnokd8idi6c.feishu.cn/space/api/box/stream/download/asynccode/?code=MmNiNmRmMTg2OTQ0ZWY1ZWMwNjYwOWM4YzBjNjMxY2VfdzZFRjNKbWhQREE2dm9KMmN6UGIzMTl0bUdMcFdoNU1fVG9rZW46SFlDc2I1NFR6b1Zhcmx4MkpiaGN0cnkzbkZoXzE3NjM1NjQyMTc6MTc2MzU2NzgxN19WNA)

4. 选择设备后点击next

---

![](https://zcnokd8idi6c.feishu.cn/space/api/box/stream/download/asynccode/?code=ZjIyMjU5OTBhMDcwODkxMzkwOGJjZWY0OTUwM2RlMjFfT1lZcHhtM08xQVFXQnRuYUp5UmU1c0tzYzVTeFR6S05fVG9rZW46WUg4RGI3cmdNb2lyVkF4b01peGNtUXFlbmRiXzE3NjM1NjQyMTc6MTc2MzU2NzgxN19WNA)

5. 选择想要的系统及其版本版本，再点击Finish

---

**选择合适的版本**

![](https://zcnokd8idi6c.feishu.cn/space/api/box/stream/download/asynccode/?code=ZTIwYzFjZGZlZTkyYTc0NGI3MzY3MDE4ODUzOTY3NTVfR3NudldKMFQ1SmNZTkNEdDFOajVsN0RRTndqYlRiU2dfVG9rZW46UGFOa2JoR1Qyb1ZPSDZ4U3NTQWNUcXB5bjNiXzE3NjM1NjQyMTc6MTc2MzU2NzgxN19WNA)

6. 启动虚拟设备

---

![](https://zcnokd8idi6c.feishu.cn/space/api/box/stream/download/asynccode/?code=NjkzNmFkZTUzMGZkNDMyMTZiMTYxMjgyNDAwYzIwODNfZ040OVVWbXp5TExjSm51T3Z0Ull0VUNFeVNKUURZajJfVG9rZW46VmFGTGJBTHU2b0JjdFl4N2RTU2NreXNJbjBnXzE3NjM1NjQyMTc6MTc2MzU2NzgxN19WNA)

7. 成功运行

---

![](https://zcnokd8idi6c.feishu.cn/space/api/box/stream/download/asynccode/?code=NWYxYWViNGVmYjViZDRhZGIzNGI1YTQxMzVkMmE0MmJfT1dkdTFhMFZkektRcE53dHp5akY1N3lLYjVhUkRmUXNfVG9rZW46SEZEQWJVcHV1b0pDZmZ4WEFHSmNJdW9YbjhlXzE3NjM1NjQyMTc6MTc2MzU2NzgxN19WNA)

# Android Studio小demo实现

