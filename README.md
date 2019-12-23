# Mirai
[![Codacy Badge](https://api.codacy.com/project/badge/Grade/7d0ec3ea244b424f93a6f59038a9deeb)](https://www.codacy.com/manual/Him188/mirai?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=mamoe/mirai&amp;utm_campaign=Badge_Grade)
[![Gitter](https://badges.gitter.im/mamoe/mirai.svg)](https://gitter.im/mamoe/mirai?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge)
[![Actions Status](https://github.com/mamoe/mirai/workflows/CI/badge.svg)](https://github.com/mamoe/mirai/actions)
[![Download](https://api.bintray.com/packages/him188moe/mirai/mirai-core/images/download.svg)](https://bintray.com/him188moe/mirai/mirai-core/)  
**[English](README-eng.md)**  

**TIM PC 协议** 跨平台 QQ 协议支持库.  
部分协议来自网络上开源项目  
**一切开发旨在学习，请勿用于非法用途**

您可在 Gitter 提问, 或加入 QQ 群: 655057127

## Update log
在 [Project](https://github.com/mamoe/mirai/projects/1) 查看已支持功能和计划  
在 [UpdateLog](https://github.com/mamoe/mirai/blob/master/UpdateLog.md) 查看版本更新记录

## Thank you!
您的 star 是对我们最大的鼓励(点击项目右上角);  
若要关注版本更新, 请点击 star 旁边的 watch

## Use as a library
把 Mirai 作为库内置于您的项目中使用.  
Mirai 只上传在 `jcenter`, 因此请确保在 `build.gradle` 添加 `jcenter()` 仓库  
```kotlin
repositories{
  jcenter()
}
```
若您需要使用在跨平台项目, 您需要对各个目标平台添加不同的依赖.  
若您只需要使用在单一平台, 则只需要添加一项该平台的依赖.  

您需要将 `VERSION` 替换为最新的版本(如 `0.5.1`): [![Download](https://api.bintray.com/packages/him188moe/mirai/mirai-core/images/download.svg)](https://bintray.com/him188moe/mirai/mirai-core/)  
Mirai 目前还处于实验性阶段, 建议您时刻保持最新版本.

现在 Mirai 只支持 TIM PC 协议.  
**common**
```kotlin
implementation("net.mamoe:mirai-core-timpc-common:VERSION")
```
**jvm**
```kotlin
implementation("net.mamoe:mirai-core-timpc-jvm:VERSION")
```
**android**
```kotlin
implementation("net.mamoe:mirai-core-timpc-android:VERSION")
```

## Try

### On JVM or Android
现在您可以开始体验低付出高效率的 Mirai

```kotlin
val bot = TIMPC.Bot(qqId, password).alsoLogin()
bot.subscribeMessages {
  "你好" reply "你好!"
  "profile" reply { sender.queryProfile() }
  contains("图片"){ File(imagePath).send() }
}
bot.subscribeAlways<MemberPermissionChangedEvent> {
  if (it.kind == BECOME_OPERATOR)
    reply("${it.member.id} 成为了管理员")
}
```

1. Clone
2. Import as Gradle project
3. 运行 Demo 程序: [mirai-demo](#mirai-demo) 示例和演示程序

**转到[开发文档](#Development-Guide---Kotlin)**

## Contribution

我们欢迎一切形式的贡献. 若您有兴趣为 Mirai 实现 JS, iOS, Native 平台, 请联系我(`Him188@mamoe.net`).  
若在使用过程中有任何疑问, 可提交 issue 或是邮件联系. 我们希望 Mirai 变得更易用.

## Build Requirements

- Kotlin 1.3.61  
- JDK 8
- Android SDK 29

### Using Java 
Q: 是否能只使用 Java 而不使用 Kotlin 来调用 Mirai?  
A: 正在适配中.  
   Mirai 大量使用协程, 内联, 扩展等 Kotlin 专有特性. 在 Java 调用这些 API 将会非常吃力. 
   我们正在为 Java 调用提供转接。

#### Libraries used
Mirai 使用以下开源库:
- [kotlin-stdlib](https://github.com/JetBrains/kotlin)
- [kotlinx-coroutines](https://github.com/Kotlin/kotlinx.coroutines)
- [kotlinx-io](https://github.com/Kotlin/kotlinx-io)
- [kotlin-reflect](https://github.com/JetBrains/kotlin)
- [pcap4j](https://github.com/kaitoy/pcap4j)
- [atomicfu](https://github.com/Kotlin/kotlinx.atomicfu)
- [ktor](https://github.com/ktorio/ktor)
- [tornadofx](https://github.com/edvin/tornadofx)
- [javafx](https://github.com/openjdk/jfx)
- [kotlinx-serialization](https://github.com/Kotlin/kotlinx.serialization)

## Wiki
在 [WiKi](https://github.com/mamoe/mirai/wiki/Development-Guide---Kotlin) 中查看各类帮助
