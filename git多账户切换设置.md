## 背景
最近新申请了个github账号，再加上公司内部搭了gitlab私服，总共三个git账户，多个git账户如何优雅的切换，提高开发效率呢？

## 设置
1. 创建`.git-credentials`文件夹，并初始化三个账号的登录凭证。
```bash
    mkdir .git-credentials
    cd .git-credentials
    touch Lee-Cloud
    touch charleyup
    touch maysa
```

2. 清除`system`和`global`登录凭证设置
```bash
    git config --system --unset credential.helper
    git config --global --unset credential.helper
```

3. 由于公司项目是最场使用的，因此我将公司的git账号作为全局的登录凭证。

```bash
    git config --global credential.helper store --file ~/.git-credentials/maysa
    # 这里用命令行配置失败，也可以直接在文件里修改
    # .gitconfig
    [credential]
        helper = store --file $HOME/.git-credentials/maysa
```

4. 设置GitHub charleyup账号登录凭证
```bash
    # 进入charleyup项目文件夹设置该仓库的登录凭证
    cd charleyup-project
    git config credential.helper store --file ~/.git-credentials/charleyup
    # 同理修改失败的话直接在文件里修改
```

5. 设置GitHub Lee-Cloud账号登录凭证同第三点。

6. 设置成功后输入一次密码后本地即永久记住密码，即将各自账户的密码写进本地`~/.git-credentials`文件夹下对应文件，下次无需再输入账户密码。
