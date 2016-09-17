# alias设置
alias是一个shell命令，可以理解为别名，就是可以让我们对一些命名重新命名，这样在终端中，我们就可以输入更少的字符完成同样的事情。

## 系统自带(或者是oh-my-zsh添加的)
在终端中输入`alias`，会得到:

```
...=../..
....=../../..
.....=../../../..
......=../../../../..
1='cd -'
2='cd -2'
3='cd -3'
4='cd -4'
5='cd -5'
6='cd -6'
7='cd -7'
8='cd -8'
9='cd -9'
_=sudo
a='fasd -a'
afind='ack-grep -il'
d='fasd -d'
f='fasd -f'
g=git
ga='git add'
gaa='git add --all'
gap='git add --patch'
gb='git branch'
gba='git branch -a'
gbr='git branch --remote'
gc='git commit -v'
'gc!'='git commit -v --amend'
gca='git commit -v -a'
'gca!'='git commit -v -a --amend'
gcl='git config --list'
gclean='git reset --hard && git clean -dfx'
gcm='git checkout master'
gcmsg='git commit -m'
gco='git checkout'
gcount='git shortlog -sn'
gcp='git cherry-pick'
gcs='git commit -S'
gd='git diff'
gdc='git diff --cached'
gdt='git difftool'
gg='git gui citool'
gga='git gui citool --amend'
ggpnp='git pull origin $(current_branch) && git push origin $(current_branch)'
ggpull='git pull origin $(current_branch)'
ggpur='git pull --rebase origin $(current_branch)'
ggpush='git push origin $(current_branch)'
gignore='git update-index --assume-unchanged'
gignored='git ls-files -v | grep "^[[:lower:]]"'
git-svn-dcommit-push='git svn dcommit && git push github master:svntrunk'
gk='gitk --all --branches'
gl='git pull'
glg='git log --stat --max-count=10'
glgg='git log --graph --max-count=10'
glgga='git log --graph --decorate --all'
glo='git log --oneline --decorate --color'
globurl='noglob urlglobber '
glog='git log --oneline --decorate --color --graph'
glp=_git_log_prettily
gm='git merge'
gmt='git mergetool --no-prompt'
gp='git push'
gpoat='git push origin --all && git push origin --tags'
gr='git remote'
grba='git rebase --abort'
grbc='git rebase --continue'
grbi='git rebase -i'
grep='grep  --color=auto --exclude-dir={.bzr,.cvs,.git,.hg,.svn}'
grh='git reset HEAD'
grhh='git reset HEAD --hard'
grmv='git remote rename'
grrm='git remote remove'
grset='git remote set-url'
grt='cd $(git rev-parse --show-toplevel || echo ".")'
grup='git remote update'
grv='git remote -v'
gsd='git svn dcommit'
gsps='git show --pretty=short --show-signature'
gsr='git svn rebase'
gss='git status -s'
gst='git status'
gsta='git stash'
gstd='git stash drop'
gstp='git stash pop'
gsts='git stash show --text'
gts='git tag -s'
gunignore='git update-index --no-assume-unchanged'
gunwip='git log -n 1 | grep -q -c "\-\-wip\-\-" && git reset HEAD~1'
gup='git pull --rebase'
gvt='git verify-tag'
gwc='git whatchanged -p --abbrev-commit --pretty=medium'
gwip='git add -A; git ls-files --deleted -z | xargs -r0 git rm; git commit -m "--wip--"'
history='fc -l 1'
l='ls -lah'
la='ls -lAh'
ll='ls -lh'
ls='ls -G'
lsa='ls -lah'
md='mkdir -p'
o='a -e open'
please=sudo
po=popd
pu=pushd
rd=rmdir
run-help=man
s='fasd -si'
sd='fasd -sid'
sf='fasd -sif'
st='open -a "Sublime Text"'
v='f -e vim'
which-command=whence
z='fasd_cd -d'
zz='fasd_cd -d -i'
```

这表明mac的终端其实自带了一些`alias`。当然，我们也可以手动添加。

## 手动添加
自定义的alias应该在终端的配置文件中添加，比如我使用的是zsh，就在`.zshrc`文件中添加。

常用的操作有:
- `alias st='open -a "Sublime Text"'`: 打开sublimeText
