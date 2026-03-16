# Linux


## OpenSSL

To get the certificates chain of any domain. It is relevant when for example your company uses ZScaler as proxy: 
```bash
openssl s_client -showcerts -connect example.com:443 </dev/null
```

## yum

Get all packages localy available for specific software package in RHEL/CentOS:
```bash
 sudo yum list erlang --showduplicates
```

## CLI Customization
Zsh setup with ohmyzsh and powerlevel10k theme:

Install zsh in Ubuntu/Debian:
```bash
sudo apt install zsh -y
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```
Install zsh in RHEL/CentOS:
```bash
sudo yum install zsh -y
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

Set Zsh as default shell:
```bash
chsh -s $(which zsh)
```

(Optional) Install powerlevel10k theme:
```bash
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git \
  ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```

(Optional) Set powerlevel10k as the default theme in `~/.zshrc`:
```bash
ZSH_THEME="powerlevel10k/powerlevel10k"
```

(Optional) Run the powerlevel10k configuration wizard:
```bash
source ~/.zshrc
p10k configure
```