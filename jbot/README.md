<h1 align="center">
  自启机器人
  <br>
  Author: chiupam
</h1>

## 简介
随着 v4-bot 启动而启动的自定义机器人。
## 目录
- [简介](#简介)
- [目录](#目录)
- [已有功能](#已有功能)
  - [bot.py功能](#botpy功能)
  - [user.py功能](#userpy功能)
- [使用方式](#使用方式)
  - [启动bot.py文件](#启动botpy文件)
  - [启动user.py文件](#启动userpy文件)
- [常见问题](#常见问题)
- [注意事项](#注意事项)
## 已有功能
### bot.py功能
- [x] 发送 `/start` 指令可开启自定义机器人
- [x] 发送 `/restart` 指令可重启机器人
- [x] 发送 `/help` 指令可获取快捷命令
- [x] 发送 `/checkcookie` 指令可临时屏蔽失效 `cookie`
- [x] 监控 `cookie` 过期通知，并及时自动屏蔽
- [x] 监控到用户发送了已 `raw` 的链接时下载文件并选择对文件进行操作 
- [x] 监控到用户发送了 `github` 仓库的链接时开启添加仓库会话
- [x] 监控到用户发送了环境变量的代码时自动添加或替换第五区域额外的环境变量
### user.py功能
- [x] 部署成功后可自动开启 `bot.py` 所有功能
- [x] 监控布道场，关注店铺有礼
- [ ] 监控龙王庙，领取直播间红包
- [x] 监控我的脚本频道，自动更新最新的脚本
- [x] 监控组队瓜分ID频道，自动替换环境变量
## 使用方法
### 启动[bot.py](https://github.com/chiupam/JD_Diy/blob/main/jbot/bot.py)文件
方法一、 在终端中使用 Linux 命令
```
docker exec -it jd bash
cd /jd/jbot/diy
rm -rf bot.py
wget http://ghproxy.com/https://raw.githubusercontent.com/chiupam/JD_Diy/main/jbot/bot.py
pm2 restart jbot
```
方法二、 给机器人发消息（需开启cmd命令功能，且执行完后机器人不会有实际回应，请等待一阵后用 `/start` 查看效果）
```
/cmd cd /jd/jbot/diy && rm -rf bot.py && wget http://ghproxy.com/https://raw.githubusercontent.com/chiupam/JD_Diy/main/jbot/bot.py && pm2 restart jbot
```
### 启动[user.py](https://github.com/chiupam/JD_Diy/blob/main/jbot/user.py)文件
1. 把文件存储在路径 `/jbot/diy/` 下， 或可以开启cmd功能给机器人发消息 `/cmd cd /jd/jbot/diy && wget http://ghproxy.com/https://raw.githubusercontent.com/chiupam/JD_Diy/main/jbot/user.py`
2. 进入容器，使用命令 `docker exec -it jd bash`
3. 先手动停止机器人，输入命令：`pm2 stop jbot`
4. 手动前台开启机器人，输入命令：`python3 -m jbot`
5. 可能需要输入手机号和telegram验证码进行登录，如果没有要求输入，请给机器人发送 `/start`，看到第二条消息后可进行第下一步
6. 按 `Ctrl`+`C` 退出前台运行，然后输入命令 `pm2 start jbot` 启动机器人
## 常见问题
1. Question: 使用 `user.py` 后发送机器人自带指令没有反应
> Answer: 尝试进入容器后，删除位于 `/jd` 目录下的 `diy.session` 文件，然后重新按上述使用方法重新操作
## 注意事项
- 如果有使用旧的[diy.py](https://github.com/chiupam/JD_Diy/blob/main/jbot/backup/diy.py)请删除后再使用以上两个脚本，因为大部分功能重复
- 首次使用[bot.py](https://github.com/chiupam/JD_Diy/blob/main/jbot/bot.py)需要按说明登录 `telegram`，因为 `.session` 文件名已经修改
