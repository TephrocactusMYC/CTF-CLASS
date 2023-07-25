OverTheWire社区是一个提供wargame的网站，可以帮助安全爱好者以趣味的方式进行学习、练习安全知识。

[bandit，熟悉linux和bash的有趣的网站](https://overthewire.org/wargames/bandit/)
# level0 ssh远程登录
```
ssh bandit0@bandit.labs.overthewire.org -p 2220
# 然后输入密码即可
```
![level0](image.png)
顺利拿到提示符
# level1
要求使用cat命令，水
```
bandit0@bandit:~$ ll
total 24
drwxr-xr-x  2 root    root    4096 Apr 23 18:04 ./
drwxr-xr-x 70 root    root    4096 Apr 23 18:05 ../
-rw-r--r--  1 root    root     220 Jan  6  2022 .bash_logout
-rw-r--r--  1 root    root    3771 Jan  6  2022 .bashrc
-rw-r--r--  1 root    root     807 Jan  6  2022 .profile
-rw-r-----  1 bandit1 bandit0   33 Apr 23 18:04 readme
bandit0@bandit:~$ cat readme
NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL
bandit0@bandit:~$
```
# level2
处理名字叫“-”的文件，这个由于会和参数解析混了，我的处理办法是加上“./”
```
bandit1@bandit:~$ ll
total 24
-rw-r-----  1 bandit2 bandit1   33 Apr 23 18:04 -
drwxr-xr-x  2 root    root    4096 Apr 23 18:04 ./
drwxr-xr-x 70 root    root    4096 Apr 23 18:05 ../
-rw-r--r--  1 root    root     220 Jan  6  2022 .bash_logout
-rw-r--r--  1 root    root    3771 Jan  6  2022 .bashrc
-rw-r--r--  1 root    root     807 Jan  6  2022 .profile
bandit1@bandit:~$ cat ./-
rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi
bandit1@bandit:~$
```
# level3
处理名字里有空格的文件，直接拿双引号包起来即可
```
bandit2@bandit:~$ ll
total 24
drwxr-xr-x  2 root    root    4096 Apr 23 18:04 ./
drwxr-xr-x 70 root    root    4096 Apr 23 18:05 ../
-rw-r--r--  1 root    root     220 Jan  6  2022 .bash_logout
-rw-r--r--  1 root    root    3771 Jan  6  2022 .bashrc
-rw-r--r--  1 root    root     807 Jan  6  2022 .profile
-rw-r-----  1 bandit3 bandit2   33 Apr 23 18:04 spaces in this filename
bandit2@bandit:~$ cat "spaces in this filename"
aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG
bandit2@bandit:~$
```
# level4
处理文件夹，正确的方式应该是cd进去再处理，因为在这个阶段还不涉及绝对路径、相对路径之类的概念，但是我懒了

另外，还有个处理隐藏文件，可以使用ls -l命令，在大多数bash中会把ls -al写成别名ll

也可以使用ls -a
```
bandit3@bandit:~$ ll
total 24
drwxr-xr-x  3 root root 4096 Apr 23 18:04 ./
drwxr-xr-x 70 root root 4096 Apr 23 18:05 ../
-rw-r--r--  1 root root  220 Jan  6  2022 .bash_logout
-rw-r--r--  1 root root 3771 Jan  6  2022 .bashrc
drwxr-xr-x  2 root root 4096 Apr 23 18:04 inhere/
-rw-r--r--  1 root root  807 Jan  6  2022 .profile
bandit3@bandit:~$ ls inhere/
bandit3@bandit:~$ ll inhere/
total 12
drwxr-xr-x 2 root    root    4096 Apr 23 18:04 ./
drwxr-xr-x 3 root    root    4096 Apr 23 18:04 ../
-rw-r----- 1 bandit4 bandit3   33 Apr 23 18:04 .hidden
bandit3@bandit:~$ cat ./inhere/.hidden
2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe
bandit3@bandit:~$
```
# level5

```
bandit4@bandit:~$ ls
inhere
bandit4@bandit:~$ cd inhere/
bandit4@bandit:~/inhere$ ll
total 48
drwxr-xr-x 2 root    root    4096 Apr 23 18:04 ./
drwxr-xr-x 3 root    root    4096 Apr 23 18:04 ../
-rw-r----- 1 bandit5 bandit4   33 Apr 23 18:04 -file00
-rw-r----- 1 bandit5 bandit4   33 Apr 23 18:04 -file01
-rw-r----- 1 bandit5 bandit4   33 Apr 23 18:04 -file02
-rw-r----- 1 bandit5 bandit4   33 Apr 23 18:04 -file03
-rw-r----- 1 bandit5 bandit4   33 Apr 23 18:04 -file04
-rw-r----- 1 bandit5 bandit4   33 Apr 23 18:04 -file05
-rw-r----- 1 bandit5 bandit4   33 Apr 23 18:04 -file06
-rw-r----- 1 bandit5 bandit4   33 Apr 23 18:04 -file07
-rw-r----- 1 bandit5 bandit4   33 Apr 23 18:04 -file08
-rw-r----- 1 bandit5 bandit4   33 Apr 23 18:04 -file09
bandit4@bandit:~/inhere$ cat ./-file06
'�wk^j��M�;,�co9bandit4@bandit:~/inhere$
# 使用reset后
bandit4@bandit:~/inhere$ cat ./-file07
lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR
bandit4@bandit:~/inhere$
```
[这里](https://blog.csdn.net/tsummer2010/article/details/105374173)有一个讲了reset和clear的区别，很简单
# level6
挺麻烦的一个鸡儿题
```
bandit5@bandit:~/inhere$ cd maybehere07
bandit5@bandit:~/inhere/maybehere07$ ll
total 56
drwxr-x---  2 root bandit5 4096 Apr 23 18:04 ./
drwxr-x--- 22 root bandit5 4096 Apr 23 18:04 ../
-rwxr-x---  1 root bandit5 3663 Apr 23 18:04 -file1*
-rwxr-x---  1 root bandit5 3065 Apr 23 18:04 .file1*
-rw-r-----  1 root bandit5 2488 Apr 23 18:04 -file2
-rw-r-----  1 root bandit5 1033 Apr 23 18:04 .file2
-rwxr-x---  1 root bandit5 3362 Apr 23 18:04 -file3*
-rwxr-x---  1 root bandit5 1997 Apr 23 18:04 .file3*
-rwxr-x---  1 root bandit5 4130 Apr 23 18:04 spaces file1*
-rw-r-----  1 root bandit5 9064 Apr 23 18:04 spaces file2
-rwxr-x---  1 root bandit5 1022 Apr 23 18:04 spaces file3*
bandit5@bandit:~/inhere/maybehere07$ cat .file2
P4L4vucdmLnm8I7Vl7jG1ApGSfjYKqJU
```
这里需要知道ll输出的这一大堆都是啥玩意儿，rwx分别代表可读可写可执行，剩下的看文档吧。
# level7
要使用find了
```
# 我cd到根目录也没怎么发现，因此直接find搜索了，还挺快的，按理说linux自带这些破玩意儿不该这么快的。。。
bandit6@bandit:/$ find / -type f -size 33c -user bandit7 -group bandit6 2>/dev/null
/var/lib/dpkg/info/bandit7.password
bandit6@bandit:/$ cat /var/lib/dpkg/info/bandit7.password
z7WtoNQU2XfjmMtWA8u5rN4vzqu4v99S
```
那个斜杠是指定为根目录，然后就是大小、用户、组，最后有一个标准错误重定向到黑洞，不写也没事儿，我习惯了
# level8
这个就是grep
```
bandit7@bandit:~$ find / -type f -name "data.txt" -exec grep -l "million" {} \; 2>/dev/null
/home/bandit7/data.txt
bandit7@bandit:~$ grep "millionth" data.txt
millionth	TESKZC0XvTetK0S9xNwm25STk5iWrBvP
```
其实另一个办法是打开文件然后用vim的搜索，我试了试也挺快的
# level9
用一下sort即可
```
bandit8@bandit:~$ ll
total 56
drwxr-xr-x  2 root    root     4096 Apr 23 18:04 ./
drwxr-xr-x 70 root    root     4096 Apr 23 18:05 ../
-rw-r--r--  1 root    root      220 Jan  6  2022 .bash_logout
-rw-r--r--  1 root    root     3771 Jan  6  2022 .bashrc
-rw-r-----  1 bandit9 bandit8 33033 Apr 23 18:04 data.txt
-rw-r--r--  1 root    root      807 Jan  6  2022 .profile
bandit8@bandit:~$ sort data.txt | uniq -c | sort -n | head -n1
      1 EN632PlfYiZbn3PhVK3XOGSlNInNE00t
bandit8@bandit:~$
```

# level10
好像是正则，我不太会，草草写了些
```
bandit9@bandit:~$ strings data.txt | grep -oE "==.*"
========== the#
========== password
========== is
========== G7w8LIi6J3kTb8A7j9LgrywtEUlyyp6s
bandit9@bandit:~$
```
# level11
base64解码
```
bandit10@bandit:~$ cat data.txt | base64 -d
The password is 6zPeziLdR2RKNdNYFNb6nVCKzphlXHBM
bandit10@bandit:~$
```
# level12
使用tr

*万幸查了一下，差点儿写个脚本。。。*
```
bandit11@bandit:~$ cat data.txt | tr 'a-zA-Z' 'n-za-mN-ZA-M'
The password is JVNBBFSmZwKKOP0XbFXOoW8chDz5yVRv
```
# level13
有点儿复杂啊，问的chatgpt然后才会的
```
# 先mkdir然后cp
bandit12@bandit:~$ cd /tmp/myname123
bandit12@bandit:/tmp/myname123$ xxd -r /tmp/myname123/data.txt > /tmp/myname123/data.bin
bandit12@bandit:/tmp/myname123$ file /tmp/myname123/data.bin
/tmp/myname123/data.bin: gzip compressed data, was "data2.bin", last modified: Sun Apr 23 18:04:23 2023, max compression, from Unix, original size modulo 2^32 581
bandit12@bandit:/tmp/myname123$ gzip -d -S .bin /tmp/myname123/data.bin
bandit12@bandit:/tmp/myname123$ ll
total 10628
drwxrwxr-x    2 bandit12 bandit12     4096 Jul 17 03:01 ./
drwxrwx-wt 3791 root     root     10801152 Jul 17 03:03 ../
-rw-rw-r--    1 bandit12 bandit12        0 Jul 17 02:39 bandit
-rw-rw-r--    1 bandit12 bandit12      581 Jul 17 02:59 data
-rw-rw-r--    1 bandit12 bandit12    20480 Jul 16 19:05 data5.tar
-rw-r--r--    1 bandit12 bandit12    10240 Apr 23 18:04 data6.tar
-rw-r--r--    1 bandit12 bandit12    10240 Apr 23 18:04 data8.tar
-rw-r--r--    1 bandit12 bandit12       49 Apr 23 18:04 data9
-rw-rw-r--    1 bandit12 bandit12      581 Jul 16 15:25 data.bz2
-rw-r-----    1 bandit12 bandit12     2642 Jul 16 19:00 data.hex
-rw-r-----    1 bandit12 bandit12     2642 Jul 17 02:50 data.txt
-rw-r-----    1 bandit12 bandit12     2642 Jul 17 02:34 mydata.txt
bandit12@bandit:/tmp/myname123$ cat data9
The password is wbWdlBxEir4CaE8LaPhauuOo6pwRmrDw
bandit12@bandit:/tmp/myname123$
```
# level14
水，用私钥登录
```
bandit13@bandit:~$ ssh -i sshkey.private bandit14@localhost -p 2220
The authenticity of host '[localhost]:2220 ([127.0.0.1]:2220)' can't be established.
ED25519 key fingerprint is SHA256:C2ihUBV7ihnV1wUXRb4RrEcLfXC5CXlhmAAM/urerLY.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Could not create directory '/home/bandit13/.ssh' (Permission denied).
Failed to add the host to the list of known hosts (/home/bandit13/.ssh/known_hosts).
                         _                     _ _ _
                        | |__   __ _ _ __   __| (_) |_
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_
                        |_.__/ \__,_|_| |_|\__,_|_|\__|


                      This is an OverTheWire game server.
            More information on http://www.overthewire.org/wargames

!!! You are trying to log into this SSH server with a password on port 2220 from localhost.
!!! Connecting from localhost is blocked to conserve resources.
!!! Please log out and log in again.


      ,----..            ,----,          .---.
     /   /   \         ,/   .`|         /. ./|
    /   .     :      ,`   .'  :     .--'.  ' ;
   .   /   ;.  \   ;    ;     /    /__./ \ : |
  .   ;   /  ` ; .'___,/    ,' .--'.  '   \' .
  ;   |  ; \ ; | |    :     | /___/ \ |    ' '
  |   :  | ; | ' ;    |.';  ; ;   \  \;      :
  .   |  ' ' ' : `----'  |  |  \   ;  `      |
  '   ;  \; /  |     '   :  ;   .   \    .\  ;
   \   \  ',  /      |   |  '    \   \   ' \ |
    ;   :    /       '   :  |     :   '  |--"
     \   \ .'        ;   |.'       \   \ ;
  www. `---` ver     '---' he       '---" ire.org


Welcome to OverTheWire!

If you find any problems, please report them to the #wargames channel on
discord or IRC.

--[ Playing the games ]--

  This machine might hold several wargames.
  If you are playing "somegame", then:

    * USERNAMES are somegame0, somegame1, ...
    * Most LEVELS are stored in /somegame/.
    * PASSWORDS for each level are stored in /etc/somegame_pass/.

  Write-access to homedirectories is disabled. It is advised to create a
  working directory with a hard-to-guess name in /tmp/.  You can use the
  command "mktemp -d" in order to generate a random and hard to guess
  directory in /tmp/.  Read-access to both /tmp/ is disabled and to /proc
  restricted so that users cannot snoop on eachother. Files and directories
  with easily guessable or short names will be periodically deleted! The /tmp
  directory is regularly wiped.
  Please play nice:

    * don't leave orphan processes running
    * don't leave exploit-files laying around
    * don't annoy other players
    * don't post passwords or spoilers
    * again, DONT POST SPOILERS!
      This includes writeups of your solution on your blog or website!

--[ Tips ]--

  This machine has a 64bit processor and many security-features enabled
  by default, although ASLR has been switched off.  The following
  compiler flags might be interesting:

    -m32                    compile for 32bit
    -fno-stack-protector    disable ProPolice
    -Wl,-z,norelro          disable relro

  In addition, the execstack tool can be used to flag the stack as
  executable on ELF binaries.

  Finally, network-access is limited for most levels by a local
  firewall.

--[ Tools ]--

 For your convenience we have installed a few useful tools which you can find
 in the following locations:

    * gef (https://github.com/hugsy/gef) in /opt/gef/
    * pwndbg (https://github.com/pwndbg/pwndbg) in /opt/pwndbg/
    * peda (https://github.com/longld/peda.git) in /opt/peda/
    * gdbinit (https://github.com/gdbinit/Gdbinit) in /opt/gdbinit/
    * pwntools (https://github.com/Gallopsled/pwntools)
    * radare2 (http://www.radare.org/)

 Both python2 and python3 are installed.

--[ More information ]--

  For more information regarding individual wargames, visit
  http://www.overthewire.org/wargames/

  For support, questions or comments, contact us on discord or IRC.

  Enjoy your stay!

bandit14@bandit:~$
```
# level15
nc这个命令在复杂情况下需要自己写http请求的内容，挺离谱的，还是curl和python方便

一些学习的链接[https://juejin.cn/post/6995203632387866631](https://juejin.cn/post/6995203632387866631)、[https://www.runoob.com/linux/linux-comm-nc.html](https://www.runoob.com/linux/linux-comm-nc.html)，更多内容可以参考CSE365 sp23的`talking web`模块。
```
bandit14@bandit:/etc/bandit_pass$ cat bandit14
fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq
bandit14@bandit:/etc/bandit_pass$ cat bandit14 | nc localhost 30000
Correct!
jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt

bandit14@bandit:/etc/bandit_pass$
```
# level16
```
bandit14@bandit:echo "jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt" | openssl s_client -connect localhost:30001 -ign_eof
Correct!
JQttfApK4SeyHwDlI9SXGR50qclOAil1

closed
```
# level17
```
bandit16@bandit:~$ nmap -sV localhost -T5 -p 31000-32000
Starting Nmap 7.80 ( https://nmap.org ) at 2023-07-17 04:20 UTC
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00015s latency).
Not shown: 996 closed ports
PORT      STATE SERVICE     VERSION
31046/tcp open  echo
31518/tcp open  ssl/echo
31691/tcp open  echo
31790/tcp open  ssl/unknown
31960/tcp open  echo
1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at https://nmap.org/cgi-bin/submit.cgi?new-service :
SF-Port31790-TCP:V=7.80%T=SSL%I=7%D=7/17%Time=64B4C185%P=x86_64-pc-linux-g
SF:nu%r(GenericLines,31,"Wrong!\x20Please\x20enter\x20the\x20correct\x20cu
SF:rrent\x20password\n")%r(GetRequest,31,"Wrong!\x20Please\x20enter\x20the
SF:\x20correct\x20current\x20password\n")%r(HTTPOptions,31,"Wrong!\x20Plea
SF:se\x20enter\x20the\x20correct\x20current\x20password\n")%r(RTSPRequest,
SF:31,"Wrong!\x20Please\x20enter\x20the\x20correct\x20current\x20password\
SF:n")%r(Help,31,"Wrong!\x20Please\x20enter\x20the\x20correct\x20current\x
SF:20password\n")%r(SSLSessionReq,31,"Wrong!\x20Please\x20enter\x20the\x20
SF:correct\x20current\x20password\n")%r(TerminalServerCookie,31,"Wrong!\x2
SF:0Please\x20enter\x20the\x20correct\x20current\x20password\n")%r(TLSSess
SF:ionReq,31,"Wrong!\x20Please\x20enter\x20the\x20correct\x20current\x20pa
SF:ssword\n")%r(Kerberos,31,"Wrong!\x20Please\x20enter\x20the\x20correct\x
SF:20current\x20password\n")%r(FourOhFourRequest,31,"Wrong!\x20Please\x20e
SF:nter\x20the\x20correct\x20current\x20password\n")%r(LPDString,31,"Wrong
SF:!\x20Please\x20enter\x20the\x20correct\x20current\x20password\n")%r(LDA
SF:PSearchReq,31,"Wrong!\x20Please\x20enter\x20the\x20correct\x20current\x
SF:20password\n")%r(SIPOptions,31,"Wrong!\x20Please\x20enter\x20the\x20cor
SF:rect\x20current\x20password\n");

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 98.85 seconds
```
然后，要输入16的密码
```
bandit16@bandit:~$ openssl s_client -connect localhost:31790 -ign_eof
CONNECTED(00000003)
Can't use SSL_get_servername
depth=0 CN = localhost
verify error:num=18:self-signed certificate
verify return:1
depth=0 CN = localhost
verify error:num=10:certificate has expired
notAfter=Jul 17 03:32:59 2023 GMT
verify return:1
depth=0 CN = localhost
notAfter=Jul 17 03:32:59 2023 GMT
verify return:1
---
Certificate chain
 0 s:CN = localhost
   i:CN = localhost
   a:PKEY: rsaEncryption, 2048 (bit); sigalg: RSA-SHA1
   v:NotBefore: Jul 17 03:31:59 2023 GMT; NotAfter: Jul 17 03:32:59 2023 GMT
---
Server certificate
-----BEGIN CERTIFICATE-----
MIIDCzCCAfOgAwIBAgIEasML0jANBgkqhkiG9w0BAQUFADAUMRIwEAYDVQQDDAls
b2NhbGhvc3QwHhcNMjMwNzE3MDMzMTU5WhcNMjMwNzE3MDMzMjU5WjAUMRIwEAYD
VQQDDAlsb2NhbGhvc3QwggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEKAoIBAQDQ
WpK5aICLya01rGDXaLVwQpZqWmn75BPH3O2vrqMAu14iXbKtemseBnOaB3vSfu04
QNfWLYWKrnab4hd73/TOurIHq33MnsH8Yb+lzx6VfBq/FouTviT2QBE5cVlvQV63
QPjJZ4mBomudPpDXLfbHWxsH8BYxa6lSqBjs8EqOnfEL9SRoQ+H0w66NjpOnGtLO
l0oYAbmriOkmOht1tr1hoxiacNZa9WEOq01SNrIRGbhOPw07c7/rVXfz9dDBrhPQ
D7FpX/UDyZvJFM3I+sTpwoUj7Ypzvhim+kVY9lGRnzuy439yGovgURCiNwlXUpDA
/Kr/hRCriC3URJT4mWKdAgMBAAGjZTBjMBQGA1UdEQQNMAuCCWxvY2FsaG9zdDBL
BglghkgBhvhCAQ0EPhY8QXV0b21hdGljYWxseSBnZW5lcmF0ZWQgYnkgTmNhdC4g
U2VlIGh0dHBzOi8vbm1hcC5vcmcvbmNhdC8uMA0GCSqGSIb3DQEBBQUAA4IBAQBy
qV/aRIcHHbKSksYqANDBrkLgfXKXKeXMZBTBq3Q4rMLF/ux7tGU+2/YPAo/6L0IZ
2/UGcW+/msmgvBE3+j5FnIB/aoqp2M8fksOiaC8OrsJ6bbShEEV+q5VITosF/Nw0
qrpoXa+7l5IF/8tuTCpi4ZQGHX+uoRgufcGkK3c8Gxsb9Xtroz8se7yLU0VKLm4d
/H0Ozu4QkVTaQ+7971pXYHyip3tKuJbCeJOJledvqGvvcaIvE9S1vxEugQUq2K6u
DZfCLU3TR9l29QonH13HtF5mEDNE4KaMtYxM4B4Mo3KMUHVf4hi4nKJVpjs/FSiI
Vpv3P9pqfmYjEQjp7yIz
-----END CERTIFICATE-----
subject=CN = localhost
issuer=CN = localhost
---
No client certificate CA names sent
Peer signing digest: SHA256
Peer signature type: RSA-PSS
Server Temp Key: X25519, 253 bits
---
SSL handshake has read 1339 bytes and written 373 bytes
Verification error: certificate has expired
---
New, TLSv1.3, Cipher is TLS_AES_256_GCM_SHA384
Server public key is 2048 bit
Secure Renegotiation IS NOT supported
Compression: NONE
Expansion: NONE
No ALPN negotiated
Early data was not sent
Verify return code: 10 (certificate has expired)
---
---
Post-Handshake New Session Ticket arrived:
SSL-Session:
    Protocol  : TLSv1.3
    Cipher    : TLS_AES_256_GCM_SHA384
    Session-ID: AD5693D41623D8997CC2EE94B1CC7C61F949EFBC34B80DC8421E8B82C6572B65
    Session-ID-ctx:
    Resumption PSK: AFE5847E9831517B3B0BCF4B511501803A902004393C9D3D926CA22524CCE716B6A771D7802C706EF3C94E8C264D4B95
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 7200 (seconds)
    TLS session ticket:
    0000 - a5 d8 4b ca c0 ad 23 28-64 e1 24 b6 18 97 bf 19   ..K...#(d.$.....
    0010 - c4 53 bd cd 78 c9 dd 28-f5 14 4c 9d 30 a0 18 97   .S..x..(..L.0...
    0020 - 5d d6 5b 92 2f 96 7a 0e-ac e2 49 bc e3 d1 a6 79   ].[./.z...I....y
    0030 - 73 37 ea 00 c4 4f 0a 07-4c 4e b9 f8 f4 fe 04 bd   s7...O..LN......
    0040 - cb a9 f5 31 28 a1 b9 07-fd cb 83 8b 8d 93 b8 7f   ...1(...........
    0050 - 51 10 1a b9 7c 4e 10 ab-4b 93 8c c7 88 9f 6e 85   Q...|N..K.....n.
    0060 - 87 e8 fc bc 3d f7 93 f0-2f 55 1d cf 64 80 7c 08   ....=.../U..d.|.
    0070 - f2 1c 95 b9 d1 3f 15 90-57 e1 b1 9e 93 87 1d 72   .....?..W......r
    0080 - 93 ed 83 b8 4b ef d2 bd-1d f5 ca 1b f9 d6 7a ff   ....K.........z.
    0090 - 13 fd 8f 40 43 fe 97 99-2a fa eb f9 52 ad b0 27   ...@C...*...R..'
    00a0 - be 2a a0 5c a7 fd 76 6a-22 58 a4 56 02 e7 f2 13   .*.\..vj"X.V....
    00b0 - 4b 01 58 44 ab 63 3d 3d-fa 7e f7 ac 66 8c ef da   K.XD.c==.~..f...
    00c0 - 79 db d0 58 9f c1 fe 8c-3f 95 19 ed a6 f6 08 e8   y..X....?.......

    Start Time: 1689568148
    Timeout   : 7200 (sec)
    Verify return code: 10 (certificate has expired)
    Extended master secret: no
    Max Early Data: 0
---
read R BLOCK
---
Post-Handshake New Session Ticket arrived:
SSL-Session:
    Protocol  : TLSv1.3
    Cipher    : TLS_AES_256_GCM_SHA384
    Session-ID: 731D8DE5B4509BB39289FED6CED817A731462808EFAF8C604A5BEE6E85CD12AB
    Session-ID-ctx:
    Resumption PSK: F18769CA70C1B23B9CAFAD3D8682E406B83AF8FC439A378D79ABBB19CD4B59EE837D9121AB1BA7FCCF1F761FA4AFB8F7
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 7200 (seconds)
    TLS session ticket:
    0000 - a5 d8 4b ca c0 ad 23 28-64 e1 24 b6 18 97 bf 19   ..K...#(d.$.....
    0010 - 23 10 a4 f3 c5 e4 25 65-c5 73 a7 ce d3 1b 98 bf   #.....%e.s......
    0020 - 1a 41 ff b2 2e 44 0f c6-a2 7c a6 12 0c 22 7a a9   .A...D...|..."z.
    0030 - 28 d6 09 17 d2 7a 97 5b-a3 37 fc 5c de 86 24 47   (....z.[.7.\..$G
    0040 - 78 20 db 23 15 d1 3d 77-19 b2 91 dc c7 43 d6 66   x .#..=w.....C.f
    0050 - 3c 04 a7 dd b9 32 e6 0f-16 a1 ab dd 92 99 18 e7   <....2..........
    0060 - 23 ad ab 79 3e af 2d ca-ea 4e 29 67 27 39 d2 d4   #..y>.-..N)g'9..
    0070 - e9 6f e0 5b be 0d d4 2d-07 e2 83 10 4a aa 94 20   .o.[...-....J..
    0080 - 1e 06 3d 42 df 74 91 99-43 cc bc ca 5c 59 74 f1   ..=B.t..C...\Yt.
    0090 - df 00 c4 16 44 2d a1 0f-db db 65 84 3b 89 58 b4   ....D-....e.;.X.
    00a0 - 81 71 91 ec 5c 5e a3 db-51 25 b4 37 e5 0d 6b 41   .q..\^..Q%.7..kA
    00b0 - 88 a8 dc 9d b3 02 5b 68-04 4c 01 cd cd a3 17 24   ......[h.L.....$
    00c0 - 4a fe f5 03 49 ab 60 1e-b3 eb 07 04 92 c5 ff ab   J...I.`.........

    Start Time: 1689568148
    Timeout   : 7200 (sec)
    Verify return code: 10 (certificate has expired)
    Extended master secret: no
    Max Early Data: 0
---
read R BLOCK

Wrong! Please enter the correct current password
closed
```
是从这里看出来要输入密码的！
```
bandit16@bandit:~$ openssl s_client -connect localhost:31790 -ign_eof
CONNECTED(00000003)
Can't use SSL_get_servername
depth=0 CN = localhost
verify error:num=18:self-signed certificate
verify return:1
depth=0 CN = localhost
verify error:num=10:certificate has expired
notAfter=Jul 17 03:32:59 2023 GMT
verify return:1
depth=0 CN = localhost
notAfter=Jul 17 03:32:59 2023 GMT
verify return:1
---
Certificate chain
 0 s:CN = localhost
   i:CN = localhost
   a:PKEY: rsaEncryption, 2048 (bit); sigalg: RSA-SHA1
   v:NotBefore: Jul 17 03:31:59 2023 GMT; NotAfter: Jul 17 03:32:59 2023 GMT
---
Server certificate
-----BEGIN CERTIFICATE-----
MIIDCzCCAfOgAwIBAgIEasML0jANBgkqhkiG9w0BAQUFADAUMRIwEAYDVQQDDAls
b2NhbGhvc3QwHhcNMjMwNzE3MDMzMTU5WhcNMjMwNzE3MDMzMjU5WjAUMRIwEAYD
VQQDDAlsb2NhbGhvc3QwggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEKAoIBAQDQ
WpK5aICLya01rGDXaLVwQpZqWmn75BPH3O2vrqMAu14iXbKtemseBnOaB3vSfu04
QNfWLYWKrnab4hd73/TOurIHq33MnsH8Yb+lzx6VfBq/FouTviT2QBE5cVlvQV63
QPjJZ4mBomudPpDXLfbHWxsH8BYxa6lSqBjs8EqOnfEL9SRoQ+H0w66NjpOnGtLO
l0oYAbmriOkmOht1tr1hoxiacNZa9WEOq01SNrIRGbhOPw07c7/rVXfz9dDBrhPQ
D7FpX/UDyZvJFM3I+sTpwoUj7Ypzvhim+kVY9lGRnzuy439yGovgURCiNwlXUpDA
/Kr/hRCriC3URJT4mWKdAgMBAAGjZTBjMBQGA1UdEQQNMAuCCWxvY2FsaG9zdDBL
BglghkgBhvhCAQ0EPhY8QXV0b21hdGljYWxseSBnZW5lcmF0ZWQgYnkgTmNhdC4g
U2VlIGh0dHBzOi8vbm1hcC5vcmcvbmNhdC8uMA0GCSqGSIb3DQEBBQUAA4IBAQBy
qV/aRIcHHbKSksYqANDBrkLgfXKXKeXMZBTBq3Q4rMLF/ux7tGU+2/YPAo/6L0IZ
2/UGcW+/msmgvBE3+j5FnIB/aoqp2M8fksOiaC8OrsJ6bbShEEV+q5VITosF/Nw0
qrpoXa+7l5IF/8tuTCpi4ZQGHX+uoRgufcGkK3c8Gxsb9Xtroz8se7yLU0VKLm4d
/H0Ozu4QkVTaQ+7971pXYHyip3tKuJbCeJOJledvqGvvcaIvE9S1vxEugQUq2K6u
DZfCLU3TR9l29QonH13HtF5mEDNE4KaMtYxM4B4Mo3KMUHVf4hi4nKJVpjs/FSiI
Vpv3P9pqfmYjEQjp7yIz
-----END CERTIFICATE-----
subject=CN = localhost
issuer=CN = localhost
---
No client certificate CA names sent
Peer signing digest: SHA256
Peer signature type: RSA-PSS
Server Temp Key: X25519, 253 bits
---
SSL handshake has read 1339 bytes and written 373 bytes
Verification error: certificate has expired
---
New, TLSv1.3, Cipher is TLS_AES_256_GCM_SHA384
Server public key is 2048 bit
Secure Renegotiation IS NOT supported
Compression: NONE
Expansion: NONE
No ALPN negotiated
Early data was not sent
Verify return code: 10 (certificate has expired)
---
---
Post-Handshake New Session Ticket arrived:
SSL-Session:
    Protocol  : TLSv1.3
    Cipher    : TLS_AES_256_GCM_SHA384
    Session-ID: 1B8DD2D7E7B861C8494FB2E901FEB50552571BFE7200C45C57EEACE66795AEEA
    Session-ID-ctx:
    Resumption PSK: 25F7290250EB5F41F5C184E597BD8493DFD4EC4E8965B10CE6A409D2909B370F30DB9A1E965F680CCD6F9C9E3BC4D0C6
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 7200 (seconds)
    TLS session ticket:
    0000 - a5 d8 4b ca c0 ad 23 28-64 e1 24 b6 18 97 bf 19   ..K...#(d.$.....
    0010 - a1 6b 8c 90 89 4b 8b e8-df 1e 82 05 28 ad a8 5f   .k...K......(.._
    0020 - 65 f3 03 76 14 8f d5 97-8a a5 28 ea 20 2f 06 55   e..v......(. /.U
    0030 - 16 ba 4b 88 de ab 7e 00-1c 76 ba 08 b1 e7 0f a9   ..K...~..v......
    0040 - 1d 53 2a 31 16 6b 02 0d-2e dd e7 9a f4 9a e8 13   .S*1.k..........
    0050 - 13 a1 20 67 4c 24 07 53-18 c1 68 56 30 f4 92 c3   .. gL$.S..hV0...
    0060 - b5 5b a6 4d 99 ff 16 fd-30 72 9b 0e f7 f2 c6 ab   .[.M....0r......
    0070 - 69 c1 c0 b9 16 18 3d 5c-c4 db 4f b9 06 bf 6c 6f   i.....=\..O...lo
    0080 - 51 c4 99 60 fa 03 55 af-ad 46 ed e1 53 0f 92 65   Q..`..U..F..S..e
    0090 - 57 82 b9 5b ce 5b 40 37-4f d5 a8 a3 27 63 b9 2d   W..[.[@7O...'c.-
    00a0 - 6b e4 ea 11 f2 9f c3 f7-82 3d 16 4e 2b 40 d3 25   k........=.N+@.%
    00b0 - 50 10 0f aa 74 30 49 da-c8 01 32 23 c0 b7 3c 8b   P...t0I...2#..<.
    00c0 - 97 8d 24 10 2d 93 73 04-33 01 d9 70 92 26 4e fc   ..$.-.s.3..p.&N.

    Start Time: 1689568162
    Timeout   : 7200 (sec)
    Verify return code: 10 (certificate has expired)
    Extended master secret: no
    Max Early Data: 0
---
read R BLOCK
---
Post-Handshake New Session Ticket arrived:
SSL-Session:
    Protocol  : TLSv1.3
    Cipher    : TLS_AES_256_GCM_SHA384
    Session-ID: A0EF32E17C1AC0960FD46EE50181836B83644B2168CDC3087A3612EC77D9A111
    Session-ID-ctx:
    Resumption PSK: 117786B647299C2A691BD342EDC8E39A7899490BE868D804415203AED03876A67C51CE8E55D236DAC96130391C36759A
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 7200 (seconds)
    TLS session ticket:
    0000 - a5 d8 4b ca c0 ad 23 28-64 e1 24 b6 18 97 bf 19   ..K...#(d.$.....
    0010 - f3 b6 fd 9d 6e e3 35 98-ad 1d df 9e 75 38 c5 47   ....n.5.....u8.G
    0020 - 15 7a c4 8f 31 3b 39 1e-ef 1c f2 56 f2 61 48 a9   .z..1;9....V.aH.
    0030 - 36 ae 3d 66 e9 0d 0f ff-07 39 33 77 d7 87 8c 63   6.=f.....93w...c
    0040 - fb 00 ab 1e 27 3a 91 ed-24 49 b6 e2 9d 49 a6 2b   ....':..$I...I.+
    0050 - 90 ce a6 8b ea 1c bd f5-38 77 83 fc 9b 4c b4 49   ........8w...L.I
    0060 - 3b d9 7c bb 52 0b 2d 38-88 a5 80 b0 8e 80 5d 66   ;.|.R.-8......]f
    0070 - 1e 0b 9d 10 b2 81 11 51-0a 30 60 ec b9 2d d2 5e   .......Q.0`..-.^
    0080 - 64 66 87 44 84 78 f8 e5-2b 62 cb 5f 84 aa 50 01   df.D.x..+b._..P.
    0090 - 5d d6 62 fd e8 8b f8 fc-91 0c 8a f9 a7 12 6e ae   ].b...........n.
    00a0 - b9 40 f2 4f 90 01 0e 30-cf bf 16 3a b5 96 fc 3a   .@.O...0...:...:
    00b0 - 9b a5 e0 4a 54 df eb 39-68 be 05 77 6b 50 d7 a3   ...JT..9h..wkP..
    00c0 - 87 0e 7d bf 33 1a 9e 31-40 b6 3e 5e 1f a9 cf d6   ..}.3..1@.>^....

    Start Time: 1689568162
    Timeout   : 7200 (sec)
    Verify return code: 10 (certificate has expired)
    Extended master secret: no
    Max Early Data: 0
---
read R BLOCK
JQttfApK4SeyHwDlI9SXGR50qclOAil1
Correct!
-----BEGIN RSA PRIVATE KEY-----
MIIEogIBAAKCAQEAvmOkuifmMg6HL2YPIOjon6iWfbp7c3jx34YkYWqUH57SUdyJ
imZzeyGC0gtZPGujUSxiJSWI/oTqexh+cAMTSMlOJf7+BrJObArnxd9Y7YT2bRPQ
Ja6Lzb558YW3FZl87ORiO+rW4LCDCNd2lUvLE/GL2GWyuKN0K5iCd5TbtJzEkQTu
DSt2mcNn4rhAL+JFr56o4T6z8WWAW18BR6yGrMq7Q/kALHYW3OekePQAzL0VUYbW
JGTi65CxbCnzc/w4+mqQyvmzpWtMAzJTzAzQxNbkR2MBGySxDLrjg0LWN6sK7wNX
x0YVztz/zbIkPjfkU1jHS+9EbVNj+D1XFOJuaQIDAQABAoIBABagpxpM1aoLWfvD
KHcj10nqcoBc4oE11aFYQwik7xfW+24pRNuDE6SFthOar69jp5RlLwD1NhPx3iBl
J9nOM8OJ0VToum43UOS8YxF8WwhXriYGnc1sskbwpXOUDc9uX4+UESzH22P29ovd
d8WErY0gPxun8pbJLmxkAtWNhpMvfe0050vk9TL5wqbu9AlbssgTcCXkMQnPw9nC
YNN6DDP2lbcBrvgT9YCNL6C+ZKufD52yOQ9qOkwFTEQpjtF4uNtJom+asvlpmS8A
vLY9r60wYSvmZhNqBUrj7lyCtXMIu1kkd4w7F77k+DjHoAXyxcUp1DGL51sOmama
+TOWWgECgYEA8JtPxP0GRJ+IQkX262jM3dEIkza8ky5moIwUqYdsx0NxHgRRhORT
8c8hAuRBb2G82so8vUHk/fur85OEfc9TncnCY2crpoqsghifKLxrLgtT+qDpfZnx
SatLdt8GfQ85yA7hnWWJ2MxF3NaeSDm75Lsm+tBbAiyc9P2jGRNtMSkCgYEAypHd
HCctNi/FwjulhttFx/rHYKhLidZDFYeiE/v45bN4yFm8x7R/b0iE7KaszX+Exdvt
SghaTdcG0Knyw1bpJVyusavPzpaJMjdJ6tcFhVAbAjm7enCIvGCSx+X3l5SiWg0A
R57hJglezIiVjv3aGwHwvlZvtszK6zV6oXFAu0ECgYAbjo46T4hyP5tJi93V5HDi
Ttiek7xRVxUl+iU7rWkGAXFpMLFteQEsRr7PJ/lemmEY5eTDAFMLy9FL2m9oQWCg
R8VdwSk8r9FGLS+9aKcV5PI/WEKlwgXinB3OhYimtiG2Cg5JCqIZFHxD6MjEGOiu
L8ktHMPvodBwNsSBULpG0QKBgBAplTfC1HOnWiMGOU3KPwYWt0O6CdTkmJOmL8Ni
blh9elyZ9FsGxsgtRBXRsqXuz7wtsQAgLHxbdLq/ZJQ7YfzOKU4ZxEnabvXnvWkU
YOdjHdSOoKvDQNWu6ucyLRAWFuISeXw9a/9p7ftpxm0TSgyvmfLF2MIAEwyzRqaM
77pBAoGAMmjmIJdjp+Ez8duyn3ieo36yrttF5NSsJLAbxFpdlc1gvtGCWW+9Cq0b
dxviW8+TFVEBl1O4f7HVm6EpTscdDxU+bCXWkfjuRb7Dy9GOtt9JPsX8MBTakzh3
vBgsyi/sN3RqRBcGU40fOoZyfAMT8s1m/uYv52O6IgeuZ/ujbjY=
-----END RSA PRIVATE KEY-----

closed
```
返回了正确的密钥，然后写入/tmp下的某个文件，然后给它只有自己可读可写即可
```
# 首先需要在tmp下新建一个文件夹，然后把密钥写进去，然后chmod 666那个文件
bandit16@bandit:/tmp/a$ ssh -i 1.private bandit17@localhost -p 2220
--[ More information ]--

  For more information regarding individual wargames, visit
  http://www.overthewire.org/wargames/

  For support, questions or comments, contact us on discord or IRC.

  Enjoy your stay!

bandit17@bandit:~$
```
# level18
直接diff
```
bandit17@bandit:~$ diff passwords.old passwords.new
42c42
< glZreTEH1V3cGKL6g4conYqZqaEj0mte
---
> hga5tuuCLF6fFzUpnagiMN8ssu9LFrdg
bandit17@bandit:~$
```
然后登录，然后就是：
```
┌─[myc@ubuntu22]─[~]
└──╼[13:02:46]$ ssh bandit18@bandit.labs.overthewire.org -p 2220
                         _                     _ _ _
                        | |__   __ _ _ __   __| (_) |_
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_
                        |_.__/ \__,_|_| |_|\__,_|_|\__|


                      This is an OverTheWire game server.
            More information on http://www.overthewire.org/wargames

bandit18@bandit.labs.overthewire.org's password:

      ,----..            ,----,          .---.
     /   /   \         ,/   .`|         /. ./|
    /   .     :      ,`   .'  :     .--'.  ' ;
   .   /   ;.  \   ;    ;     /    /__./ \ : |
  .   ;   /  ` ; .'___,/    ,' .--'.  '   \' .
  ;   |  ; \ ; | |    :     | /___/ \ |    ' '
  |   :  | ; | ' ;    |.';  ; ;   \  \;      :
  .   |  ' ' ' : `----'  |  |  \   ;  `      |
  '   ;  \; /  |     '   :  ;   .   \    .\  ;
   \   \  ',  /      |   |  '    \   \   ' \ |
    ;   :    /       '   :  |     :   '  |--"
     \   \ .'        ;   |.'       \   \ ;
  www. `---` ver     '---' he       '---" ire.org


Welcome to OverTheWire!

If you find any problems, please report them to the #wargames channel on
discord or IRC.

--[ Playing the games ]--

  This machine might hold several wargames.
  If you are playing "somegame", then:

    * USERNAMES are somegame0, somegame1, ...
    * Most LEVELS are stored in /somegame/.
    * PASSWORDS for each level are stored in /etc/somegame_pass/.

  Write-access to homedirectories is disabled. It is advised to create a
  working directory with a hard-to-guess name in /tmp/.  You can use the
  command "mktemp -d" in order to generate a random and hard to guess
  directory in /tmp/.  Read-access to both /tmp/ is disabled and to /proc
  restricted so that users cannot snoop on eachother. Files and directories
  with easily guessable or short names will be periodically deleted! The /tmp
  directory is regularly wiped.
  Please play nice:

    * don't leave orphan processes running
    * don't leave exploit-files laying around
    * don't annoy other players
    * don't post passwords or spoilers
    * again, DONT POST SPOILERS!
      This includes writeups of your solution on your blog or website!

--[ Tips ]--

  This machine has a 64bit processor and many security-features enabled
  by default, although ASLR has been switched off.  The following
  compiler flags might be interesting:

    -m32                    compile for 32bit
    -fno-stack-protector    disable ProPolice
    -Wl,-z,norelro          disable relro

  In addition, the execstack tool can be used to flag the stack as
  executable on ELF binaries.

  Finally, network-access is limited for most levels by a local
  firewall.

--[ Tools ]--

 For your convenience we have installed a few useful tools which you can find
 in the following locations:

    * gef (https://github.com/hugsy/gef) in /opt/gef/
    * pwndbg (https://github.com/pwndbg/pwndbg) in /opt/pwndbg/
    * peda (https://github.com/longld/peda.git) in /opt/peda/
    * gdbinit (https://github.com/gdbinit/Gdbinit) in /opt/gdbinit/
    * pwntools (https://github.com/Gallopsled/pwntools)
    * radare2 (http://www.radare.org/)

 Both python2 and python3 are installed.

--[ More information ]--

  For more information regarding individual wargames, visit
  http://www.overthewire.org/wargames/

  For support, questions or comments, contact us on discord or IRC.

  Enjoy your stay!

Byebye !
Connection to bandit.labs.overthewire.org closed.
```
# level19
这个，告诉了你文件名和位置，可以直接读，而不是链接一个bash

因此可以玩儿一个骚操作
```
┌─[Fail][myc@ubuntu22]─[~]
└──╼[13:09:29]$ ssh bandit18@bandit.labs.overthewire.org -p 2220 -t cat readme
                         _                     _ _ _
                        | |__   __ _ _ __   __| (_) |_
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_
                        |_.__/ \__,_|_| |_|\__,_|_|\__|


                      This is an OverTheWire game server.
            More information on http://www.overthewire.org/wargames

bandit18@bandit.labs.overthewire.org's password:
awhqfNnAbc1naukrpqDYcF95h7HoMTrC
Connection to bandit.labs.overthewire.org closed.
```
# level20
就是运行这个小文件
```
bandit19@bandit:~$ ./bandit20-do --help
Usage: env [OPTION]... [-] [NAME=VALUE]... [COMMAND [ARG]...]
Set each NAME to VALUE in the environment and run COMMAND.

Mandatory arguments to long options are mandatory for short options too.
  -i, --ignore-environment  start with an empty environment
  -0, --null           end each output line with NUL, not newline
  -u, --unset=NAME     remove variable from the environment
  -C, --chdir=DIR      change working directory to DIR
  -S, --split-string=S  process and split S into separate arguments;
                        used to pass multiple arguments on shebang lines
      --block-signal[=SIG]    block delivery of SIG signal(s) to COMMAND
      --default-signal[=SIG]  reset handling of SIG signal(s) to the default
      --ignore-signal[=SIG]   set handling of SIG signals(s) to do nothing
      --list-signal-handling  list non default signal handling to stderr
  -v, --debug          print verbose information for each processing step
      --help     display this help and exit
      --version  output version information and exit

A mere - implies -i.  If no COMMAND, print the resulting environment.

SIG may be a signal name like 'PIPE', or a signal number like '13'.
Without SIG, all known signals are included.  Multiple signals can be
comma-separated.

GNU coreutils online help: <https://www.gnu.org/software/coreutils/>
Full documentation <https://www.gnu.org/software/coreutils/env>
or available locally via: info '(coreutils) env invocation'
bandit19@bandit:~$ ./bandit20-do NAME=11020 cat /etc/bandit_pass/bandit20
VxCazJaVykI6W36BkBU0mJTCM8rR95XT
bandit19@bandit:~$
```
# level21
直接看图
![level20-21](image-1.png)
```
NvEJF7oVjkddltPSrdKEFOllh9V1IBcq
```
# level22
就是看守护进程在运行哪个脚本，然后跟着去找。
```
bandit21@bandit:~$ man cron
bandit21@bandit:~$ man crontab
bandit21@bandit:~$ man 5 crontab
bandit21@bandit:~$ cd /etc/cron.d/
bandit21@bandit:/etc/cron.d$ ll
total 56
drwxr-xr-x   2 root root  4096 Apr 23 18:05 ./
drwxr-xr-x 108 root root 12288 Jun 10 22:51 ../
-rw-r--r--   1 root root    62 Apr 23 18:04 cronjob_bandit15_root
-rw-r--r--   1 root root    62 Apr 23 18:04 cronjob_bandit17_root
-rw-r--r--   1 root root   120 Apr 23 18:04 cronjob_bandit22
-rw-r--r--   1 root root   122 Apr 23 18:04 cronjob_bandit23
-rw-r--r--   1 root root   120 Apr 23 18:04 cronjob_bandit24
-rw-r--r--   1 root root    62 Apr 23 18:04 cronjob_bandit25_root
-rw-r--r--   1 root root   201 Jan  8  2022 e2scrub_all
-rwx------   1 root root    52 Apr 23 18:05 otw-tmp-dir*
-rw-r--r--   1 root root   102 Mar 23  2022 .placeholder
-rw-r--r--   1 root root   396 Feb  2  2021 sysstat
bandit21@bandit:/etc/cron.d$ cat cronjob_bandit15_root
* * * * * root /usr/bin/cronjob_bandit15_root.sh &> /dev/null
bandit21@bandit:/etc/cron.d$ cat cronjob_bandit17_root
* * * * * root /usr/bin/cronjob_bandit17_root.sh &> /dev/null
bandit21@bandit:/etc/cron.d$ cat cronjob_bandit22
@reboot bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
* * * * * bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
bandit21@bandit:/etc/cron.d$ cat /usr/bin/cronjob_bandit22.sh
#!/bin/bash
chmod 644 /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
cat /etc/bandit_pass/bandit22 > /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
bandit21@bandit:/etc/cron.d$ cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
WdDozAdTM2z9DiFEQ2mGlwngMfj4EZff
bandit21@bandit:/etc/cron.d$
```
# level23
和上面那个题几乎一样
```
bandit22@bandit:~$ cd /etc/cron.d/
bandit22@bandit:/etc/cron.d$ ll
total 56
drwxr-xr-x   2 root root  4096 Apr 23 18:05 ./
drwxr-xr-x 108 root root 12288 Jun 10 22:51 ../
-rw-r--r--   1 root root    62 Apr 23 18:04 cronjob_bandit15_root
-rw-r--r--   1 root root    62 Apr 23 18:04 cronjob_bandit17_root
-rw-r--r--   1 root root   120 Apr 23 18:04 cronjob_bandit22
-rw-r--r--   1 root root   122 Apr 23 18:04 cronjob_bandit23
-rw-r--r--   1 root root   120 Apr 23 18:04 cronjob_bandit24
-rw-r--r--   1 root root    62 Apr 23 18:04 cronjob_bandit25_root
-rw-r--r--   1 root root   201 Jan  8  2022 e2scrub_all
-rwx------   1 root root    52 Apr 23 18:05 otw-tmp-dir*
-rw-r--r--   1 root root   102 Mar 23  2022 .placeholder
-rw-r--r--   1 root root   396 Feb  2  2021 sysstat
bandit22@bandit:/etc/cron.d$ cat cronjob_bandit23
@reboot bandit23 /usr/bin/cronjob_bandit23.sh  &> /dev/null
* * * * * bandit23 /usr/bin/cronjob_bandit23.sh  &> /dev/null
bandit22@bandit:/etc/cron.d$ cat /usr/bin/cronjob_bandit23.sh
#!/bin/bash

myname=$(whoami)
mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)

echo "Copying passwordfile /etc/bandit_pass/$myname to /tmp/$mytarget"

cat /etc/bandit_pass/$myname > /tmp/$mytarget
bandit22@bandit:/etc/cron.d$
```
拿到脚本以后直接执行一下，不过需要注意用户是bandit23，因为whoami输出的是bandit22
```
bandit22@bandit:/etc/cron.d$ echo I am user bandit23 | md5sum | cut -d ' ' -f 1
8ca319486bfbbc3663ea0fbe81326349
bandit22@bandit:/etc/cron.d$ cat /tmp/8ca319486bfbbc3663ea0fbe81326349
QYw0Y2aiA672PsMmh9puTQuhoz8SyR2G
```
# level24
还是那几步，然后看到了这玩意儿
```
bandit23@bandit:/etc/cron.d$ cat /usr/bin/cronjob_bandit24.sh
#!/bin/bash

myname=$(whoami)

cd /var/spool/$myname/foo || exit 1
echo "Executing and deleting all scripts in /var/spool/$myname/foo:"
for i in * .*;
do
    if [ "$i" != "." -a "$i" != ".." ];
    then
        echo "Handling $i"
        owner="$(stat --format "%U" ./$i)"
        if [ "${owner}" = "bandit23" ]; then
            timeout -s 9 60 ./$i
        fi
        rm -rf ./$i
    fi
done
```

```
bandit23@bandit:/var/spool/bandit24$ ll
total 12
dr-xr-x---  3 bandit24 bandit23 4096 Apr 23 18:04 ./
drwxr-xr-x  5 root     root     4096 Apr 23 18:04 ../
drwxrwx-wx 13 root     bandit24 4096 Jul 17 06:58 foo/
bandit23@bandit:/var/spool/bandit24$
# 这里我根本没有写的权限，题改了？？？？？？？
```
那也简单，就是把脚本放在foo底下

脚本就是一个输出，水的一批
```
#!/bin/bash
cat /etc/bandit_pass/bandit24 >> /tmp/bandit23/pass
```
然后执行脚本就行，最后得到如下结果：
```
VAfGXJ1PBSsPSnvsjI8p759leLZ9GGar
```
# level25
要写爆破脚本
```
bandit24@bandit:~$ nc localhost 30002
I am the pincode checker for user bandit25. Please enter the password for user bandit24 and the secret pincode on a single line, separated by a space.

Fail! You did not supply enough data. Try again.
^C
bandit24@bandit:~$
```
脚本如下：
```
#! /bin/bash
pass24="VAfGXJ1PBSsPSnvsjI8p759leLZ9GGar"
for i in {0..9}{0..9}{0..9}{0..9}
do
    echo $pass24' '$i >> mydict
done
echo "done loop!"
cat ./mydict | nc localhost 30002 >> re
sort re | uniq -u
```
*上边儿有个题貌似应该用-u的，G*

最后得到如下结果：
```
The password of user bandit25 is p7TaowMYrmu23Ol8hiZh9UvD0O9hpx8d
```
# level26
登陆上以后出现如下内容：
```
bandit25@bandit:~$ ll
total 32
drwxr-xr-x  2 root     root     4096 Apr 23 18:04 ./
drwxr-xr-x 70 root     root     4096 Apr 23 18:05 ../
-rw-r-----  1 bandit25 bandit25   33 Apr 23 18:04 .bandit24.password
-r--------  1 bandit25 bandit25 1679 Apr 23 18:04 bandit26.sshkey
-rw-r--r--  1 root     root      220 Jan  6  2022 .bash_logout
-rw-r--r--  1 root     root     3771 Jan  6  2022 .bashrc
-rw-r-----  1 bandit25 bandit25    4 Apr 23 18:04 .pin
-rw-r--r--  1 root     root      807 Jan  6  2022 .profile
bandit25@bandit:~$ ssh -i bandit26.sshkey bandit26@localhost -p 2220
The authenticity of host '[localhost]:2220 ([127.0.0.1]:2220)' can't be established.
ED25519 key fingerprint is SHA256:C2ihUBV7ihnV1wUXRb4RrEcLfXC5CXlhmAAM/urerLY.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Could not create directory '/home/bandit25/.ssh' (Permission denied).
Failed to add the host to the list of known hosts (/home/bandit25/.ssh/known_hosts).
                         _                     _ _ _
                        | |__   __ _ _ __   __| (_) |_
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_
                        |_.__/ \__,_|_| |_|\__,_|_|\__|


                      This is an OverTheWire game server.
            More information on http://www.overthewire.org/wargames

!!! You are trying to log into this SSH server with a password on port 2220 from localhost.
!!! Connecting from localhost is blocked to conserve resources.
!!! Please log out and log in again.


      ,----..            ,----,          .---.
     /   /   \         ,/   .`|         /. ./|
    /   .     :      ,`   .'  :     .--'.  ' ;
   .   /   ;.  \   ;    ;     /    /__./ \ : |
  .   ;   /  ` ; .'___,/    ,' .--'.  '   \' .
  ;   |  ; \ ; | |    :     | /___/ \ |    ' '
  |   :  | ; | ' ;    |.';  ; ;   \  \;      :
  .   |  ' ' ' : `----'  |  |  \   ;  `      |
  '   ;  \; /  |     '   :  ;   .   \    .\  ;
   \   \  ',  /      |   |  '    \   \   ' \ |
    ;   :    /       '   :  |     :   '  |--"
     \   \ .'        ;   |.'       \   \ ;
  www. `---` ver     '---' he       '---" ire.org


Welcome to OverTheWire!

If you find any problems, please report them to the #wargames channel on
discord or IRC.

--[ Playing the games ]--

  This machine might hold several wargames.
  If you are playing "somegame", then:

    * USERNAMES are somegame0, somegame1, ...
    * Most LEVELS are stored in /somegame/.
    * PASSWORDS for each level are stored in /etc/somegame_pass/.

  Write-access to homedirectories is disabled. It is advised to create a
  working directory with a hard-to-guess name in /tmp/.  You can use the
  command "mktemp -d" in order to generate a random and hard to guess
  directory in /tmp/.  Read-access to both /tmp/ is disabled and to /proc
  restricted so that users cannot snoop on eachother. Files and directories
  with easily guessable or short names will be periodically deleted! The /tmp
  directory is regularly wiped.
  Please play nice:

    * don't leave orphan processes running
    * don't leave exploit-files laying around
    * don't annoy other players
    * don't post passwords or spoilers
    * again, DONT POST SPOILERS!
      This includes writeups of your solution on your blog or website!

--[ Tips ]--

  This machine has a 64bit processor and many security-features enabled
  by default, although ASLR has been switched off.  The following
  compiler flags might be interesting:

    -m32                    compile for 32bit
    -fno-stack-protector    disable ProPolice
    -Wl,-z,norelro          disable relro

  In addition, the execstack tool can be used to flag the stack as
  executable on ELF binaries.

  Finally, network-access is limited for most levels by a local
  firewall.

--[ Tools ]--

 For your convenience we have installed a few useful tools which you can find
 in the following locations:

    * gef (https://github.com/hugsy/gef) in /opt/gef/
    * pwndbg (https://github.com/pwndbg/pwndbg) in /opt/pwndbg/
    * peda (https://github.com/longld/peda.git) in /opt/peda/
    * gdbinit (https://github.com/gdbinit/Gdbinit) in /opt/gdbinit/
    * pwntools (https://github.com/Gallopsled/pwntools)
    * radare2 (http://www.radare.org/)

 Both python2 and python3 are installed.

--[ More information ]--

  For more information regarding individual wargames, visit
  http://www.overthewire.org/wargames/

  For support, questions or comments, contact us on discord or IRC.

  Enjoy your stay!

  _                     _ _ _   ___   __
 | |                   | (_) | |__ \ / /
 | |__   __ _ _ __   __| |_| |_   ) / /_
 | '_ \ / _` | '_ \ / _` | | __| / / '_ \
 | |_) | (_| | | | | (_| | | |_ / /| (_) |
 |_.__/ \__,_|_| |_|\__,_|_|\__|____\___/
Connection to localhost closed.
bandit25@bandit:~$
```
这一步需要知道etc/passwd的内容，这里有个[中文博客](https://blog.csdn.net/dearsq/article/details/52586320)
```
bandit25@bandit:~$ cat /etc/passwd | grep "bandit26"
bandit26:x:11026:11026:bandit level 26:/home/bandit26:/usr/bin/showtext
bandit25@bandit:~$ cat /usr/bin/showtext
#!/bin/sh

export TERM=linux

exec more ~/text.txt
exit 0
bandit25@bandit:~$
```
发现使用more展示，这里就可以把窗口缩小，让他一下子展示不完需要翻页即可，然后进入vim模式就可以进行搜索啊、编辑啊之类的事了，就解决了。
```
:r /etc/bandit_pass/bandit26
c7GvcKlw9mC7aUQaPx7nwFstuAIBw1o1
```
# level27
这一题和level26一样，还得缩小terminal，这个不会，看的网上的题解。
```
:set shell sh=/bin/sh
:sh
$ ll
/bin/sh: 1: ll: not found
$ ls -al
total 44
drwxr-xr-x  3 root     root      4096 Apr 23 18:04 .
drwxr-xr-x 70 root     root      4096 Apr 23 18:05 ..
-rw-r--r--  1 root     root       220 Jan  6  2022 .bash_logout
-rw-r--r--  1 root     root      3771 Jan  6  2022 .bashrc
-rw-r--r--  1 root     root       807 Jan  6  2022 .profile
drwxr-xr-x  2 root     root      4096 Apr 23 18:04 .ssh
-rwsr-x---  1 bandit27 bandit26 14876 Apr 23 18:04 bandit27-do
-rw-r-----  1 bandit26 bandit26   258 Apr 23 18:04 text.txt
$ file bandit27-do
bandit27-do: setuid ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked, interpreter /lib/ld-linux.so.2, BuildID[sha1]=c148b21f7eb7e816998f07490c8007567e51953f, for GNU/Linux 3.2.0, not stripped
$ ./bandit27-do
Run a command as another user.
  Example: ./bandit27-do id
$ ./bandit27-do cat /etc/bandit_pass/bandit27
YnQpBuifNMas1hcUFk70ZmqkhUU2EuaS
```
# level28
使用git仓库
```
bandit27@bandit:/tmp/a$ git clone ssh://bandit27-git@localhost:2220/home/bandit27-git/repo
Cloning into 'repo'...
The authenticity of host '[localhost]:2220 ([127.0.0.1]:2220)' can't be established.
ED25519 key fingerprint is SHA256:C2ihUBV7ihnV1wUXRb4RrEcLfXC5CXlhmAAM/urerLY.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Could not create directory '/home/bandit27/.ssh' (Permission denied).
Failed to add the host to the list of known hosts (/home/bandit27/.ssh/known_hosts).
                         _                     _ _ _
                        | |__   __ _ _ __   __| (_) |_
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_
                        |_.__/ \__,_|_| |_|\__,_|_|\__|


                      This is an OverTheWire game server.
            More information on http://www.overthewire.org/wargames

bandit27-git@localhost's password:
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
Receiving objects: 100% (3/3), done.
bandit27@bandit:/tmp/a$ ll
total 10564
drwxrwxr-x   3 bandit27 bandit27     4096 Jul 19 02:08 ./
drwxrwx-wt 317 root     root     10801152 Jul 19 02:08 ../
drwxrwxr-x   3 bandit27 bandit27     4096 Jul 19 02:08 repo/
bandit27@bandit:/tmp/a$ cd repo/
bandit27@bandit:/tmp/a/repo$ ll
total 16
drwxrwxr-x 3 bandit27 bandit27 4096 Jul 19 02:08 ./
drwxrwxr-x 3 bandit27 bandit27 4096 Jul 19 02:08 ../
drwxrwxr-x 8 bandit27 bandit27 4096 Jul 19 02:08 .git/
-rw-rw-r-- 1 bandit27 bandit27   68 Jul 19 02:08 README
bandit27@bandit:/tmp/a/repo$ cat README
The password to the next level is: AVanL161y9rsbcJIsFHuw35rjaOM19nR
bandit27@bandit:/tmp/a/repo$
```
# level29
还是老规矩
```
bandit28@bandit:/tmp/b$ git clone ssh://bandit28-git@localhost:2220/home/bandit28-git/repo
Cloning into 'repo'...
The authenticity of host '[localhost]:2220 ([127.0.0.1]:2220)' can't be established.
ED25519 key fingerprint is SHA256:C2ihUBV7ihnV1wUXRb4RrEcLfXC5CXlhmAAM/urerLY.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Could not create directory '/home/bandit28/.ssh' (Permission denied).
Failed to add the host to the list of known hosts (/home/bandit28/.ssh/known_hosts).
                         _                     _ _ _
                        | |__   __ _ _ __   __| (_) |_
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_
                        |_.__/ \__,_|_| |_|\__,_|_|\__|


                      This is an OverTheWire game server.
            More information on http://www.overthewire.org/wargames

bandit28-git@localhost's password:
remote: Enumerating objects: 9, done.
remote: Counting objects: 100% (9/9), done.
remote: Compressing objects: 100% (6/6), done.
remote: Total 9 (delta 2), reused 0 (delta 0), pack-reused 0
Receiving objects: 100% (9/9), done.
Resolving deltas: 100% (2/2), done.
bandit28@bandit:/tmp/b$ cd repo/
bandit28@bandit:/tmp/b/repo$ ll
total 16
drwxrwxr-x 3 bandit28 bandit28 4096 Jul 19 02:11 ./
drwxrwxr-x 3 bandit28 bandit28 4096 Jul 19 02:11 ../
drwxrwxr-x 8 bandit28 bandit28 4096 Jul 19 02:11 .git/
-rw-rw-r-- 1 bandit28 bandit28  111 Jul 19 02:11 README.md
bandit28@bandit:/tmp/b/repo$ cat README.md
# Bandit Notes
Some notes for level29 of bandit.

## credentials

- username: bandit29
- password: xxxxxxxxxx

bandit28@bandit:/tmp/b/repo$ git log
commit 899ba88df296331cc01f30d022c006775d467f28 (HEAD -> master, origin/master, origin/HEAD)
Author: Morla Porla <morla@overthewire.org>
Date:   Sun Apr 23 18:04:39 2023 +0000

    fix info leak

commit abcff758fa6343a0d002a1c0add1ad8c71b88534
Author: Morla Porla <morla@overthewire.org>
Date:   Sun Apr 23 18:04:39 2023 +0000

    add missing data

commit c0a8c3cf093fba65f4ee0e1fe2a530b799508c78
Author: Ben Dover <noone@overthewire.org>
Date:   Sun Apr 23 18:04:39 2023 +0000

    initial commit of README.md
```
**这是典型的git泄露**
```
bandit28@bandit:/tmp/b/repo$ git diff 899b abcf
diff --git a/README.md b/README.md
index 5c6457b..b302105 100644
--- a/README.md
+++ b/README.md
@@ -4,5 +4,5 @@ Some notes for level29 of bandit.
 ## credentials

 - username: bandit29
-- password: xxxxxxxxxx
+- password: tQKvmcwNYcFS6vmPHIUSI3ShmsrQZK8S

bandit28@bandit:/tmp/b/repo$
```
# level30
下载下来以后，一开始以为是stash，然后发现不是，那么查看别的分支。
```
bandit29@bandit:/tmp/c/repo$ git stash list
bandit29@bandit:/tmp/c/repo$ git branch  -a
* master
  remotes/origin/HEAD -> origin/master
  remotes/origin/dev
  remotes/origin/master
  remotes/origin/sploits-dev
bandit29@bandit:/tmp/c/repo$
```
然后切换分支即可
```
bandit29@bandit:/tmp/c/repo$ git checkout dev
Branch 'dev' set up to track remote branch 'dev' from 'origin'.
Switched to a new branch 'dev'
bandit29@bandit:/tmp/c/repo$ cat README.md
# Bandit Notes
Some notes for bandit30 of bandit.

## credentials

- username: bandit30
- password: xbhV3HpNGlTIdnjUrdAlPzc2L6y9EOnS

bandit29@bandit:/tmp/c/repo$
```
# level31
这个不会，看了一下网上的答案，这玩意儿叫引用，这里是[Git Pro教程](https://git-scm.com/docs/git-show-ref)
```
bandit30@bandit:/tmp/d/repo$ git show-ref
59530d30d299ff2e3e9719c096ebf46a65cc1424 refs/heads/master
59530d30d299ff2e3e9719c096ebf46a65cc1424 refs/remotes/origin/HEAD
59530d30d299ff2e3e9719c096ebf46a65cc1424 refs/remotes/origin/master
831aac2e2341f009e40e46392a4f5dd318483019 refs/tags/secret
bandit30@bandit:/tmp/d/repo$ git show 831a
OoffzGDlzhAlerFJ2cAiz1D41JW1Mhmt
bandit30@bandit:/tmp/d/repo$
```
# level32
push文件
```
bandit31@bandit:/tmp/d/repo$ git add -f ./key.txt
bandit31@bandit:/tmp/d/repo$ git commit -m "add key.txt"
[master 462b8a5] add key.txt
 1 file changed, 1 insertion(+)
 create mode 100644 key.txt
bandit31@bandit:/tmp/d/repo$ git push
The authenticity of host '[localhost]:2220 ([127.0.0.1]:2220)' can't be established.
ED25519 key fingerprint is SHA256:C2ihUBV7ihnV1wUXRb4RrEcLfXC5CXlhmAAM/urerLY.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Could not create directory '/home/bandit31/.ssh' (Permission denied).
Failed to add the host to the list of known hosts (/home/bandit31/.ssh/known_hosts).
                         _                     _ _ _
                        | |__   __ _ _ __   __| (_) |_
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_
                        |_.__/ \__,_|_| |_|\__,_|_|\__|


                      This is an OverTheWire game server.
            More information on http://www.overthewire.org/wargames

bandit31-git@localhost's password:
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 2 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 324 bytes | 324.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
remote: ### Attempting to validate files... ####
remote:
remote: .oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.
remote:
remote: Well done! Here is the password for the next level:
remote: rmCBvG56y58BXzv98yZGdO7ATVL5dW8y
remote:
remote: .oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.
remote:
To ssh://localhost:2220/home/bandit31-git/repo
 ! [remote rejected] master -> master (pre-receive hook declined)
error: failed to push some refs to 'ssh://localhost:2220/home/bandit31-git/repo'
bandit31@bandit:/tmp/d/repo$
```
# level33
这个不会，看的[答案](https://mayadevbe.me/posts/overthewire/bandit/level33/)
```
>> $0
$ cat /etc/bandit_pass/bandit33
odHo63fHiFqcWWJG9rLiLDtPm45KzUKy
```
# 彩蛋了
```
bandit33@bandit:~$ cat README.txt
Congratulations on solving the last level of this game!

At this moment, there are no more levels to play in this game. However, we are constantly working
on new levels and will most likely expand this game with more levels soon.
Keep an eye out for an announcement on our usual communication channels!
In the meantime, you could play some of our other wargames.

If you have an idea for an awesome new level, please let us know!
bandit33@bandit:~$
```
**完结撒花**