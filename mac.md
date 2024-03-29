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

