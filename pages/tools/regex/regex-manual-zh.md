---
title: SCP-079-REGEX
---

<link rel="stylesheet" href="/css/chinese.css">
<button onmouseover="PlaySound('totop1')" onmouseout="StopSound('totop1')" onclick="window.location.href = '/regex-manual/';" class="en">Click Here to English Page</button>

# SCP-079-REGEX 使用手册

[TOC]

## 概述

SCP-079 工作组 通过 SCP_079_REGEX_BOT 管理着 SCP-079 旗下所有机器人使用的正则表达式。

## 声明

1. [SCP-079-REGEX](https://github.com/scp-079/scp-079-regex) 项目未公开 [SCP-079-REGEX](https://t.me/SCP-079_REGEX_BOT) 所使用的正则表达式且暂无公开 [SCP-079-REGEX](https://t.me/SCP-079_REGEX_BOT) 所使用的正则表达式的计划。
2. 本文不讲述正则表达式的语法，请有管理正则表达式需求者自行学习正则表达式的相关语法。
3. 本文介绍如何使用 SCP-079-REGEX 机器人实例，对应的搭建说明在[此处](/regex/)。
4. 本文中假设 SCP-079 旗下所有机器人的所有功能均被开启，实际上本文所述的所有封禁、删除均受`白名单`、`操作降级`和`群组对机器人的配置`共同调控。

## 规则集说明

### 广告用语

规则集代号：ad ada-adz

### 头像分析

规则集代号：ava


SCP-079-NOSPAM：将使用该类规则分析用户头像 OCR 结果，触发该类规则将导致封禁。


### 敏感检测

规则集代号：bad

SCP-079-NOSPAM:更新用户评分，自动举报至 SCP-079-WARN 提交至群组管理员处理。


### 自动封禁

规则集代号：ban



SCP-079-AVATAR
SCP-079-CAPTCHA
SCP-079-CLEAN
SCP-079-LANG
SCP-079-LONG
SCP-079-NOPORN
SCP-079-NOSPAM
SCP-079-RECHECK
SCP-079-TIP
SCP-079-WATCH



SCP-079-NOSPAM 全局封禁触发者，并加入全局黑名单。

### 简介检查

规则集代号：bio

SCP-079-AVATAR
SCP-079-CAPTCHA
SCP-079-CLEAN
SCP-079-LANG
SCP-079-LONG
SCP-079-NOPORN
SCP-079-NOSPAM
SCP-079-RECHECK
SCP-079-TIP
SCP-079-WATCH



### 联系方式

规则集代号：con

### 自动删除

规则集代号：del

SCP-079-CLEAN
SCP-079-LANG
SCP-079-LONG
SCP-079-NOPORN
SCP-079-NOSPAM:删除触发的消息并更新用户评分
SCP-079-RECHECK
SCP-079-WATCH

### 文件名称

规则集代号：fil

SCP-079-CLEAN
SCP-079-LANG
SCP-079-NOPORN
SCP-079-NOSPAM:封禁发送者并更新用户评分
SCP-079-RECHECK
SCP-079-TIP
SCP-079-WATCH

### IM 链接

规则集代号：iml



### 电话号码

规则集代号：pho



### 名称封禁

规则集代号：nm



### RM 笑话

规则集代号：rm

SCP-079-TIP：回复触发消息，提示他人谨慎执行该操作。

### 短链接

规则集代号：sho



### 特殊中文

规则集代号：spc



### 特殊英文

规则集代号：spe



### 贴纸删除

规则集代号：sti



### TG 链接

规则集代号：tgl

SCP-079-CLEAN
SCP-079-NOPORN
SCP-079-NOSPAM：作为`con 规则集`的子集，触发效果同触发
SCP-079-WATCH

### TG 代理

规则集代号：tgp

SCP-079-CLEAN：
SCP-079-WATCH

### 追踪封禁

规则集代号：wb

SCP-079-CAPTCHA：
SCP-079-CLEAN：
SCP-079-NOFLOOD：
SCP-079-NOPORN：
SCP-079-NOSPAM：
SCP-079-RECHECK：
SCP-079-TIP：
SCP-079-WATCH：


### 追踪删除

规则集代号：wd

SCP-079-NOSPAM：
SCP-079-WATCH：

### 测试用例

规则集代号：test

SCP-079-REGEX：SCP-070-TEST 群组成员可发送消息至 SCP-070-TEST 群组检测是否匹配正则表达式。

## 基本操作
本章节所有操作均在 SCP-079-REGEX 或 SCP-079-TEST 群组中完成。

### 添加正则表达式
在 SCP-079-REGEX 群组中通过 `/add 任意规则集代号 正则表达式`或`/ad 任意规则集代号 正则表达式` 添加正则表达式，例如：`/add wb 专业引流` `/ad del 1a2b3c4d5e6f`。
如需将相同的正则表达式添加至多个规则集中，可使用 `/same 规则集代号1 规则集代号2 规则集代号3 规则集代号4`完成。

---

示例：
在执行完 `/ad del 1a2b3c4d5e6f` 后`1a2b3c4d5e6f`被添加进了`del 规则集`，此时若需将`1a2b3c4d5e6f`同时加入`nm 规则集`，只需回复`/ad del 1a2b3c4d5e6f`这条消息`/same nm`；若此时又需将`1a2b3c4d5e6f`加入`ad 规则集`和`test 规则集`，只需再次回复`/ad del 1a2b3c4d5e6f`这条消息`/same ad test`即可。
该情景下操作还可进一步简化，SCP-079-REGEX 会读取正则表达式中的注释部分，只需使用注释注明包含该正则表达式的所有规则集即可，例如该情景下使用`/ad del 1a2b3c4d5e6f(?# del nm ad test)`即可一键将`/ad del 1a2b3c4d5e6f(?# del nm ad test)`加入`del 规则集`、`nm 规则集`、`ad 规则集`、`test 规则集`。

---

在同规则集中添加与已有正则表达式近似的正则表达式是会触发

### 删除正则表达式
在 SCP-079-REGEX 群组中通过 `/remove 任意规则集代号 正则表达式`或`/rm 任意规则集代号 正则表达式` 添加正则表达式，例如：`/remove wb 专业引流` `/rm del 1a2b3c4d5e6f`。
如需将相同的正则表达式添加至多个规则集中，可使用 `/same 规则集代号1 规则集代号2 规则集代号3 规则集代号4`完成。
示例：
在执行完 `/rm del 1a2b3c4d5e6f` 后`1a2b3c4d5e6f`被从`del 规则集`中删除，此时若需将`1a2b3c4d5e6f`同时从`nm 规则集`删除，只需回复`/rm del 1a2b3c4d5e6f`这条消息`/same nm`；若此时又需将`1a2b3c4d5e6f`从`ad 规则集`和`test 规则集`中删除，只需再次回复`/rm del 1a2b3c4d5e6f`这条消息`/same ad test`即可。

该情景下操作还可进一步简化，SCP-079-REGEX 会读取正则表达式中的注释部分，只需使用注释注明包含该正则表达式的所有规则集即可，例如该情景下使用`/rm del 1a2b3c4d5e6f(?# del nm rm test)`即可一键将`/rm del 1a2b3c4d5e6f(?# del nm ad test)`从`del 规则集`、`nm 规则集`、`ad 规则集`、`test 规则集`中一键删除。

### 检索正则表达式

SCP-079-REGEX 已提供多种方式检索正则表达式。

#### 查阅全部

您可使用 `/ls 规则集代号`显示该规则集中的全部内容，该列表默认按照平均触发次数降序排列

#### 搜索
您可使用 `/search 规则集代号 内容`、`/s 规则集代号 内容`或`/find 规则集代号 内容` 。除已有的规则集代号外，这三个命令均支持规则集代号`all`来搜索所有规则集。

### 触发测试