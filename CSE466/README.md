# CSE466
fall22
# 模块总结
## program misuse
这个模块比较基础，大部分是让你认识linux下的各种工具。对新人（指至少熟悉其中部分工具但没接触过CTF的人）来说应该启发很大，很多工具虽然设计出来并不是为了读取文件内容，但是由于其支持调试、输出错误信息、甚至是调用其他程序等种种运行方式，你可以通过这些方法得到文件内容。其实我认为这是让你关注那些工具不常用的功能，比如我一直在使用tldr，但tldr之中没有不常用的参数，因此做了几个题以后就不太适合这个挑战了。同时，作为CTF人，应该对权限很敏感，在一个工具有suid的情况下，深挖这个工具。我想这就是这个模块所能带来的启发了。

# 讲解
YOUTUBE上pwn college上传了老师的讲解，大多数很细致，少部分没有完成给出过程，但都有思路，需要自己去实现。其实在实现了之后发现也就是这么回事儿，但是思考的过程有时候是痛苦的。

# 我参考过的所有链接
- [一个博主](https://www.freebuf.com/author/thundersword)
- [一个做了不少的同学](https://j-shiro.github.io/)
- [一个不算特别具体的wp](https://hurricane618.me/2022/05/26/pwn-college-writeup-one/)
- [有一点点](https://www.cnblogs.com/crybaby/)
- [也不太多](https://s0uthwood.github.io/)
- [一个老哥记录的自己不会的题，无具体wp](https://i3r0nya.cn/categories/pwn/)
- [只有babyshell](https://imaxct.dev/2023/02/25/PwnCollege-baby-shell-writeup/)
- [部分题解](https://blog.junyu33.me/2032/07/03/pwn_college.html)
- [一个神奇的老哥，全是笔记，没有wp](https://s0merset7.github.io/posts/)
- [微信公众号文章，只有misuse部分](https://mp.weixin.qq.com/s/VoS5pwBkrq8k_WVVttBr4w)

很多题，不同人的解法真是不一样，可以多看看，参考着做，会有启发的。