
# Before the beginning

在南京大学的

blog并不是要完整的翻译整篇手册的内容，而是选取一些我原来不知道的知识点进行解释。

# sh 手册导读

## Redirections 重定向

重定向的格式为 

```
[n] redir-op file
```

其中 `"[n]"` 是一个可选的`File descriptor`。这让我想起了一些shell脚本中的 `"2>&1"` 。在StackoverFlow中的[`In the shell, what does " 2>&1 " mean?`](https://stackoverflowpoint.com/question/bash-in-the-shell-what-does-21-mean/)提到：

> File descriptor 0 is the standard input (stdin).   
File descriptor 1 is the standard output (stdout).  
File descriptor 2 is the standard error (stderr).

作用是把标准错误输出到屏幕上。`&` 的作用是避免将 `1` 解释为文件名。严格意义上来说，所有的

```
echo test > afile.txt
```

实际上都是默认了

```
echo test 1> afile.txt
```

博文中提到了一个很有趣的demo
```
(base) junliu@JunliusLaptop:~$ ls -ld /tmp /tnt
ls: cannot access '/tnt': No such file or directory
drwxrwxrwt 1 root root 512 Jun 23 17:55 /tmp

(base) junliu@JunliusLaptop:~$ ls -ld /tmp /tnt >/dev/null
ls: cannot access '/tnt': No such file or directory

(base) junliu@JunliusLaptop:~$ ls -ld /tmp /tnt 2>/dev/null
drwxrwxrwt 1 root root 512 Jun 23 17:55 /tmp
```



