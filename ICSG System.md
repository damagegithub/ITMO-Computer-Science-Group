# ITMO Computer Science Group Control System
---
1. 权限控制

||Member|Administrator|
||-|-|
|查看、标记自己的 Daily Words|√|√|
|在 Daily Words 发送消息|√|√|
|控制 Daily Words 的计划||√|
|对 Daily Words 的词库进行控制||√|
|发布任务、指派任务、归档任务||√|
|查看自己的任务、确认完成自己的任务|√|√|

2. Daily Words 逻辑

- Administrator 制定单词计划
- Member 每日得到计划单词并背诵

3. Task System 逻辑

- Administrator 发布任务
    - 包含字段
        - 任务属组
        - 任务名称
        - 任务说明
    - 此任务进入 System TO-DO List
- Administrator 指派任务
    - 包含字段
        - 任务被指派者
        - 任务截止时间
    - 此任务进入 System In Process List、被指派者的 Personal TO-DO List，同时 telegram robot 向频道和被指派者推送任务
- Member 查看个人任务
    - 可在此系统的 Web 界面查看 Personal TO-DO List 或 Personal Finished List
    - 可在 telegram robot 的推送中或者使用命令查看个人的 Personal TO-DO List 或 Personal Finished List
- Member 完成被指派任务后确认完成
    - 被指派者可在 telegram robot 或者 Web 界面将任务确认完成，此时任务将从个人的 Personal TO-DO List 转移到 Personal Finished List，同时将从 System In Process List 转移到 System Finished List
- Administrator 检验后归档任务
    - 如果任务被检验成功，该任务将从 System Finished List 转移到 System Archive List
    - 如果任务被检验失败，该任务将会回退到指派任务阶段