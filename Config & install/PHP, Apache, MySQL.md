[A, PHP, MySQL](https://getgrav.org/blog/macos-ventura-apache-multiple-php-versions) Configuration tutoriel (bien slectionner Apple silicon pour les puces mac M1/M1 pro)

Instalation de obsidian pour les notes et discord.

# TUTORIEL 

### XCode
`xcode-select --install`

### Homebrew

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

##### Scripts installés

```bash
/opt/homebrew/bin/brew
/opt/homebrew/share/doc/homebrew
/opt/homebrew/share/man/man1/brew.1
/opt/homebrew/share/zsh/site-functions/_brew
/opt/homebrew/etc/bash_completion.d/brew
/opt/homebrew
```

##### Dossiers créés

```bash
/opt/homebrew/bin
/opt/homebrew/etc
/opt/homebrew/include
/opt/homebrew/lib
/opt/homebrew/sbin
/opt/homebrew/share
/opt/homebrew/var
/opt/homebrew/opt
/opt/homebrew/share/zsh
/opt/homebrew/share/zsh/site-functions
/opt/homebrew/var/homebrew
/opt/homebrew/var/homebrew/linked
/opt/homebrew/Cellar
/opt/homebrew/Caskroom
/opt/homebrew/Frameworks
```

Press ENTER/RETURN

##### PATH
Rentrer ces deux commandes

```bash
(echo; echo 'eval "$(/opt/homebrew/bin/brew shellenv)"') >> /Users/zach/.zprofile

eval "$(/opt/homebrew/bin/brew shellenv)"
```

Test version
`brew -v / brew doctor`
`-> Homebrew 4.0.5`

### OPENSSL Library
`brew install openssl`

### VSCode
`brew install --cask visual-studio-code`

##### Thème
Lien : [Deepdark Material Theme](https://vscodethemes.com/e/nimda.deepdark-material/deepdark-material-theme-or-default-version?language=javascript)

### Apache
`brew install httpd`

Chemin de httpd.conf 
```bash
/opt/homebrew/etc/httpd/httpd.conf
```

##### Lancer et arrêter un serveur local avec brew
```bash
brew services start httpd
brew services stop httpd
```

Ouvrir un chemin avec VSCode
`code /opt/homebrew/etc/httpd/httpd.conf`

Puis modifier et configurer apache en suivant le [tutoriel](https://getgrav.org/blog/macos-ventura-apache-multiple-php-versions) apres VSCode. Ce tutoriel configure le dossier qui va contenir le serveur apache. 

### PHP

##### Installer les versions de php avec shivammathur

```bash
brew tap shivammathur/php

brew install shivammathur/php/php@8.0 
brew install shivammathur/php/php@8.1 
brew install shivammathur/php/php@8.2
```

Si besoin les dossiers php.ini se trouvent

```bash
/opt/homebrew/etc/php/8.0/php.ini 
/opt/homebrew/etc/php/8.1/php.ini 
/opt/homebrew/etc/php/8.2/php.ini
```

Pour changer de version de PHP 

```bash
brew unlink php && brew link --overwrite --force php@8.1
```

Pour verfier la version d'utilisation
`php -v`

##### Configurer apache avec php
Suivre le [tutoriel](https://getgrav.org/blog/macos-ventura-apache-multiple-php-versions) pour modifier le fichier httpd.conf

##### À noter
Tout fonctionne apache ouvre bien le localhost avec la bonne version de PHP. Il est possible d'ajouter une commande de switch `sphp` mais tout fonctionne pour l'instant pas besoin. 