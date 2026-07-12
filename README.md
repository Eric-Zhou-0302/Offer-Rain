<div align="center">
  <img src="assets/logo.png" width="200" alt="eric's-logo" />
  <h1>📮 Offer-Rain: 把 JD 发给 Agent，让他帮你投递简历。</h1>
  <p><strong>等待你的 Offer 雨吧！</strong></p>
  <p>
    手动投简历的痛不在于写邮件，而在于重复打开邮箱、抄地址、粘模板、附简历。
    Offer-Rain 把每一次投递写成一个 JSON 文件，让 agent 帮你确认、帮你发，
    你只需要准备好简历和 JD 列表。
  </p>
  <p>
  <a href="https://mail.163.com">
    <img alt="网易163邮箱" src="https://img.shields.io/badge/163%E9%82%AE%E7%AE%B1-Mail-ff2442?style=for-the-badge&labelColor=555" />
  </a>
  <a href="https://opensource.org/licenses/MIT">
    <img alt="License" src="https://img.shields.io/badge/License-MIT-blue?style=for-the-badge&labelColor=555" />
  </a>
</p>

</div>

<p align="center">
  <img
    src="assets/main.png"
    alt="offer-rain preview"
    width="900"
  />
</p>

---

## 安装

复制这段话，让你的 OpenClaw / Claude Code / Codex ... 安装：

```
帮我安装这个 Skill：
https://github.com/Eric-Zhou-0302/Offer-Rain
```

当然，你也可以手动安装这个项目至你的技能目录：

```bash
git clone https://github.com/Eric-Zhou-0302/Offer-Rain.git
```

---

## 使用

### 准备工作

- 准备一个 `@163` 邮箱，并到 [网易邮箱官网-设置-POP3/SMTP/IMAP](https://mail.163.com) 获取本 Skill 专用的邮箱授权码，并确保已开启 SMTP 服务。
- 准备一份简历。

### 第一步

无论你在 Anywhere 刷到 JD，复制下来甩给 Agent，让它替你投：

```
帮我投递这两个岗位：

JD 1：
公司：鼎盛资本（虚拟）
地点：上海
岗位描述：
协助基金经理进行多因子模型回测与数据清洗
跟踪宏观
参与另类数据（如舆情、天气）的信号提取与验证
投递要求：
邮件主题：量化岗-姓名-学校
正文：注明最早到岗日 + 一句话说明你的编程工具偏好（Python/R/其他）
简历命名：CV_姓名.pdf
邮箱：example@dingsheng-cap.virtual

JD 2：
公司：星云科技（虚拟）
地点：深圳（可远程）
岗位描述：
负责高并发微服务接口设计与性能调优
维护Kafka/RabbitMQ消息中间件，处理数据管道异常
编写单元测试与接口文档，参与Code Review
投递要求：
邮件主题：后端-姓名-工作年限
正文：附上GitHub/技术博客链接 + 最近一个项目的简要技术栈说明（50字内）
简历命名：resume_姓名.pdf
邮箱：example@xingyun-tech.virtual
```

之后，Agent 会按照投递要求自动帮你处理邮件主题、正文、简历命名等，并递呈方案由你审核，你同意后 Agent 会依次进行投递。

### 第二步

**每天翻翻邮箱，保持手机畅通，备好西装领带，准备迎接属于你的 Offer 雨 ⛈️。**

---

## 工作流

```
        user.json            ←  你的发件邮箱 + 授权码 + 简历路径（只填一次）
              │
              ▼
        log/YYYY-MM-DD/
         ├─ alibaba.json     ←  每个招聘方一份
         ├─ tencent.json
         └─ meituan.json
              │
              ▼
        scripts/send_email.py
              │
              ▼
       ┌──────────────┐
       │  招聘方邮箱   │   ←  附件 + 主题 + 正文
       └──────────────┘
```

*先配一次，再投一摞。*

---

## 关于配置信息 `user.json`

### 配置字段说明

| 字段 | 必填 | 说明 |
|---|---|---|
| `smtp_server` | ✅ | SMTP 服务器地址 |
| `smtp_port` | ✅ | SMTP 端口（SSL 通常 465） |
| `sender` | ✅ | 发件人邮箱地址 |
| `password` | ✅ | **邮箱授权码**（不是登录密码） |
| `attachment_path` | ✅ | 简历附件路径 |
| `name` | ❎ | 你的姓名 |
| 其他可选字段 | ❎ | 用于 Agent 编辑邮件主题、正文、简历命名等 |

### 初始化

如果 `user.json` 缺少投递任务所需的相关字段，Agent 会询问你相关内容，并存入 `user.json`，并在后续投递任务中复用。

### 手动配置与修改

当然，当你的个人信息需要更新时，你也可以手动配置与修改 `user.json`，或让你的 Agent 修改。

---

## 安全与隐私

Offer-Rain 的核心承诺：你的数据永远存放在本地，你的邮件必须由你确认后才会发送。

- 邮箱地址，授权码等信息存放于本 Skill 目录下的 `user.json` 文件中。
- 单投递任务的配置文件存放于本 Skill 目录下的 `log/` 目录中。

---

## Q & A

**Q: 不是 163 邮箱能用吗？**

A: 不可以，仅支持 163 邮箱。*顺便提一句，还是不要用你的QQ邮箱投递简历了。*

**Q: 邮件发错了能撤回吗？**

A: Agent 不能帮你撤回，但是你可以到邮箱客户端手动撤回。

---

## 协议

[MIT](./LICENSE) @ 2026 Eric Zhou

---

## 请作者喝杯咖啡

<div align="center">
  <p>
    如果这个项目帮你顺利发出了第一封、第五封，或者第五十封投递邮件，
    <br />
    欢迎请作者喝杯咖啡。
  </p>
  <p>
    愿你的邮箱早日收到面试邀请，
    <br />
    而我的杯子里也能顺便续上一点热美式。
  </p>
  <img src="assets/buy-me-a-coffee.jpg" alt="请作者喝杯咖啡" width="320" />
  <p>
    <sub>自愿支持，不影响功能使用，也不影响 Offer 雨落下。</sub>
  </p>
</div>
