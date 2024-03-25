> **免责声明：**

> 本仓库的所有内容仅供学习和参考之用，禁止用于商业用途。任何人或组织不得将本仓库的内容用于非法用途或侵犯他人合法权益。本仓库所涉及的爬虫技术仅用于学习和研究，不得用于对其他平台进行大规模爬虫或其他非法行为。对于因使用本仓库内容而引起的任何法律责任，本仓库不承担任何责任。使用本仓库的内容即表示您同意本免责声明的所有条款和条件。

# 仓库描述

**小红书爬虫**，**抖音爬虫**， **快手爬虫**， **B 站爬虫**， **微博爬虫**...。  
目前能抓取小红书、抖音、快手、B 站、微博的视频、图片、评论、点赞、转发等信息。

原理：利用[playwright](https://playwright.dev/)搭桥，保留登录成功后的上下文浏览器环境，通过执行 JS 表达式获取一些加密参数
通过使用此方式，免去了复现核心加密 JS 代码，逆向难度大大降低

## 功能列表

|  平台  | Cookie 登录 | 二维码登录 | 指定创作者主页 | 关键词搜索 | 指定视频/帖子 ID 爬取 | 登录状态缓存 | 数据保存 | IP 代理池 | 滑块验证码 |
| :----: | :---------: | :--------: | :------------: | :--------: | :-------------------: | :----------: | :------: | :-------: | :--------: |
| 小红书 |     ✅      |     ✅     |       ✅       |     ✅     |          ✅           |      ✅      |    ✅    |    ✅     |     ✕      |
|  抖音  |     ✅      |     ✅     |       ✕        |     ✅     |          ✅           |      ✅      |    ✅    |    ✅     |     ✅     |
|  快手  |     ✅      |     ✅     |       ✕        |     ✅     |          ✅           |      ✅      |    ✅    |    ✅     |     ✕      |
|  B 站  |     ✅      |     ✅     |       ✕        |     ✅     |          ✅           |      ✅      |    ✅    |    ✅     |     ✕      |
|  微博  |     ✅      |     ✅     |       ✕        |     ✅     |          ✅           |      ✅      |    ✅    |    ✅     |     ✕      |

## 使用方法

### 创建并激活 python 虚拟环境

```shell
# 进入项目根目录
cd MediaCrawler

# 创建虚拟环境
python -m venv venv

# macos & linux 激活虚拟环境
source venv/bin/activate

# windows 激活虚拟环境
venv\Scripts\activate

```

### 安装依赖库

```shell
pip3 install -r requirements.txt
```

### 安装 playwright 浏览器驱动

```shell
playwright install
```

### 运行爬虫程序

```shell
# 默认没有开启评论爬取模式，有需要请到配置文件中指定
# 从配置文件中读取关键词搜索相关的帖子并爬去帖子信息与评论
python main.py --platform xhs --lt qrcode --type search

# 从配置文件中读取指定的帖子ID列表获取指定帖子的信息与评论信息
python main.py --platform xhs --lt qrcode --type detail

# 打开对应APP扫二维码登录

# 其他平台爬虫使用示例, 执行下面的命令查看
python main.py --help
```

### 数据保存

- 支持保存到关系型数据库（Mysql、PgSQL 等）
- 支持保存到 csv 中（data/目录下）
- 支持保存到 json 中（data/目录下）

<!-- ## 打赏

如果觉得项目不错的话可以打赏哦。您的支持就是我最大的动力！

打赏时您可以备注名称，我会将您添加至打赏列表中。

<p>
  <img alt="打赏-微信" src="" style="width: 200px;margin-right: 140px;" />
  <img alt="打赏-支付宝" src="" style="width: 200px" />
</p> -->

## 运行报错常见问题 Q&A

> 遇到问题先自行搜索解决下，现在 AI 很火，用 ChatGPT 大多情况下能解决你的问题 [免费的 ChatGPT](https://sider.ai/invited?c=8e03db1a973401fdf114ed9cf9f8c183)

➡️➡️➡️ [常见问题](docs/常见问题.md)

## 项目代码结构

➡️➡️➡️ [项目代码结构说明](docs/项目代码结构.md)

## 手机号登录说明

➡️➡️➡️ [手机号登录说明](docs/手机号登录说明.md)

## star 趋势图

- 如果该项目对你有帮助，star 一下 ❤️❤️❤️

[![Star History Chart](https://api.star-history.com/svg?repos=NanmiCoder/MediaCrawler&type=Date)](https://star-history.com/#NanmiCoder/MediaCrawler&Date)

## 参考

- xhs 客户端 [ReaJason 的 xhs 仓库](https://github.com/ReaJason/xhs)
- 短信转发 [参考仓库](https://github.com/pppscn/SmsForwarder)
- 内网穿透工具 [ngrok](https://ngrok.com/docs/)
