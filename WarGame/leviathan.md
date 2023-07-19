# level0
ssh登录，老三样了
```
┌─🌵[myc@ubuntu22]─[~]
└──╼[11:00:33]$ ssh leviathan0@leviathan.labs.overthewire.org -p 2223
The authenticity of host '[leviathan.labs.overthewire.org]:2223 ([16.16.148.221]:2223)' can't be established.
ED25519 key fingerprint is SHA256:C2ihUBV7ihnV1wUXRb4RrEcLfXC5CXlhmAAM/urerLY.
This host key is known by the following other names/addresses:
    ~/.ssh/known_hosts:6: [hashed name]
    ~/.ssh/known_hosts:9: [hashed name]
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '[leviathan.labs.overthewire.org]:2223' (ED25519) to the list of known hosts.
                   _            _       _   _
                  | | _____   _(_) __ _| |_| |__   __ _ _ __
                  | |/ _ \ \ / / |/ _` | __| '_ \ / _` | '_ \
                  | |  __/\ V /| | (_| | |_| | | | (_| | | | |
                  |_|\___| \_/ |_|\__,_|\__|_| |_|\__,_|_| |_|


                      This is an OverTheWire game server.
            More information on http://www.overthewire.org/wargames

leviathan0@leviathan.labs.overthewire.org's password:

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

leviathan0@gibson:~$
```
# level1
先看一眼存密码的地方
```
total 48
drwxr-xr-x   2 root       root        4096 Apr 23 18:04 ./
drwxr-xr-x 111 root       root       12288 Apr 23 18:06 ../
-r--------   1 leviathan0 leviathan0    11 Apr 23 18:04 leviathan0
-r--------   1 leviathan1 leviathan1    11 Apr 23 18:04 leviathan1
-r--------   1 leviathan2 leviathan2    11 Apr 23 18:04 leviathan2
-r--------   1 leviathan3 leviathan3    11 Apr 23 18:04 leviathan3
-r--------   1 leviathan4 leviathan4    11 Apr 23 18:04 leviathan4
-r--------   1 leviathan5 leviathan5    11 Apr 23 18:04 leviathan5
-r--------   1 leviathan6 leviathan6    11 Apr 23 18:04 leviathan6
-r--------   1 leviathan7 leviathan7    11 Apr 23 18:04 leviathan7
leviathan0@gibson:~$
```
这挑战啥也不写，全靠脑洞啊。。。
```
leviathan0@gibson:~$ ll
total 24
drwxr-xr-x  3 root       root       4096 Apr 23 18:04 ./
drwxr-xr-x 83 root       root       4096 Apr 23 18:06 ../
drwxr-x---  2 leviathan1 leviathan0 4096 Apr 23 18:04 .backup/
-rw-r--r--  1 root       root        220 Jan  6  2022 .bash_logout
-rw-r--r--  1 root       root       3771 Jan  6  2022 .bashrc
-rw-r--r--  1 root       root        807 Jan  6  2022 .profile
leviathan0@gibson:~$ ll .backup
total 140
drwxr-x--- 2 leviathan1 leviathan0   4096 Apr 23 18:04 ./
drwxr-xr-x 3 root       root         4096 Apr 23 18:04 ../
-rw-r----- 1 leviathan1 leviathan0 133259 Apr 23 18:04 bookmarks.html
leviathan0@gibson:~$ cat .backup/bookmarks.html | grep "pass"
<DT><A HREF="http://leviathan.labs.overthewire.org/passwordus.html | This will be fixed later, the password for leviathan1 is PPIfmI1qsA" ADD_DATE="1155384634" LAST_CHARSET="ISO-8859-1" ID="rdf:#$2wIU71">password to leviathan1</A>
leviathan0@gibson:~$
```
反正进去以后看了看home，找到了
# level2
先看一下文件
```
leviathan1@gibson:~$ file check
check: setuid ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked, interpreter /lib/ld-linux.so.2, BuildID[sha1]=aab009a1eb3940df51c668d1c35dc9cdc1191805, for GNU/Linux 3.2.0, not stripped
```
说明如下：
- `setuid`：表示该可执行文件被设置了 SetUID 属性，即在执行该文件时，会使用该文件的所有者的权限来执行，而不是当前用户的权限。
- `ELF`：表示该可执行文件使用 ELF 文件格式。
- `32-bit`：表示该可执行文件是 32 位的。
- `LSB`：表示该可执行文件遵循 LSB（Linux Standard Base）规范。
- `Intel 80386`：表示该可执行文件是为 Intel 80386 架构编译的。
- `version 1 (SYSV)`：表示该可执行文件使用 SYSV 版本 1 ABI 标准。
- `dynamically linked`：表示该可执行文件使用动态链接库。
- `interpreter /lib/ld-linux.so.2`：表示该可执行文件使用 `/lib/ld-linux.so.2` 作为动态链接库的解释器。
- `BuildID[sha1]=aab009a1eb3940df51c668d1c35dc9cdc1191805`：表示该可执行文件的构建 ID。
- `for GNU/Linux 3.2.0`：表示该可执行文件是为 GNU/Linux 3.2.0 版本编译的。
- `not stripped`：表示该可执行文件没有被剥离（stripped），即可执行文件中包含了符号表和调试信息，便于调试和分析。

一开始没思路，输了好几遍密码都错，然后用strings扫了一下
```
leviathan1@gibson:~$ strings check
td8
/lib/ld-linux.so.2
_IO_stdin_used
__libc_start_main
__stack_chk_fail
puts
printf
getchar
system
strcmp
geteuid
setreuid
libc.so.6
GLIBC_2.4
GLIBC_2.34
GLIBC_2.0
__gmon_start__
secrf
love
password:
/bin/sh
Wrong password, Good Bye ...
```
搞了一下它的汇编
```
leviathan1@gibson:~$ objdump -d check

check:     file format elf32-i386


Disassembly of section .init:

08049000 <_init>:
 8049000:	f3 0f 1e fb          	endbr32
 8049004:	53                   	push   %ebx
 8049005:	83 ec 08             	sub    $0x8,%esp
 8049008:	e8 13 01 00 00       	call   8049120 <__x86.get_pc_thunk.bx>
 804900d:	81 c3 f3 2f 00 00    	add    $0x2ff3,%ebx
 8049013:	8b 83 fc ff ff ff    	mov    -0x4(%ebx),%eax
 8049019:	85 c0                	test   %eax,%eax
 804901b:	74 02                	je     804901f <_init+0x1f>
 804901d:	ff d0                	call   *%eax
 804901f:	83 c4 08             	add    $0x8,%esp
 8049022:	5b                   	pop    %ebx
 8049023:	c3                   	ret

Disassembly of section .plt:

08049030 <strcmp@plt-0x10>:
 8049030:	ff 35 04 c0 04 08    	push   0x804c004
 8049036:	ff 25 08 c0 04 08    	jmp    *0x804c008
 804903c:	00 00                	add    %al,(%eax)
	...

08049040 <strcmp@plt>:
 8049040:	ff 25 0c c0 04 08    	jmp    *0x804c00c
 8049046:	68 00 00 00 00       	push   $0x0
 804904b:	e9 e0 ff ff ff       	jmp    8049030 <_init+0x30>

08049050 <__libc_start_main@plt>:
 8049050:	ff 25 10 c0 04 08    	jmp    *0x804c010
 8049056:	68 08 00 00 00       	push   $0x8
 804905b:	e9 d0 ff ff ff       	jmp    8049030 <_init+0x30>

08049060 <printf@plt>:
 8049060:	ff 25 14 c0 04 08    	jmp    *0x804c014
 8049066:	68 10 00 00 00       	push   $0x10
 804906b:	e9 c0 ff ff ff       	jmp    8049030 <_init+0x30>

08049070 <getchar@plt>:
 8049070:	ff 25 18 c0 04 08    	jmp    *0x804c018
 8049076:	68 18 00 00 00       	push   $0x18
 804907b:	e9 b0 ff ff ff       	jmp    8049030 <_init+0x30>

08049080 <__stack_chk_fail@plt>:
 8049080:	ff 25 1c c0 04 08    	jmp    *0x804c01c
 8049086:	68 20 00 00 00       	push   $0x20
 804908b:	e9 a0 ff ff ff       	jmp    8049030 <_init+0x30>

08049090 <geteuid@plt>:
 8049090:	ff 25 20 c0 04 08    	jmp    *0x804c020
 8049096:	68 28 00 00 00       	push   $0x28
 804909b:	e9 90 ff ff ff       	jmp    8049030 <_init+0x30>

080490a0 <puts@plt>:
 80490a0:	ff 25 24 c0 04 08    	jmp    *0x804c024
 80490a6:	68 30 00 00 00       	push   $0x30
 80490ab:	e9 80 ff ff ff       	jmp    8049030 <_init+0x30>

080490b0 <system@plt>:
 80490b0:	ff 25 28 c0 04 08    	jmp    *0x804c028
 80490b6:	68 38 00 00 00       	push   $0x38
 80490bb:	e9 70 ff ff ff       	jmp    8049030 <_init+0x30>

080490c0 <setreuid@plt>:
 80490c0:	ff 25 2c c0 04 08    	jmp    *0x804c02c
 80490c6:	68 40 00 00 00       	push   $0x40
 80490cb:	e9 60 ff ff ff       	jmp    8049030 <_init+0x30>

Disassembly of section .text:

080490d0 <_start>:
 80490d0:	f3 0f 1e fb          	endbr32
 80490d4:	31 ed                	xor    %ebp,%ebp
 80490d6:	5e                   	pop    %esi
 80490d7:	89 e1                	mov    %esp,%ecx
 80490d9:	83 e4 f0             	and    $0xfffffff0,%esp
 80490dc:	50                   	push   %eax
 80490dd:	54                   	push   %esp
 80490de:	52                   	push   %edx
 80490df:	e8 19 00 00 00       	call   80490fd <_start+0x2d>
 80490e4:	81 c3 1c 2f 00 00    	add    $0x2f1c,%ebx
 80490ea:	6a 00                	push   $0x0
 80490ec:	6a 00                	push   $0x0
 80490ee:	51                   	push   %ecx
 80490ef:	56                   	push   %esi
 80490f0:	c7 c0 e6 91 04 08    	mov    $0x80491e6,%eax
 80490f6:	50                   	push   %eax
 80490f7:	e8 54 ff ff ff       	call   8049050 <__libc_start_main@plt>
 80490fc:	f4                   	hlt
 80490fd:	8b 1c 24             	mov    (%esp),%ebx
 8049100:	c3                   	ret
 8049101:	66 90                	xchg   %ax,%ax
 8049103:	66 90                	xchg   %ax,%ax
 8049105:	66 90                	xchg   %ax,%ax
 8049107:	66 90                	xchg   %ax,%ax
 8049109:	66 90                	xchg   %ax,%ax
 804910b:	66 90                	xchg   %ax,%ax
 804910d:	66 90                	xchg   %ax,%ax
 804910f:	90                   	nop

08049110 <_dl_relocate_static_pie>:
 8049110:	f3 0f 1e fb          	endbr32
 8049114:	c3                   	ret
 8049115:	66 90                	xchg   %ax,%ax
 8049117:	66 90                	xchg   %ax,%ax
 8049119:	66 90                	xchg   %ax,%ax
 804911b:	66 90                	xchg   %ax,%ax
 804911d:	66 90                	xchg   %ax,%ax
 804911f:	90                   	nop

08049120 <__x86.get_pc_thunk.bx>:
 8049120:	8b 1c 24             	mov    (%esp),%ebx
 8049123:	c3                   	ret
 8049124:	66 90                	xchg   %ax,%ax
 8049126:	66 90                	xchg   %ax,%ax
 8049128:	66 90                	xchg   %ax,%ax
 804912a:	66 90                	xchg   %ax,%ax
 804912c:	66 90                	xchg   %ax,%ax
 804912e:	66 90                	xchg   %ax,%ax

08049130 <deregister_tm_clones>:
 8049130:	b8 38 c0 04 08       	mov    $0x804c038,%eax
 8049135:	3d 38 c0 04 08       	cmp    $0x804c038,%eax
 804913a:	74 24                	je     8049160 <deregister_tm_clones+0x30>
 804913c:	b8 00 00 00 00       	mov    $0x0,%eax
 8049141:	85 c0                	test   %eax,%eax
 8049143:	74 1b                	je     8049160 <deregister_tm_clones+0x30>
 8049145:	55                   	push   %ebp
 8049146:	89 e5                	mov    %esp,%ebp
 8049148:	83 ec 14             	sub    $0x14,%esp
 804914b:	68 38 c0 04 08       	push   $0x804c038
 8049150:	ff d0                	call   *%eax
 8049152:	83 c4 10             	add    $0x10,%esp
 8049155:	c9                   	leave
 8049156:	c3                   	ret
 8049157:	8d b4 26 00 00 00 00 	lea    0x0(%esi,%eiz,1),%esi
 804915e:	66 90                	xchg   %ax,%ax
 8049160:	c3                   	ret
 8049161:	8d b4 26 00 00 00 00 	lea    0x0(%esi,%eiz,1),%esi
 8049168:	8d b4 26 00 00 00 00 	lea    0x0(%esi,%eiz,1),%esi
 804916f:	90                   	nop

08049170 <register_tm_clones>:
 8049170:	b8 38 c0 04 08       	mov    $0x804c038,%eax
 8049175:	2d 38 c0 04 08       	sub    $0x804c038,%eax
 804917a:	89 c2                	mov    %eax,%edx
 804917c:	c1 e8 1f             	shr    $0x1f,%eax
 804917f:	c1 fa 02             	sar    $0x2,%edx
 8049182:	01 d0                	add    %edx,%eax
 8049184:	d1 f8                	sar    %eax
 8049186:	74 20                	je     80491a8 <register_tm_clones+0x38>
 8049188:	ba 00 00 00 00       	mov    $0x0,%edx
 804918d:	85 d2                	test   %edx,%edx
 804918f:	74 17                	je     80491a8 <register_tm_clones+0x38>
 8049191:	55                   	push   %ebp
 8049192:	89 e5                	mov    %esp,%ebp
 8049194:	83 ec 10             	sub    $0x10,%esp
 8049197:	50                   	push   %eax
 8049198:	68 38 c0 04 08       	push   $0x804c038
 804919d:	ff d2                	call   *%edx
 804919f:	83 c4 10             	add    $0x10,%esp
 80491a2:	c9                   	leave
 80491a3:	c3                   	ret
 80491a4:	8d 74 26 00          	lea    0x0(%esi,%eiz,1),%esi
 80491a8:	c3                   	ret
 80491a9:	8d b4 26 00 00 00 00 	lea    0x0(%esi,%eiz,1),%esi

080491b0 <__do_global_dtors_aux>:
 80491b0:	f3 0f 1e fb          	endbr32
 80491b4:	80 3d 38 c0 04 08 00 	cmpb   $0x0,0x804c038
 80491bb:	75 1b                	jne    80491d8 <__do_global_dtors_aux+0x28>
 80491bd:	55                   	push   %ebp
 80491be:	89 e5                	mov    %esp,%ebp
 80491c0:	83 ec 08             	sub    $0x8,%esp
 80491c3:	e8 68 ff ff ff       	call   8049130 <deregister_tm_clones>
 80491c8:	c6 05 38 c0 04 08 01 	movb   $0x1,0x804c038
 80491cf:	c9                   	leave
 80491d0:	c3                   	ret
 80491d1:	8d b4 26 00 00 00 00 	lea    0x0(%esi,%eiz,1),%esi
 80491d8:	c3                   	ret
 80491d9:	8d b4 26 00 00 00 00 	lea    0x0(%esi,%eiz,1),%esi

080491e0 <frame_dummy>:
 80491e0:	f3 0f 1e fb          	endbr32
 80491e4:	eb 8a                	jmp    8049170 <register_tm_clones>

080491e6 <main>:
 80491e6:	8d 4c 24 04          	lea    0x4(%esp),%ecx
 80491ea:	83 e4 f0             	and    $0xfffffff0,%esp
 80491ed:	ff 71 fc             	push   -0x4(%ecx)
 80491f0:	55                   	push   %ebp
 80491f1:	89 e5                	mov    %esp,%ebp
 80491f3:	53                   	push   %ebx
 80491f4:	51                   	push   %ecx
 80491f5:	83 ec 20             	sub    $0x20,%esp
 80491f8:	65 a1 14 00 00 00    	mov    %gs:0x14,%eax
 80491fe:	89 45 f4             	mov    %eax,-0xc(%ebp)
 8049201:	31 c0                	xor    %eax,%eax
 8049203:	c7 45 e0 73 65 78 00 	movl   $0x786573,-0x20(%ebp)
 804920a:	c7 45 ed 73 65 63 72 	movl   $0x72636573,-0x13(%ebp)
 8049211:	66 c7 45 f1 65 74    	movw   $0x7465,-0xf(%ebp)
 8049217:	c6 45 f3 00          	movb   $0x0,-0xd(%ebp)
 804921b:	c7 45 e4 67 6f 64 00 	movl   $0x646f67,-0x1c(%ebp)
 8049222:	c7 45 e8 6c 6f 76 65 	movl   $0x65766f6c,-0x18(%ebp)
 8049229:	c6 45 ec 00          	movb   $0x0,-0x14(%ebp)
 804922d:	83 ec 0c             	sub    $0xc,%esp
 8049230:	68 08 a0 04 08       	push   $0x804a008
 8049235:	e8 26 fe ff ff       	call   8049060 <printf@plt>
 804923a:	83 c4 10             	add    $0x10,%esp
 804923d:	e8 2e fe ff ff       	call   8049070 <getchar@plt>
 8049242:	88 45 dc             	mov    %al,-0x24(%ebp)
 8049245:	e8 26 fe ff ff       	call   8049070 <getchar@plt>
 804924a:	88 45 dd             	mov    %al,-0x23(%ebp)
 804924d:	e8 1e fe ff ff       	call   8049070 <getchar@plt>
 8049252:	88 45 de             	mov    %al,-0x22(%ebp)
 8049255:	c6 45 df 00          	movb   $0x0,-0x21(%ebp)
 8049259:	83 ec 08             	sub    $0x8,%esp
 804925c:	8d 45 e0             	lea    -0x20(%ebp),%eax
 804925f:	50                   	push   %eax
 8049260:	8d 45 dc             	lea    -0x24(%ebp),%eax
 8049263:	50                   	push   %eax
 8049264:	e8 d7 fd ff ff       	call   8049040 <strcmp@plt>
 8049269:	83 c4 10             	add    $0x10,%esp
 804926c:	85 c0                	test   %eax,%eax
 804926e:	75 2b                	jne    804929b <main+0xb5>
 8049270:	e8 1b fe ff ff       	call   8049090 <geteuid@plt>
 8049275:	89 c3                	mov    %eax,%ebx
 8049277:	e8 14 fe ff ff       	call   8049090 <geteuid@plt>
 804927c:	83 ec 08             	sub    $0x8,%esp
 804927f:	53                   	push   %ebx
 8049280:	50                   	push   %eax
 8049281:	e8 3a fe ff ff       	call   80490c0 <setreuid@plt>
 8049286:	83 c4 10             	add    $0x10,%esp
 8049289:	83 ec 0c             	sub    $0xc,%esp
 804928c:	68 13 a0 04 08       	push   $0x804a013
 8049291:	e8 1a fe ff ff       	call   80490b0 <system@plt>
 8049296:	83 c4 10             	add    $0x10,%esp
 8049299:	eb 10                	jmp    80492ab <main+0xc5>
 804929b:	83 ec 0c             	sub    $0xc,%esp
 804929e:	68 1b a0 04 08       	push   $0x804a01b
 80492a3:	e8 f8 fd ff ff       	call   80490a0 <puts@plt>
 80492a8:	83 c4 10             	add    $0x10,%esp
 80492ab:	b8 00 00 00 00       	mov    $0x0,%eax
 80492b0:	8b 55 f4             	mov    -0xc(%ebp),%edx
 80492b3:	65 2b 15 14 00 00 00 	sub    %gs:0x14,%edx
 80492ba:	74 05                	je     80492c1 <main+0xdb>
 80492bc:	e8 bf fd ff ff       	call   8049080 <__stack_chk_fail@plt>
 80492c1:	8d 65 f8             	lea    -0x8(%ebp),%esp
 80492c4:	59                   	pop    %ecx
 80492c5:	5b                   	pop    %ebx
 80492c6:	5d                   	pop    %ebp
 80492c7:	8d 61 fc             	lea    -0x4(%ecx),%esp
 80492ca:	c3                   	ret

Disassembly of section .fini:

080492cc <_fini>:
 80492cc:	f3 0f 1e fb          	endbr32
 80492d0:	53                   	push   %ebx
 80492d1:	83 ec 08             	sub    $0x8,%esp
 80492d4:	e8 47 fe ff ff       	call   8049120 <__x86.get_pc_thunk.bx>
 80492d9:	81 c3 27 2d 00 00    	add    $0x2d27,%ebx
 80492df:	83 c4 08             	add    $0x8,%esp
 80492e2:	5b                   	pop    %ebx
 80492e3:	c3                   	ret
leviathan1@gibson:~$
```
其中的
```
movl $0x786573,-0x20(%ebp)
```
看出来密码是sex

*说好的只需要基本的linux命令呢？？？太抽象了*
```
leviathan1@gibson:~$ ./check
password: sex
$ cat /etc/leviathan_pass/leviathan2
mEh5PNl10e
$
```

### 他人解法
很好，然后去网上看了一下别人的答案，貌似有另一个好东西叫`ltrace`

这个玩意儿可以单步调试，然后就很简单了
```
leviathan1@gibson:~$ ltrace ./check
__libc_start_main(0x80491e6, 1, 0xffffd504, 0 <unfinished ...>
printf("password: ")                                         = 10
getchar(0xf7fbe4a0, 0xf7fd6f80, 0x786573, 0x646f67password: 123
)          = 49
getchar(0xf7fbe4a0, 0xf7fd6f31, 0x786573, 0x646f67)          = 50
getchar(0xf7fbe4a0, 0xf7fd3231, 0x786573, 0x646f67)          = 51
strcmp("123", "sex")                                         = -1
puts("Wrong password, Good Bye ..."Wrong password, Good Bye ...
)                         = 29
+++ exited (status 0) +++
leviathan1@gibson:~$
```
这里有一个中文的[教程](https://zhuanlan.zhihu.com/p/107063011)
# level3
直接运行会提示不成功
```
leviathan2@gibson:~$ ll
total 36
drwxr-xr-x  2 root       root        4096 Apr 23 18:04 ./
drwxr-xr-x 83 root       root        4096 Apr 23 18:06 ../
-rw-r--r--  1 root       root         220 Jan  6  2022 .bash_logout
-rw-r--r--  1 root       root        3771 Jan  6  2022 .bashrc
-r-sr-x---  1 leviathan3 leviathan2 15060 Apr 23 18:04 printfile*
-rw-r--r--  1 root       root         807 Jan  6  2022 .profile
leviathan2@gibson:~$ file printfile
printfile: setuid ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked, interpreter /lib/ld-linux.so.2, BuildID[sha1]=32c7e041842883e05808ab99c763a0fc1849b84e, for GNU/Linux 3.2.0, not stripped
leviathan2@gibson:~$ printfile
printfile: command not found
leviathan2@gibson:~$ printfile --help
printfile: command not found
leviathan2@gibson:~$ ./printfile
*** File Printer ***
Usage: ./printfile filename
leviathan2@gibson:~$ ./printfile /etc/leviathan_pass/leviathan3
You cant have that file...
```
然后分别看一下
```
leviathan2@gibson:~$ ./printfile /etc/leviathan_pass/leviathan2
/bin/cat: /etc/leviathan_pass/leviathan2: Permission denied
leviathan2@gibson:~$ ltrace ./printfile /etc/leviathan_pass/leviathan3
__libc_start_main(0x80491e6, 2, 0xffffd4d4, 0 <unfinished ...>
access("/etc/leviathan_pass/leviathan3", 4)                  = -1
puts("You cant have that file..."You cant have that file...
)                           = 27
+++ exited (status 1) +++
leviathan2@gibson:~$ ltrace ./printfile /etc/leviathan_pass/leviathan3
__libc_start_main(0x80491e6, 2, 0xffffd4d4, 0 <unfinished ...>
access("/etc/leviathan_pass/leviathan3", 4)                  = -1
puts("You cant have that file..."You cant have that file...
)                           = 27
+++ exited (status 1) +++
leviathan2@gibson:~$ ltrace ./printfile .bashrc
__libc_start_main(0x80491e6, 2, 0xffffd4e4, 0 <unfinished ...>
access(".bashrc", 4)                                         = 0
snprintf("/bin/cat .bashrc", 511, "/bin/cat %s", ".bashrc")  = 16
geteuid()                                                    = 12002
geteuid()                                                    = 12002
setreuid(12002, 12002)                                       = 0
system("/bin/cat .bashrc"# ~/.bashrc: executed by bash(1) for non-login shells.
```
这里的逻辑是，access函数来判断你是否有某个文件的权限，然后调用cat进行输出。因此可行的解释就是使用有空格的文件名，做一个软连接，这样cat只会读取第一个，就结束了。
```
leviathan2@gibson:~$ cd /tmp/
leviathan2@gibson:/tmp$ ls
ls: cannot open directory '.': Permission denied
leviathan2@gibson:/tmp$ mkdir hnz
leviathan2@gibson:/tmp$ cd hnz
leviathan2@gibson:/tmp/hnz$ ls
leviathan2@gibson:/tmp/hnz$ ll
total 732
drwxrwxr-x     2 leviathan2 leviathan2   4096 Jul 19 06:59 ./
drwxrwx-wt 16075 root       root       741376 Jul 19 06:59 ../
leviathan2@gibson:/tmp/hnz$ touch "file1 file2.txt"
leviathan2@gibson:/tmp/hnz$ ls
file1 file2.txt
leviathan2@gibson:/tmp/hnz$ ln -s /etc/leviathan_pass/leviathan3 /tmp/hnz/file1
leviathan2@gibson:/tmp/hnz$ ll
total 732
drwxrwxr-x     2 leviathan2 leviathan2   4096 Jul 19 07:02 ./
drwxrwx-wt 16075 root       root       741376 Jul 19 07:02 ../
lrwxrwxrwx     1 leviathan2 leviathan2     30 Jul 19 07:02 file1 -> /etc/leviathan_pass/leviathan3
-rw-rw-r--     1 leviathan2 leviathan2      0 Jul 19 07:00 file1 file2.txt
leviathan2@gibson:~$ ./printfile /tmp/hnz/"file1 file2.txt"
Q0G8j4sakn
/bin/cat: file2.txt: No such file or directory
leviathan2@gibson:~$
```
# level4
还是先看一下
```
leviathan3@gibson:~$ ./level3
Enter the password> 123
bzzzzzzzzap. WRONG
leviathan3@gibson:~$ ltrace ./level3
__libc_start_main(0x80492bf, 1, 0xffffd504, 0 <unfinished ...>
strcmp("h0no33", "kakaka")                                   = -1
printf("Enter the password> ")                               = 20
fgets(Enter the password> 1234
"1234\n", 256, 0xf7e2a620)                             = 0xffffd2dc
strcmp("1234\n", "snlprintf\n")                              = -1
puts("bzzzzzzzzap. WRONG"bzzzzzzzzap. WRONG
)                                   = 19
+++ exited (status 0) +++
```
然后就是直接读取了，这玩意儿就是一提权
```
leviathan3@gibson:~$ ./level3
Enter the password> snlprintf
[You've got shell]!
$ cat /etc/leviathan_pass/leviathan4
AgvropI4OA
$
```
# level5
画风越来越正常了
```
leviathan4@gibson:~/.trash$ ./bin
01000101 01001011 01001011 01101100 01010100 01000110 00110001 01011000 01110001 01110011 00001010
```
显然的ascii编码
```
echo "01000101 01001011 01001011 01101100 01010100 01000110 00110001 01011000 01110001 01110011 00001010" | perl -lape '$_=pack"(B8)*",@F'
EKKlTF1Xqs
```
# level6
貌似直接输出了level5的密码
```
leviathan5@gibson:~$ ./leviathan5
EKKlTF1Xqs
```
看起来有个叫log的很有用
```
leviathan5@gibson:~$ ltrace ./leviathan5
__libc_start_main(0x8049206, 1, 0xffffd534, 0 <unfinished ...>
fopen("/tmp/file.log", "r")                                  = 0
puts("Cannot find /tmp/file.log"Cannot find /tmp/file.log
)                            = 26
exit(-1 <no return ...>
+++ exited (status 255) +++
leviathan5@gibson:~$ ltrace ./leviathan5
__libc_start_main(0x8049206, 1, 0xffffd534, 0 <unfinished ...>
fopen("/tmp/file.log", "r")                                  = 0x804d1a0
fgetc(0x804d1a0)                                             = 'E'
feof(0x804d1a0)                                              = 0
putchar(69, 0x804a008, 0xf7c184be, 0xf7fbe4a0)               = 69
fgetc(0x804d1a0)                                             = 'K'
feof(0x804d1a0)                                              = 0
putchar(75, 0x804a008, 0xf7c184be, 0xf7fbe4a0)               = 75
fgetc(0x804d1a0)                                             = 'K'
feof(0x804d1a0)                                              = 0
putchar(75, 0x804a008, 0xf7c184be, 0xf7fbe4a0)               = 75
fgetc(0x804d1a0)                                             = 'l'
feof(0x804d1a0)                                              = 0
putchar(108, 0x804a008, 0xf7c184be, 0xf7fbe4a0)              = 108
fgetc(0x804d1a0)                                             = 'T'
feof(0x804d1a0)                                              = 0
putchar(84, 0x804a008, 0xf7c184be, 0xf7fbe4a0)               = 84
fgetc(0x804d1a0)                                             = 'F'
feof(0x804d1a0)                                              = 0
putchar(70, 0x804a008, 0xf7c184be, 0xf7fbe4a0)               = 70
fgetc(0x804d1a0)                                             = '1'
feof(0x804d1a0)                                              = 0
putchar(49, 0x804a008, 0xf7c184be, 0xf7fbe4a0)               = 49
fgetc(0x804d1a0)                                             = 'X'
feof(0x804d1a0)                                              = 0
putchar(88, 0x804a008, 0xf7c184be, 0xf7fbe4a0)               = 88
fgetc(0x804d1a0)                                             = 'q'
feof(0x804d1a0)                                              = 0
putchar(113, 0x804a008, 0xf7c184be, 0xf7fbe4a0)              = 113
fgetc(0x804d1a0)                                             = 's'
feof(0x804d1a0)                                              = 0
putchar(115, 0x804a008, 0xf7c184be, 0xf7fbe4a0)              = 115
fgetc(0x804d1a0)                                             = '\n'
feof(0x804d1a0)                                              = 0
putchar(10, 0x804a008, 0xf7c184be, 0xf7fbe4a0EKKlTF1Xqs
)               = 10
fgetc(0x804d1a0)                                             = '\377'
feof(0x804d1a0)                                              = 1
fclose(0x804d1a0)                                            = 0
getuid()                                                     = 12005
setuid(12005)                                                = 0
unlink("/tmp/file.log")                                      = 0
+++ exited (status 0) +++
leviathan5@gibson:~$
```
那还是软连接就解决了
```
leviathan5@gibson:~$ ln -s /etc/leviathan_pass/leviathan6 /tmp/file.log
leviathan5@gibson:~$ ./leviathan5
YZ55XPVk2l
leviathan5@gibson:~$
```
# level7
```
leviathan6@gibson:~$ ./leviathan6
usage: ./leviathan6 <4 digit code>
leviathan6@gibson:~$ ltrace ./leviathan6
__libc_start_main(0x80491d6, 1, 0xffffd504, 0 <unfinished ...>
printf("usage: %s <4 digit code>\n", "./leviathan6"usage: ./leviathan6 <4 digit code>
)         = 35
exit(-1 <no return ...>
+++ exited (status 255) +++
leviathan6@gibson:~$ ltrace ./leviathan6 1234
__libc_start_main(0x80491d6, 2, 0xffffd4e4, 0 <unfinished ...>
atoi(0xffffd668, 0xf7fd6f80, 0xf7c184be, 0xf7fbe4a0)         = 1234
puts("Wrong"Wrong
)                                                = 6
+++ exited (status 0) +++
```
很好，又要看汇编了
```
leviathan6@gibson:~$ objdump -d leviathan6

leviathan6:     file format elf32-i386


Disassembly of section .init:

08049000 <_init>:
 8049000:	f3 0f 1e fb          	endbr32
 8049004:	53                   	push   %ebx
 8049005:	83 ec 08             	sub    $0x8,%esp
 8049008:	e8 03 01 00 00       	call   8049110 <__x86.get_pc_thunk.bx>
 804900d:	81 c3 f3 2f 00 00    	add    $0x2ff3,%ebx
 8049013:	8b 83 fc ff ff ff    	mov    -0x4(%ebx),%eax
 8049019:	85 c0                	test   %eax,%eax
 804901b:	74 02                	je     804901f <_init+0x1f>
 804901d:	ff d0                	call   *%eax
 804901f:	83 c4 08             	add    $0x8,%esp
 8049022:	5b                   	pop    %ebx
 8049023:	c3                   	ret

Disassembly of section .plt:

08049030 <__libc_start_main@plt-0x10>:
 8049030:	ff 35 04 c0 04 08    	push   0x804c004
 8049036:	ff 25 08 c0 04 08    	jmp    *0x804c008
 804903c:	00 00                	add    %al,(%eax)
	...

08049040 <__libc_start_main@plt>:
 8049040:	ff 25 0c c0 04 08    	jmp    *0x804c00c
 8049046:	68 00 00 00 00       	push   $0x0
 804904b:	e9 e0 ff ff ff       	jmp    8049030 <_init+0x30>

08049050 <printf@plt>:
 8049050:	ff 25 10 c0 04 08    	jmp    *0x804c010
 8049056:	68 08 00 00 00       	push   $0x8
 804905b:	e9 d0 ff ff ff       	jmp    8049030 <_init+0x30>

08049060 <geteuid@plt>:
 8049060:	ff 25 14 c0 04 08    	jmp    *0x804c014
 8049066:	68 10 00 00 00       	push   $0x10
 804906b:	e9 c0 ff ff ff       	jmp    8049030 <_init+0x30>

08049070 <puts@plt>:
 8049070:	ff 25 18 c0 04 08    	jmp    *0x804c018
 8049076:	68 18 00 00 00       	push   $0x18
 804907b:	e9 b0 ff ff ff       	jmp    8049030 <_init+0x30>

08049080 <system@plt>:
 8049080:	ff 25 1c c0 04 08    	jmp    *0x804c01c
 8049086:	68 20 00 00 00       	push   $0x20
 804908b:	e9 a0 ff ff ff       	jmp    8049030 <_init+0x30>

08049090 <exit@plt>:
 8049090:	ff 25 20 c0 04 08    	jmp    *0x804c020
 8049096:	68 28 00 00 00       	push   $0x28
 804909b:	e9 90 ff ff ff       	jmp    8049030 <_init+0x30>

080490a0 <setreuid@plt>:
 80490a0:	ff 25 24 c0 04 08    	jmp    *0x804c024
 80490a6:	68 30 00 00 00       	push   $0x30
 80490ab:	e9 80 ff ff ff       	jmp    8049030 <_init+0x30>

080490b0 <atoi@plt>:
 80490b0:	ff 25 28 c0 04 08    	jmp    *0x804c028
 80490b6:	68 38 00 00 00       	push   $0x38
 80490bb:	e9 70 ff ff ff       	jmp    8049030 <_init+0x30>

Disassembly of section .text:

080490c0 <_start>:
 80490c0:	f3 0f 1e fb          	endbr32
 80490c4:	31 ed                	xor    %ebp,%ebp
 80490c6:	5e                   	pop    %esi
 80490c7:	89 e1                	mov    %esp,%ecx
 80490c9:	83 e4 f0             	and    $0xfffffff0,%esp
 80490cc:	50                   	push   %eax
 80490cd:	54                   	push   %esp
 80490ce:	52                   	push   %edx
 80490cf:	e8 19 00 00 00       	call   80490ed <_start+0x2d>
 80490d4:	81 c3 2c 2f 00 00    	add    $0x2f2c,%ebx
 80490da:	6a 00                	push   $0x0
 80490dc:	6a 00                	push   $0x0
 80490de:	51                   	push   %ecx
 80490df:	56                   	push   %esi
 80490e0:	c7 c0 d6 91 04 08    	mov    $0x80491d6,%eax
 80490e6:	50                   	push   %eax
 80490e7:	e8 54 ff ff ff       	call   8049040 <__libc_start_main@plt>
 80490ec:	f4                   	hlt
 80490ed:	8b 1c 24             	mov    (%esp),%ebx
 80490f0:	c3                   	ret
 80490f1:	66 90                	xchg   %ax,%ax
 80490f3:	66 90                	xchg   %ax,%ax
 80490f5:	66 90                	xchg   %ax,%ax
 80490f7:	66 90                	xchg   %ax,%ax
 80490f9:	66 90                	xchg   %ax,%ax
 80490fb:	66 90                	xchg   %ax,%ax
 80490fd:	66 90                	xchg   %ax,%ax
 80490ff:	90                   	nop

08049100 <_dl_relocate_static_pie>:
 8049100:	f3 0f 1e fb          	endbr32
 8049104:	c3                   	ret
 8049105:	66 90                	xchg   %ax,%ax
 8049107:	66 90                	xchg   %ax,%ax
 8049109:	66 90                	xchg   %ax,%ax
 804910b:	66 90                	xchg   %ax,%ax
 804910d:	66 90                	xchg   %ax,%ax
 804910f:	90                   	nop

08049110 <__x86.get_pc_thunk.bx>:
 8049110:	8b 1c 24             	mov    (%esp),%ebx
 8049113:	c3                   	ret
 8049114:	66 90                	xchg   %ax,%ax
 8049116:	66 90                	xchg   %ax,%ax
 8049118:	66 90                	xchg   %ax,%ax
 804911a:	66 90                	xchg   %ax,%ax
 804911c:	66 90                	xchg   %ax,%ax
 804911e:	66 90                	xchg   %ax,%ax

08049120 <deregister_tm_clones>:
 8049120:	b8 34 c0 04 08       	mov    $0x804c034,%eax
 8049125:	3d 34 c0 04 08       	cmp    $0x804c034,%eax
 804912a:	74 24                	je     8049150 <deregister_tm_clones+0x30>
 804912c:	b8 00 00 00 00       	mov    $0x0,%eax
 8049131:	85 c0                	test   %eax,%eax
 8049133:	74 1b                	je     8049150 <deregister_tm_clones+0x30>
 8049135:	55                   	push   %ebp
 8049136:	89 e5                	mov    %esp,%ebp
 8049138:	83 ec 14             	sub    $0x14,%esp
 804913b:	68 34 c0 04 08       	push   $0x804c034
 8049140:	ff d0                	call   *%eax
 8049142:	83 c4 10             	add    $0x10,%esp
 8049145:	c9                   	leave
 8049146:	c3                   	ret
 8049147:	8d b4 26 00 00 00 00 	lea    0x0(%esi,%eiz,1),%esi
 804914e:	66 90                	xchg   %ax,%ax
 8049150:	c3                   	ret
 8049151:	8d b4 26 00 00 00 00 	lea    0x0(%esi,%eiz,1),%esi
 8049158:	8d b4 26 00 00 00 00 	lea    0x0(%esi,%eiz,1),%esi
 804915f:	90                   	nop

08049160 <register_tm_clones>:
 8049160:	b8 34 c0 04 08       	mov    $0x804c034,%eax
 8049165:	2d 34 c0 04 08       	sub    $0x804c034,%eax
 804916a:	89 c2                	mov    %eax,%edx
 804916c:	c1 e8 1f             	shr    $0x1f,%eax
 804916f:	c1 fa 02             	sar    $0x2,%edx
 8049172:	01 d0                	add    %edx,%eax
 8049174:	d1 f8                	sar    %eax
 8049176:	74 20                	je     8049198 <register_tm_clones+0x38>
 8049178:	ba 00 00 00 00       	mov    $0x0,%edx
 804917d:	85 d2                	test   %edx,%edx
 804917f:	74 17                	je     8049198 <register_tm_clones+0x38>
 8049181:	55                   	push   %ebp
 8049182:	89 e5                	mov    %esp,%ebp
 8049184:	83 ec 10             	sub    $0x10,%esp
 8049187:	50                   	push   %eax
 8049188:	68 34 c0 04 08       	push   $0x804c034
 804918d:	ff d2                	call   *%edx
 804918f:	83 c4 10             	add    $0x10,%esp
 8049192:	c9                   	leave
 8049193:	c3                   	ret
 8049194:	8d 74 26 00          	lea    0x0(%esi,%eiz,1),%esi
 8049198:	c3                   	ret
 8049199:	8d b4 26 00 00 00 00 	lea    0x0(%esi,%eiz,1),%esi

080491a0 <__do_global_dtors_aux>:
 80491a0:	f3 0f 1e fb          	endbr32
 80491a4:	80 3d 34 c0 04 08 00 	cmpb   $0x0,0x804c034
 80491ab:	75 1b                	jne    80491c8 <__do_global_dtors_aux+0x28>
 80491ad:	55                   	push   %ebp
 80491ae:	89 e5                	mov    %esp,%ebp
 80491b0:	83 ec 08             	sub    $0x8,%esp
 80491b3:	e8 68 ff ff ff       	call   8049120 <deregister_tm_clones>
 80491b8:	c6 05 34 c0 04 08 01 	movb   $0x1,0x804c034
 80491bf:	c9                   	leave
 80491c0:	c3                   	ret
 80491c1:	8d b4 26 00 00 00 00 	lea    0x0(%esi,%eiz,1),%esi
 80491c8:	c3                   	ret
 80491c9:	8d b4 26 00 00 00 00 	lea    0x0(%esi,%eiz,1),%esi

080491d0 <frame_dummy>:
 80491d0:	f3 0f 1e fb          	endbr32
 80491d4:	eb 8a                	jmp    8049160 <register_tm_clones>

080491d6 <main>:
 80491d6:	8d 4c 24 04          	lea    0x4(%esp),%ecx
 80491da:	83 e4 f0             	and    $0xfffffff0,%esp
 80491dd:	ff 71 fc             	push   -0x4(%ecx)
 80491e0:	55                   	push   %ebp
 80491e1:	89 e5                	mov    %esp,%ebp
 80491e3:	53                   	push   %ebx
 80491e4:	51                   	push   %ecx
 80491e5:	83 ec 10             	sub    $0x10,%esp
 80491e8:	89 c8                	mov    %ecx,%eax
 80491ea:	c7 45 f4 d3 1b 00 00 	movl   $0x1bd3,-0xc(%ebp)
 80491f1:	83 38 02             	cmpl   $0x2,(%eax)
 80491f4:	74 20                	je     8049216 <main+0x40>
 80491f6:	8b 40 04             	mov    0x4(%eax),%eax
 80491f9:	8b 00                	mov    (%eax),%eax
 80491fb:	83 ec 08             	sub    $0x8,%esp
 80491fe:	50                   	push   %eax
 80491ff:	68 08 a0 04 08       	push   $0x804a008
 8049204:	e8 47 fe ff ff       	call   8049050 <printf@plt>
 8049209:	83 c4 10             	add    $0x10,%esp
 804920c:	83 ec 0c             	sub    $0xc,%esp
 804920f:	6a ff                	push   $0xffffffff
 8049211:	e8 7a fe ff ff       	call   8049090 <exit@plt>
 8049216:	8b 40 04             	mov    0x4(%eax),%eax
 8049219:	83 c0 04             	add    $0x4,%eax
 804921c:	8b 00                	mov    (%eax),%eax
 804921e:	83 ec 0c             	sub    $0xc,%esp
 8049221:	50                   	push   %eax
 8049222:	e8 89 fe ff ff       	call   80490b0 <atoi@plt>
 8049227:	83 c4 10             	add    $0x10,%esp
 804922a:	39 45 f4             	cmp    %eax,-0xc(%ebp)
 804922d:	75 2b                	jne    804925a <main+0x84>
 804922f:	e8 2c fe ff ff       	call   8049060 <geteuid@plt>
 8049234:	89 c3                	mov    %eax,%ebx
 8049236:	e8 25 fe ff ff       	call   8049060 <geteuid@plt>
 804923b:	83 ec 08             	sub    $0x8,%esp
 804923e:	53                   	push   %ebx
 804923f:	50                   	push   %eax
 8049240:	e8 5b fe ff ff       	call   80490a0 <setreuid@plt>
 8049245:	83 c4 10             	add    $0x10,%esp
 8049248:	83 ec 0c             	sub    $0xc,%esp
 804924b:	68 22 a0 04 08       	push   $0x804a022
 8049250:	e8 2b fe ff ff       	call   8049080 <system@plt>
 8049255:	83 c4 10             	add    $0x10,%esp
 8049258:	eb 10                	jmp    804926a <main+0x94>
 804925a:	83 ec 0c             	sub    $0xc,%esp
 804925d:	68 2a a0 04 08       	push   $0x804a02a
 8049262:	e8 09 fe ff ff       	call   8049070 <puts@plt>
 8049267:	83 c4 10             	add    $0x10,%esp
 804926a:	b8 00 00 00 00       	mov    $0x0,%eax
 804926f:	8d 65 f8             	lea    -0x8(%ebp),%esp
 8049272:	59                   	pop    %ecx
 8049273:	5b                   	pop    %ebx
 8049274:	5d                   	pop    %ebp
 8049275:	8d 61 fc             	lea    -0x4(%ecx),%esp
 8049278:	c3                   	ret

Disassembly of section .fini:

0804927c <_fini>:
 804927c:	f3 0f 1e fb          	endbr32
 8049280:	53                   	push   %ebx
 8049281:	83 ec 08             	sub    $0x8,%esp
 8049284:	e8 87 fe ff ff       	call   8049110 <__x86.get_pc_thunk.bx>
 8049289:	81 c3 77 2d 00 00    	add    $0x2d77,%ebx
 804928f:	83 c4 08             	add    $0x8,%esp
 8049292:	5b                   	pop    %ebx
 8049293:	c3                   	ret
```
还是movl这一句找立即数
```
80491ea:	c7 45 f4 d3 1b 00 00 	movl   $0x1bd3,-0xc(%ebp)
```
0x1bd3换算一下是7123
然后得到密码
```
leviathan6@gibson:~$ ./leviathan6 7123
$ cat /etc/leviathan_pass/leviathan7
8GpZ5f8Hze
$
```
进彩蛋
```
leviathan7@gibson:~$ ll
total 24
drwxr-xr-x  2 root       root       4096 Apr 23 18:05 ./
drwxr-xr-x 83 root       root       4096 Apr 23 18:06 ../
-rw-r--r--  1 root       root        220 Jan  6  2022 .bash_logout
-rw-r--r--  1 root       root       3771 Jan  6  2022 .bashrc
-r--r-----  1 leviathan7 leviathan7  178 Apr 23 18:05 CONGRATULATIONS
-rw-r--r--  1 root       root        807 Jan  6  2022 .profile
leviathan7@gibson:~$ cat CONGRATULATIONS
Well Done, you seem to have used a *nix system before, now try something more serious.
(Please don't post writeups, solutions or spoilers about the games on the web. Thank you!)
leviathan7@gibson:~$
```
这玩意儿，里面有大量的东西可不是linux操作啊，这里面有阅读汇编的内容的事儿，可底层。。。

**被骗的很惨啊，这里面要会的linux是不是指RHCA那种，那可真屌**

*咋回事儿，人家不让传答案，az，反正我没啥流量，就传了吧。。。*