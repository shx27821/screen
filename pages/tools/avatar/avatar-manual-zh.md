---
title: SCP-079-AVATAR
---

<link rel="stylesheet" href="/css/chinese.css">
<button onmouseover="PlaySound('totop1')" onmouseout="StopSound('totop1')" onclick="window.location.href = '/avatar-manual/';" class="en">Click Here to English Page</button>

---

# SCP-079-AVATAR 使用手册

本文介绍如何使用 SCP-079-AVATAR 的机器人实例，对应的搭建说明在[此处](/avatar-zh/)。

---

## 运作流程

以下介绍机器人的工作流程，在进行使用和设置前，建议您了解此流程。

---

### 加入群组

此机器人不接受任何群组的使用申请，群组也无法对此机器人进行设置，服务托管者自行决定此机器人加入哪些群组中。

AVATAR 应加入成员人数较多的群组，其加入的群组只可以为 NOSPAM 机器人所在的群组，但不可加入 NOSPAM 所在的全部群组，避免机器人的真实身份被轻易识别。

同时，我们建议 AVATAR 只加入管理员较为活跃的群组，以群组的管理员能够及时处理广告和举报、及时干预群组内的异常现象为宜。这样是为了保证由 AVATAR 自动生成的全局白名单具有一定的可靠性。

### 分析头像

当用户加入群组时，AVATAR 会检查是否已向 NOSPAM 分享过此用户当前的头像：如已分享过，则不做操作；如未分享，则通过 EXCHANGE 频道向 NOSPAM 发送此用户当前的头像，以供分析。

### 生成白名单

通过 AVATAR 加入的群组建立受信用户列表。每日更新。

用户加入白名单的条件：

- 非黑名单用户
- 非受追踪的用户
- 评分不大于 1.2
- 未被 WARN 移除或封禁
- 加入群组超过一定时间
- 在自定义时段内的累计发言超过特定条数（仅计算未被删除的有效发言的条数，主动或被动删除的发言均算为无效发言）
- 次日，该用户在自定义时间点仍为群组成员，并且未被管理员限制发言

依 `config.ini` 文件中的定义，添加白名单的过程可这样描述：

> AVATAR 将在每日的 `time_check` 点生成新的白名单用户列表。
>
> 在 `time_check` 点之前，若用户在候选列表中，且仍为群组成员未被限制，则被加入白名单中。
>
> 在 `time_check` 点之前，若用户不在候选列表中，但用户在 `time_begin` 到 `time_end` 这一时间段内，发送的有效消息条数超过 `limit_message` 条，则用户会被加入到候选列表中，待次日的 `time_check` 点判断最终是否应将其加入到白名单中。

白名单可作为操作等级的参考。不同机器人根据实际情况做不同的对待。例如白名单用户不会被各机器人操作升级，NOSPAM 的检查相对宽松，而 WATCH 则有可能因为白名单而不对用户进行追踪处理。

---

## 实用命令

以下介绍本机器人可响应的文字命令。

---

### SCP-079-TEST 中的成员

- `/version`：通过 HIDE 间接检查机器人版本