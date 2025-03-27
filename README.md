# WeChatHook（api）

#### 介绍
WeChatHook 是一个功能强大的 Python 微信机器人框架，基于 DLL 注入技术构建，支持丰富的接口和高扩展性。通过多线程消息处理，它能够高效应对大量消息，极大地提升你的开发效率。无论是处理复杂任务还是实现个性化需求！

#### 基础功能

- 登录状态检测
- 用户信息获取（wxid/昵称/备注）
- 消息撤回管理
- 聊天记录操作（查询/删除）

#### 消息处理

|类型|同步发送|CDN 发送|引用回复|合并转发|
|--|--|--|--|--|
|文本消息|✅|✅|✅|✅|
|图片/文件|✅|✅|✅|✅|
|语音/视频|✅|✅|-|✅|
|位置/名片|✅|-|-|✅|
|小程序/链接|✅|-|✅|✅|


#### 群组管理

- 群创建/解散
- 成员管理（添加/移除/邀请）
- 群公告设置
- 群备注修改
- @全体成员消息
- 群主权限转移

#### 好友管理

- 好友添加（二维码/名片/微信号）
- 权限控制（拉黑/朋友圈权限）
- 僵尸粉检测（双重方法）
- 自动通过好友请求
- 企业微信好友对接

#### 高级功能

- 朋友圈互动（点赞/评论/发布）
- 微信支付（收款/转账/退款）
- 数据库操作（SQL 执行/数据提取）
- OCR 图片文字识别
- 公众号文章抓取
- 企业微信群管理

#### 微信版本

[WeChatSetup3.9.5.81.exe](http://WeChatSetup3.9.5.81.exe)

#### 安装

pip install wxhook

#### 使用示例（技术微信:LY-wenboo）


```
# import os
# os.environ["WXHOOK_LOG_LEVEL"] = "INFO" # 修改日志输出级别
# os.environ["WXHOOK_LOG_FORMAT"] = "<green>{time:YYYY-MM-DD HH:mm:ss}</green> | <level>{message}</level>" # 修改日志输出格式
from wxhook import Bot
from wxhook import events
from wxhook.model import Event


def on_login(bot: Bot, event: Event):
    print("登录成功之后会触发这个函数")


def on_start(bot: Bot):
    print("微信客户端打开之后会触发这个函数")


def on_stop(bot: Bot):
    print("关闭微信客户端之前会触发这个函数")


def on_before_message(bot: Bot, event: Event):
    print("消息事件处理之前")


def on_after_message(bot: Bot, event: Event):
    print("消息事件处理之后")


bot = Bot(
    # faked_version="3.9.10.19", # 解除微信低版本限制
    on_login=on_login,
    on_start=on_start,
    on_stop=on_stop,
    on_before_message=on_before_message,
    on_after_message=on_after_message
)


# 消息回调地址
# bot.set_webhook_url("http://127.0.0.1:8000")

@bot.handle(events.TEXT_MESSAGE)
def on_message(bot: Bot, event: Event):
    bot.send_text("filehelper", "hello world!")


bot.run()
```
（技术微信:LY-wenboo）
