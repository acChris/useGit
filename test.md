## 使用gitlab进行push出现的错误
### 前提：已输入邮箱名字

### FAQ

**问题：git clone/push 都失败了**

**报错：**
![](https://img2020.cnblogs.com/blog/2191525/202012/2191525-20201205192357999-1246482413.png)


```
fatal: unable to access 'https://git.......': 
Failed to connect to 127.0.0.1 port 1080: Connection refused
```

或
```
fatal: unable to connect to gitlab.com:
gitlab.com[0: 180.97.125.228]: errno=Invalid argument
```

或

`Timed out`



#### 解决方案：
1. https://改成git@

2. 
```
fatal: 'git@gitlab.com/.../test.git' does not appear to be a git repository
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.
```

![](https://img2020.cnblogs.com/blog/2191525/202012/2191525-20201207234828195-1259868842.png)


### 解决方案：

1. 经过百度，知道可能是github/gitlab上面的README.md文件不在本地目录，可以先合并：

* `git pull --rebase origin master`

2. 再度报错：

```
$ git push origin master
fatal: unable to access 'https://gitlab.com/.../test.git/': Empty reply from server
```

3. 尝试：

```
      git config --global --unset http.proxy 
      git config --global --unset https.proxy
```

again:`Empty reply from server`

4. 查看自己的配置

`git config --global -l`

如果没有http_proxy或https_proxy则无误

5. 仍然无用，则取消环境变量

`env|grep -i proxy  `

如果无显示信息应该是好的

6. 再次检查环境变量（重要）

`env|grep -i proxy`  

我记得我有一次只输入了一次这个env|grep -i proxy ，然后再尝试push，依旧失败，所以这一步不能省略。

问题参考地址：

https://blog.csdn.net/u013468614/article/details/83116044

https://blog.csdn.net/dashi_lu/article/details/89641778

