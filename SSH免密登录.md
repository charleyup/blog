1. 本地生成ssh密钥
```bash
ssh-keygen
```
成功之后会在`.ssh`文件夹下生成公钥`id_rsa.pub`和私钥`id_rsa`。

2. 让远程服务器记住我们的公钥(本地执行)
```bash
ssh-copy-id user@remote -p port
```
到这一步已经可以免密登录了

3. 设置别名(本地)
```
# .ssh/config
Host lab
    HostName remote
    User user
    Port port
```
现在就可以使用`ssh lab`命令直接登录远程服务器了

4. 可能遇到的问题
```
[user@hostname ~]$ ssh root@pong
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that a host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
6e:45:f9:a8:af:38:3d:a1:a5:c7:76:1d:02:f8:77:00.
Please contact your system administrator.
Add correct host key in /home/hostname /.ssh/known_hosts to get rid of this message.
Offending RSA key in /var/lib/sss/pubconf/known_hosts:4
RSA host key for pong has changed and you have requested strict checking.
Host key verification failed.
```
解决办法:
```
ssh-keygen -R <host>
```
