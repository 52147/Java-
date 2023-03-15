# Github 指令
## git index
git index 是一個暫存區，他在本地資料夾系統與 commit 歷史之間。    
當運行git add 時，在工作目錄中的文件，將被hashed 為一個object，儲存在index中。    
## origin
origin 代表遠程倉庫

## git rebase
```
git rebase <branch_a>
```
重新定義參考基準到branch a。  
https://gitbook.tw/chapters/branch/merge-with-rebase    
## git pull --rebase origin dev
```
git fetch origin dev
git rebase origin/dev
```
https://stackoverflow.com/questions/22335987/what-happens-when-i-git-pull-rebase-origin-development-from-within-a-feature

## checkout
### checkout到新創立的分支後遇到錯誤

```
Git: cannot checkout branch - error: pathspec '...' did not match any file(s) known to git
```
原因：本地repo沒有更新到remote repo的資料   

解決：   
1. 先 git fetch 將remote repo資料，更新到本地repo
2. 再 git checkout branch_name
https://stackoverflow.com/questions/13072111/gits-local-repository-and-remote-repository-confusing-concepts


## 修改已push 到github的 commit message
修改最近三則訊息
```
git rebase -i HEAD^^^
```
或
```
git rebase -i HEAD~n // 把n改成3
```
接著出現以以下3則最近的commit 紀錄：


```bash
pick e499d89 Delete CNAME
pick 0c39034 Better README
pick f7fde4a Change the commit message but push the same commit.

# Rebase 9fdb3bd..f7fde4a onto 9fdb3bd
#
# Commands:
# p, pick = use commit
# r, reword = use commit, but edit the commit message
# e, edit = use commit, but stop for amending
# s, squash = use commit, but meld into previous commit
# f, fixup = like "squash", but discard this commit's log message
# x, exec = run command (the rest of the line) using shell
#
# These lines can be re-ordered; they are executed from top to bottom.
#
# If you remove a line here THAT COMMIT WILL BE LOST.
#
# However, if you remove everything, the rebase will be aborted.
#
# Note that empty commits are commented out
```
如果我要修改0c39034 這條commit message，把他前面的pick改成reword。   
   
步驟：   
 1. 按i 鍵修改
 2. 修改完後按esc鍵退出修改模式
 3. 接著輸入:wq然後按enter代表保存
```bash
pick e499d89 Delete CNAME
reword 0c39034 Better README
pick f7fde4a Change the commit message but push the same commit.

# Rebase 9fdb3bd..f7fde4a onto 9fdb3bd
#
# Commands:
# p, pick = use commit
# r, reword = use commit, but edit the commit message
# e, edit = use commit, but stop for amending
# s, squash = use commit, but meld into previous commit
# f, fixup = like "squash", but discard this commit's log message
# x, exec = run command (the rest of the line) using shell
#
# These lines can be re-ordered; they are executed from top to bottom.
#
# If you remove a line here THAT COMMIT WILL BE LOST.
#
# However, if you remove everything, the rebase will be aborted.
#
# Note that empty commits are commented out
```
接著跳到 修改commit message的頁面：
```bash
Better README // 舊 commit message

# 一些英文說明
# 一些英文說明
# 一些英文說明
```
把原本的commit message 刪除，按i後，輸入新的commit message，按esc退出修改，輸入:wq然後按enter保存，跳回原本的terminal。
```bash
update README // 新 commit message

# 一些英文說明
# 一些英文說明
# 一些英文說明
```
接著重新推入到遠端的repo
```
git push --force
```
https://docs.github.com/en/pull-requests/committing-changes-to-your-project/creating-and-editing-commits/changing-a-commit-message     
https://github.com/ZRuei/notes/issues/1
