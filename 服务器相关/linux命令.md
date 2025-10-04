在 Ubuntu 系统中，你可以使用以下命令来查看指定端口上运行的程序： 
### 1. 使用 `netstat` 命令 
`netstat` 是一个常用的网络工具，可以显示网络连接、路由表、接口统计信息等。 
```sudo netstat -tuln | grep :<端口号> ``` 
- `-t`：显示 TCP 端口。 
- `-u`：显示 UDP 端口。
- `-l`：显示监听中的端口。 
- `-n`：以数字形式显示地址和端口号。 
- `grep :<端口号>`：过滤出指定端口的行。 例如，查看端口 `8080` 的程序：
```sudo netstat -tuln | grep :8080 ``` 
### 2. 使用 `ss` 命令 
`ss` 是 `netstat` 的现代替代工具，功能更强大，速度更快。 
```sudo ss -tuln | grep :<端口号> ``` 
- `-t`：显示 TCP 端口。 
- `-u`：显示 UDP 端口。 
- `-l`：显示监听中的端口。 
- `-n`：以数字形式显示地址和端口号。 例如，查看端口 `8080` 的程序： 
```sudo ss -tuln | grep :8080 ``` 
### 3. 使用 `lsof` 命令 
`lsof` 是一个列出打开文件的工具，可以用来查看哪个程序正在使用指定端口。 
```sudo lsof -i :<端口号> ```
- `-i :<端口号>`：显示使用指定端口的程序。 例如，查看端口 `8080` 的程序： 
```sudo lsof -i :8080 ``` 
### 4. 使用 `fuser` 命令 
`fuser` 可以显示使用指定端口的进程 ID。 
```sudo fuser <端口号>/tcp ``` 
- `<端口号>/tcp`：指定 TCP 端口。 
- 如果是 UDP 端口，可以使用 `<端口号>/udp`。 
例如，查看端口 `8080` 的程序： 
```sudo fuser 8080/tcp ``` 
### 示例输出 
假设你运行 `sudo lsof -i :8080`，输出可能如下： 
``` COMMAND PID USER FD TYPE DEVICE SIZE/OFF NODE NAME java 1234 user 123u IPv6 12345 0t0 TCP *:http-alt (LISTEN) ``` 
- `COMMAND`：程序名称（如 `java`）。 
- `PID`：进程 ID（如 `1234`）。 
- `USER`：运行该程序的用户（如 `user`）。 
- `NAME`：端口和状态（如 `*:http-alt (LISTEN)`）。 
通过这些命令，你可以轻松找到使用指定端口的程序及其详细信息。


### 杀死进程
找到进程PID sudo lsof -i :6080,8088
杀进程 sudo kill 1234
强制杀进程 sudo kill -9 1234
验证是否关闭 sudo lsof -i :6080,8088