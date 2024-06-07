# Arch Linux Loong64 Maintainance 计划

## 背景

龙芯是优秀的自主可控CPU，目前`3A6000`性能已经达到10代酷睿水准，有较大的发展潜力。`Arch Linux`是广为人知、备受喜爱的Linux发行版，以滚动更新、活跃的社区和详细的教程闻名，非常适合支持龙芯这类新型的、上游化的CPU。

目前 `Arch Linux`的打包测试与发行都由武校田老师负责，工作量过于集中，很难做到稳定滚动更新。LCPU目前有足够的经费、较强的技术和勉强充足的同学来负责这部分工作。

## 主要目标

1. 建设 `Loong Arch Linux`长期可维护性的社区、打包、分发、响应机制
2. 组织开发者，恢复 `Loong Arch Linux`的滚动，提供测试
3. 与其他发行版合作，共同建设龙芯的生态体系

## 主要思路

1. 共建，团结一切能推动`loong`架构生态的力量；增长
2. 上游化，尽可能把所有port和修改推送到上游，以patch的形式从上游同步
3. 文档化，所有内容都要求写文档，避免后续维护者burnout的困境
4. 自动化

## 时间表

2024年2月27日-3月15日：社区准备，初步基础设施部署，学习调研之前的打包方式，gentoo AOSC fedora deepin debain和arch Linux rv的打包方式，准备构建系统

2024年3月15日-6月1日：武老师季度更新发布，LCPU尝试接手日常维护，4台3A6000打包测试机到位，组织镜像站Tier和备份，bug tracker

2024年6月1日-10月：逐步重构武老师的项目组织形式，试图满足上游化要求，深度定制基础设施，和肥猫共同探究ArchLinux ports

之后，长期维护

## 一些具体实现

### 构建管理

修改肥猫的[工作流脚本](https://github.com/felixonmars/archlinux-futils)，入口点为[riscvu](https://github.com/felixonmars/archlinux-futils/blob/master/archriscv-staging/riscvu)。

`PKGBUILD`和补丁包使用patch文件形式管理

### 镜像站 Tier

Tier0：LCPU 虚拟机，仅内网，开放rsync

Tier1：PKU Mirror，半天同步一次

Tier2：NJU、WSYU等，通知将上游更改为PKU

Tier3：罗马尼亚备份机，进行历史包存档

## 硬件

虚拟机：3台双路 AMD 9654，约120台虚拟3A5000

物理机：1台5000 1台6000 5台华硕 3A6000

32G 内存，1T系统盘

NAS？NFS

## 具体问题

1. 重要base包的patch如何从上游分离
2. 如何获取需要的更新以及patch、如何获知包过时（从上游拉）
3. 构建和分发**工作流**的确定，包签名等置信
4. 文档同步、工作协同

