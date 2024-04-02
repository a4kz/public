### macOS网络复原
hd -> library ->preferences -> systemconfiguration ->
只留下`com.apple.boot.plist` 其余都删除后在重新启动

------------

### homebrew installation

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

### homebrew stop auto update
```
# ~/.zshrc

export HOMEBREW_NO_AUTO_UPDATE=1
source ~/.zshrc
```

### homebrew update

```
brew update
```

### 查找 homebrew 安装程序的路径

```
brew list python
```



### oh-my-zsh installation

```
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

### oh-my-zsh update

```
omz update
```

### zsh-autosuggestions

```
brew install zsh-autosuggestions
```
#### `vi ~/.zshrc`
```
source $(brew --prefix)/share/zsh-autosuggestions/zsh-autosuggestions.zsh
```

### VSCode安装vim插件后，不能响应长按的问题解决

```
defaults write com.microsoft.VSCode ApplePressAndHoldEnabled -bool false
```

