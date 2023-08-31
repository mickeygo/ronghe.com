# ronghe.com

## 说明

昆山融禾电子科技有限公司门户完整

## 模板

框架模板：[hugo](https://gohugo.io)

主题：[universal](https://github.com/devcows/hugo-universal-theme)

## 部署

### CentOS

查看服务是否在后台运行 => `ps -aux | grep hugo`

查看服务占用端口 => `netstat -tunlp | grep 1313`

关闭进程 => `kill -9 pid`

#### nohup 后台启动

后台启动命令（不含日志） => `nohup hugo server --bind="0.0.0.0" > /dev/null 1>&2 &`

后台启动命令（含日志） => `nohup hugo server --bind="0.0.0.0" > out.log 2>&1 &`

#### screen 启动服务

CentOS8以上需要安装 => `yum install epel-release`

新建一个窗口 => `screen -S [虚拟终端名字]`

启动服务 => `hugo server --bind="0.0.0.0" > out.log 2>&1`

退出窗口（保留当前窗口） => `ctrl+a+d` 或 `screen -d`

查看已存在的screen => `screen -ls`

重新连接窗口 => `screen -r [PID]` 或 `screen -R [窗口名称]`

#### tmux 启动服务

创建 tmux 终端 => `tmux new -s [终端名称]`

退出终端 => 先按 `ctrl+b` tmux 接收指令，再按 `d` 即可回到主终端

退出终端 => `ctrl+b+d`，同时按住三个键，或是输入 `exit` 命令

查看已存在的 tmux => `tmux ls`

重新进入 => `tmux a -t [终端名称]`

#### 直接用 Hugo 作为你的 Web 服务器

$ hugo server --baseURL=http://ksronghe.com/ --port=80 --appendPort=false --bind=0.0.0.0

若显示 “Error: command error: server startup failed: listen tcp 127.0.0.1:80: bind: permission denied” 错误，使用超管权限:
$ sudo /usr/local/bin/hugo server --baseURL=http://ksronghe.com/ --port=80 --appendPort=false --bind=0.0.0.0
