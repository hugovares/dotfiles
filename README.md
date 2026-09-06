# dotfiles

Meus arquivos de configuração de linha de comando para macOS (zsh, git, vim, tmux e afins).

## Instalação

```console
git clone https://github.com/hugovares/dotfiles ~/.dotfiles
cd ~/.dotfiles
chmod +x setup.sh
./setup.sh
```

O `setup.sh`:

1. Instala o Homebrew (se necessário) e o `zsh`.
2. Instala o [oh-my-zsh](https://ohmyzsh.sh/).
3. Cria um symlink em `~/.<nome>` para cada arquivo dentro de `files/` (ex.: `files/zshrc` → `~/.zshrc`). Se já existir algo em `~/.<nome>`, um backup é feito antes (`~/.<nome>.bkp.<pid>`).
4. Define o zsh como shell padrão.

Funciona tanto em Apple Silicon (`/opt/homebrew`) quanto em Intel (`/usr/local`).

## O que tem aqui

| Arquivo | Para quê |
|---|---|
| `zshrc` | shell, aliases e funções (git, docker, kubernetes, cloud CLIs, JDK switching, etc.) |
| `gitconfig`, `githelpers`, `git_template` | aliases de log, hook de `ctags` automático em checkout/commit/merge |
| `vimrc` | configuração básica do vim (usa [pathogen](https://github.com/tpope/vim-pathogen) como gerenciador de plugins) |
| `ideavimrc` | configuração do plugin [IdeaVim](https://github.com/JetBrains/ideavim) para IntelliJ/WebStorm/PyCharm/Android Studio |
| `tmux.conf` | configuração do tmux |
| `ackrc`, `agignore`, `colordiffrc` | configs de `ack`/`ag`/`colordiff` |
| `prose.zsh-theme` | tema do oh-my-zsh |

## Aliases e funções úteis

**Git:** `g`, `gs`, `ga`, `gc`, `gp`, `gd`, `gl` (log formatado), `gl1` (log --oneline), `gb`, `gm`, `gch`, `gt`, `gr`, `gk`.

**Docker / Kubernetes:** `d` (docker), `dc` (docker compose), `dps`, `k` (kubectl), `kgp`, `kctx`.

**Cloud / infra:** `tf`/`tfp`/`tfa` (terraform), `gcl` (gcloud), `aws` e `az` já vêm curtos o suficiente.

**Java:** não há mais uma função por versão. Use `jdk <versão>` para trocar o `JAVA_HOME` dinamicamente via `/usr/libexec/java_home`, ex.:

```console
jdk 21
jdk 17
```

Rode `jdk` com uma versão inexistente para listar as JDKs instaladas na máquina.

**Outras:** `killp <porta>` (mata processo numa porta), `showp <porta>`, `ff`/`fd`/`fl` (find por tipo), `size`, `ip`, `hr` (linha divisória no terminal), `dash` (abre docset no Dash.app).

## Customização local

Qualquer coisa específica da máquina (segredos, tokens, aliases pessoais) deve ir em `~/.zshrc-private` — esse arquivo é sourced automaticamente pelo `zshrc` se existir, e **não** faz parte deste repositório.

## Possíveis próximos passos

- Consolidar `rbenv`/`nvm` num único version manager poliglota (ex. [mise](https://mise.jdx.dev/) ou [asdf](https://asdf-vm.com/)) usando um `.tool-versions`.
- Migrar o `vimrc` de pathogen para um gerenciador de plugins mais moderno (`vim-plug`, pacotes nativos do vim8+, ou trocar por neovim + lua config).
