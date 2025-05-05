# 🛠️ Chris McDermut's Dotfiles

This repository contains my personal macOS development environment configuration: shell, editor, terminal, and system preferences.

## 🔧 Tools Covered

- **Shell**: `zsh` with custom aliases and environment variables
- **Terminal**: iTerm2 with custom profile (color scheme, fonts, spacing)
- **Editor**: Atom settings and packages (legacy setup)
- **System Setup**: Paths, invisible characters, indentation, etc.
- **Git**: Clean repo without history logs or secrets

## 🪜 Setup Instructions (New Machine)

> Assumes you're on macOS with Homebrew installed.

### 1. Clone this repo

```bash
git clone git@github.com:chrismcdermut/dotfiles.git ~/Sites/dotfiles
cd ~/Sites/dotfiles
```

### 2. Symlink config files

Back up existing config files first:

```bash
mkdir -p ~/.dotfiles-backup
mv ~/.zshrc ~/.bash_profile ~/.vimrc ~/.aliases ~/.path ~/.env_vars ~/.dotfiles-backup 2>/dev/null
```

Then symlink everything:

```bash
ln -s ~/Sites/dotfiles/.zshrc ~/.zshrc
ln -s ~/Sites/dotfiles/.bash_profile ~/.bash_profile
ln -s ~/Sites/dotfiles/.vimrc ~/.vimrc
ln -s ~/Sites/dotfiles/.aliases ~/.aliases
ln -s ~/Sites/dotfiles/.path ~/.path
ln -s ~/Sites/dotfiles/.env_vars ~/.env_vars
```

### 3. iTerm2 Setup

- Open iTerm2
- Go to **Preferences > Profiles > Other Actions > Import**
- Import `iterm2/com.googlecode.iterm2.plist`

Alternatively, place this file into:

```bash
cp ~/Sites/dotfiles/iterm2/com.googlecode.iterm2.plist ~/Library/Preferences/
```

Then restart iTerm2.

### 4. (Optional) Atom Setup

Atom is deprecated, but if needed:

```bash
cp -r ~/Sites/dotfiles/deprecated/.atom ~/.atom
```

### 5. Shell History Handling (optional)

Shell history files are **excluded from git**. If you want to sync them across machines:

```bash
cp ~/Sites/dotfiles/history/zsh_history ~/.zsh_history
cp ~/Sites/dotfiles/history/bash_history ~/.bash_history
```

These are **ignored** via `.gitignore`.

---

## 🚫 Git Clean State

- `.zsh_history` and `.bash_history` are scrubbed and not stored in version control.
- Commits are force-cleaned of any accidental sensitive info.

## 🧪 Validate Setup

After everything is linked:

```bash
source ~/.zshrc
```

Or restart your terminal.

---

## 📁 Repo Structure

```
dotfiles/
├── .aliases
├── .bash_profile
├── .env_vars
├── .path
├── .vimrc
├── .zshrc
├── iterm2/
│   └── com.googlecode.iterm2.plist
├── history/                # Shell histories (gitignored)
├── deprecated/             # Atom configs
└── README.md
```

---

## 🛡️ Safety

- No credentials, private keys, or shell history are committed.
- Verified clean using `git filter-repo`.

## 📌 Notes

- Designed for macOS.
- Uses `zsh` (the default shell on macOS).
- Assumes you'll manually install apps like iTerm2, VS Code, etc.

## Credits

This dotfiles setup was inspired by [Nick Rebhun's dotfiles](https://github.com/nrebhun/dotfiles).