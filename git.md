```
git config --global user.name "kevin"
git config --global user.email "kevin@example.com"
```

### 设置git客户端提交时的认证问题，参考

https://www.nih-cfde.org/resource/setting-up-github-authentication/#user-content-step-3a-generate-a-pat

------

### create a new repository
```
echo "# ptzhao" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add github https://github.com/a4kz/sth.git
git push -u github main
```

### push an existing repository 

```
git remote add github https://github.com/a4kz/ptzhao.git
git branch -M main
git push -u github main
```

