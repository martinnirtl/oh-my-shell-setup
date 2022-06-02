```bash
$ let's make your shell awesome
```

## Installing `zsh`, `oh-my-zsh` and more

As the very first command, we upgrade all packages on our Ubuntu system:
```bash
sudo apt update && sudo apt upgrade
```

Next, we install `zsh` shell ([docs](https://github.com/ohmyzsh/ohmyzsh/wiki/Installing-ZSH)):
```bash
sudo apt install zsh
```
> You can verify the installation by running `zsh --version`.

We could now change the default shell to `zsh` with `chsh -s $(which zsh)`, but we can also change it during the `oh-my-zsh` installation ([docs](https://github.com/ohmyzsh/ohmyzsh#basic-installation)):
```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

Now that we got `oh-my-zsh` on our system, let's add some nice themes and plugins on top:
```bash
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```

To finalize the [plugin](https://github.com/ohmyzsh/ohmyzsh/wiki/Plugins) installation, we need to add the plugin names to the `plugins` array in your `.zshrc` file (run `vi ~/.zshrc` to open the file):
```
plugins=(git colorize jump kubectl docker sudo web-search history copyfile aliases zsh-syntax-highlighting zsh-autosuggestions)
```

Besides activating our plugins, we also want to switch the [theme](https://github.com/ohmyzsh/ohmyzsh/wiki/Themes) (look and feel)! So let's activate `powerlevel10k` by updating `ZSH_THEME` it in `.zshrc`:
```
ZSH_THEME="powerlevel10k/powerlevel10k"
```
> Powerlevel10k is an [external theme](https://github.com/ohmyzsh/ohmyzsh/wiki/External-themes) and can be found [here](https://github.com/romkatv/powerlevel10k).


## CLI tools ftw

### Azure CLI: az ([microsoft.com](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli-linux?pivots=apt))
```bash
curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash
```

### Kubernetes CLI: kubectl ([kubernetes.io](https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/))
```bash
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
curl -LO "https://dl.k8s.io/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl.sha256"
echo "$(cat kubectl.sha256)  kubectl" | sha256sum --check
sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
```

### Kubectl helpers: kubectx and kubens ([github.com](https://github.com/ahmetb/kubectx))
```bash
sudo apt install kubectx
```
> Optionally you can use the krew-based installation and set aliases in `.zshrc`!

## Nice and funny utils
- thefuck: https://github.com/nvbn/thefuck#installation
- cmatrix: https://howtoinstall.co/en/cmatrix
- sl: https://howtoinstall.co/en/sl
- lolcat: https://github.com/busyloop/lolcat 
- asciiquarium: https://askubuntu.com/questions/927441/how-do-i-install-asciiquarium
