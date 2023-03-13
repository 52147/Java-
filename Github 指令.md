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
原因：本地repo沒有更新到remote repo的資料.   

解決：   
1. 先 git fetch 將remote repo資料，更新到本地repo
2. 再 git checkout branch_name
https://stackoverflow.com/questions/13072111/gits-local-repository-and-remote-repository-confusing-concepts
