Android Studio配置环境及镜像
Android Studio配置环境
Android Studio配置环境参考该链接进行
Android Studio配置镜像
Android Studio配置镜像参考该链接进行
1. 配置镜像地址：点击Android Studio界面左上角File->Settings->Appearance & Behavior->System Settings->HTTP Proxy，填写阿里云镜像地址：
https://mirrors.aliyun.com/android.googlesource.com/

---
[图片]
2. 修改gradle-wrapper.properties
        在项目路径中找到【  项目名】->gradle->wrapper->gradle-wrapper.properties文件，修改distributionUrl的值为镜像地址加原来的gradle版本号：
#原默认地址
#distributionUrl=https\://services.gradle.org/distributions/gradle-8.11.1-bin.zip
 
#修改后地址
distributionUrl=https://mirrors.aliyun.com/macports/distfiles/gradle/gradle-8.13-all.zip
#Tue Nov 18 00:46:05 CST 2025
distributionBase=GRADLE_USER_HOME
distributionPath=wrapper/dists
#distributionUrl=https\://services.gradle.org/distributions/gradle-8.13-bin.zip
distributionUrl=https://mirrors.aliyun.com/macports/distfiles/gradle/gradle-8.13-all.zip
networkTimeout=10000
validateDistributionUrl=true
zipStoreBase=GRADLE_USER_HOME
zipStorePath=wrapper/dists
3. 配置settings.gradle.kts
在项目根目录下找到settings.gradle.kts文件，分别在pluginManagement和dependencyResolutionManagement的repositories中进行如下阿里云镜像配置：
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
4. 清除配置缓存重启项目
点击Android Studio界面左上角File->Invalidate Caches，选择重启选项后点击Invalidate and Restart，等待重启重新编译即可。

---
[图片]
新建设备模拟器
新建设备模拟器参考该链接进行
1. 点击该图标新建模拟器

---
[图片]
2. 点击加号图标新建模拟器

---
[图片]
3. 选择创建虚拟设备

---
[图片]
4. 选择设备后点击next

---
[图片]
5. 选择想要的系统及其版本版本，再点击Finish

---
选择合适的版本
[图片]
6. 启动虚拟设备

---
[图片]
7. 成功运行

---
[图片]
Android Studio小demo实现
