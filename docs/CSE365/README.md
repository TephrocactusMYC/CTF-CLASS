# CSE365
sp23，不得不说pwn college真是精品网站，题目很丰富，质量也还不错，入门、进阶都有，而且提供的靶场非常良心！在我一大通瞎搞之后，空间居然还这么大！
```
Filesystem      Size  Used Avail Use% Mounted on
overlay         916G  169G  701G  20% /
tmpfs            64M     0   64M   0% /dev
tmpfs           126G     0  126G   0% /sys/fs/cgroup
overlay         916G  169G  701G  20% /usr/sbin/docker-init
/dev/loop79     982M  557M  360M  61% /home/hacker
/dev/sdc2       916G  169G  701G  20% /etc/hosts
shm              64M     0   64M   0% /dev/shm
tmpfs           126G     0  126G   0% /proc/acpi
tmpfs           126G     0  126G   0% /proc/scsi
tmpfs           126G     0  126G   0% /sys/firmware
```
而且主目录持久保存，真是爱了！
# 模块总结
## talking web
这个模块比较简单，就是让你熟练使用curl、nc、python来进行http包的发送，是比较基础的。但是可以都记录下来这些内容，以便日后查阅。
## intercepting communication
这个模块涉及到了计算机网络的四层网络结构，还算是有点意思吧，大多数所需要的知识其实如果学过计算机网络这门课本身的话，都是最最浅显的。不过这个模块的意义就在于学习一下arp,ip,scapy怎么用，看看这些知识是怎么应用的，最后一个题有些困难，我在看了解答之后也是问了一个学了CTF的同学才搞定，G

主要是scapy的学习资料有点儿少，我搜了不少也没搜到最后一个特别相关的，不过相信在写完这些挑战之后对scapy和计算机网络的理解会有一定加深的。
# 讲解
YOUTUBE上pwn college上传了老师的讲解，大多数很细致，少部分没有完成给出过程，但都有思路，需要自己去实现。其实在实现了之后发现也就是这么回事儿，但是思考的过程有时候是痛苦的。
# 友链
另一位搞安全的盆友的[博客](https://tech.c01dkit.com/pwn-college-cse365-spring2023/)