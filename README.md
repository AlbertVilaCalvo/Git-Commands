Just a few commands ;)

* [Git](#Git)
* [npm](#npm)
* [Yarn](#Yarn)
* [Homebrew](#Homebrew)
* [Oh My Zsh](#Oh-My-Zsh)
* [Android](#Android)
* [React Native](#React-Native)

man pages: https://tldr.sh/

# Git

## Undo
```
git reset --soft HEAD^   # keeps changes
git reset --hard HEAD^   # discards changes
```
[source](https://stackoverflow.com/a/6376039/4034572)


### Undo a public commit
```
git revert HEAD
```


## Merge changes from remote master branch to a feature branch without switching to master
```
> git checkout some-branch
> git fetch origin # gets you up to date with origin by getting all commits on all branches, but named 'origin/branch'
> git merge origin/master # brings all commits in 'origin/master' to whatever branch we are; we could use --ff-only
> git fetch origin master:master # update master if we have a feature branch checked out
```
[source-part-1](https://stackoverflow.com/a/20103414/4034572)
[source-part-2](https://stackoverflow.com/a/17722977/4034572)

## GitHub pull request

https://gist.github.com/Chaser324/ce0505fbed06b947d962

http://blog.davidecoppola.com/2016/11/howto-contribute-to-open-source-project-on-github/

```
git remote add upstream git@github.com:Kotlin/kotlinx.coroutines.git
```


### Incorporating upstream changes
```
git fetch upstream master
git log --oneline --graph --decorate --all
git checkout master
git merge upstream/master
git push origin master
```


## Misc

### Remove untracked files
```
git clean -f -d
```


### Prune
```
git remote prune origin
```


### Squash all commits on a branch
```
git checkout your-branch
git reset $(git merge-base master your-branch)
```
This leaves all changes on the branch at the staging area. Then you can `git add .` and `git commit`.

[source](https://stackoverflow.com/a/25357146/4034572)


### Always use annotated tags
```
git tag -a v1.0
```

They have extra information like author, date, SHA and message ([more info](https://stackoverflow.com/q/4971746/4034572)).

### Search string in all git history
```
git log -S something
```

[source](https://stackoverflow.com/a/4472267/4034572)


# npm

Upgrade npm itself:

`npm install -g npm`

(If this command fails and we then get `zsh: command not found: npm` we can fix it with `brew reinstall node`.)

List global pacakges:

`npm list -g --depth=0`

List outdated global packages:

`npm outdated -g`

Add global package:

`npm install -g <package>`

Upgrade global package:

`npm update -g <package>`

Remove global package:

`npm uninstall -g <package>`


# Yarn

To upgrade yarn itself use Homebrew!

List global packages:

`yarn global list`

Add global package:

`yarn global add <package>`

Upgrade global packages one by one (lists all packages and versions and allows to choose):

`yarn global upgrade-interactive --latest`

Upgrade global packages all at once:

`yarn global upgrade`

Remove global package:

`yarn global remove <package>`

Know which version of a package you are using:

`yarn list @react-native-community/cli`


# Homebrew

https://docs.brew.sh/FAQ

```
brew update --debug --verbose
brew outdated
brew upgrade
brew cleanup
```

## Fix `zsh: command not found: yarn`

Run `brew doctor`. If you see:

```
Warning: You have unlinked kegs in your Cellar.
Leaving kegs unlinked can lead to build-trouble and cause brews that depend on
those kegs to fail to run properly once built. Run `brew link` on these:
  yarn
```

Then run `brew link yarn`, which fixes the issue.

## Cask

List of commands: https://github.com/Homebrew/homebrew-cask/blob/master/USAGE.md

```
brew cask list
brew cask install <package>
```


# Oh My Zsh

Upgrade: just type `upgrade_oh_my_zsh` :)


# Android

List emulators: `emulator -list-avds`

Launch emulator: `${ANDROID_HOME}/emulator/emulator -avd Nexus_5X_API_27_-_Google_Play &`


# React Native

Show dev menu: `adb shell input keyevent 82` or `adb shell input keyevent KEYCODE_MENU`
