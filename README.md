# proj183-xiaomi-zcore-teeos

## 基于zCore的TEEOS

### 项目描述

Android 系统是目前应用最广泛的手机操作系统，拥有非常开放的生态环境，由此它的安全性也备受大家关注。TEE（Trusted Execution Environment）是一种基于硬件隔离的解决方案，独立于 Android 系统之外的可信执行环境，与可信执行环境（TEE）相对的是运行普通操作系统和应用程序的 REE（Rich Execution Environment）。相比于运行在 REE 的 Android 系统，TEE 拥有更高的权限，运行于 Android 无法访问的独立的执行内存中，应用程序可以把关键处理和敏感数据放在 TEE 中执行或加密存储，这样即便是有攻击者获得了 Android 系统的 Root 权限，也无法进一步窃取或攻击 TEE 中的数据。

目前Android系统大部分的硬件平台是ARM soc，TEEOS基本上都是C/C++实现的，本项目目标是以zCore（rust实现的zircon微内核）为基础，构建运行在ARM trustzone 上的TEEOS，用rust实现Global platform标准API，在REE侧实现对应的client API。在TEEOS实现之后，可以用rust写一个测试CA（client application）和TA（trust application）进行验证。

### 所属赛道

2022全国大学生操作系统比赛的“OS功能挑战”赛道

### 项目导师

• 潘双全：panshuangquan@xiaomi.com

• 聂伟：[niewei@xiaomi.com](mailto:niewei@xiaomi.com)

### 难度

第一阶段难度中等

第二阶段难度较高

### 预期目标

硬件平台可以选用树莓派，第一阶段是基础，第二阶段是挑战

#### 第一阶段

1. 在ARM secure world 移植zCore，涉及bootloader，ATF等改动

2. 实现REE/TEE的IPC，Android侧和zCore侧需要对应的driver，通过shared memory实现IPC

3. 通过IPC实现Android侧执行TEE侧的shell

#### 第二阶段

1. zCore上面搭建TEE框架，支持Global platform API，包括TA management，secure storage，Cryptographic algorithm等

2. 完善调试机制，可以分析TEE crashdump

3. 用rust实现一个测试CA和TA，验证Global platform API

