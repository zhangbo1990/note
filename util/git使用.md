
# git使用

## …or create a new repository on the command line
echo "# note" >> README.md  
git init  
git add README.md  
git commit -m "first commit"  
git remote add origin    https://github.com/zhangbo1990/note.git  
git push -u origin master  

## …or push an existing repository from the command line  

git remote add origin https://github.com/zhangbo1990/note.git
git push -u origin master


## Git tag
新功能上线前，这之前的发布版本打tag已被上线bug回退
  
  - git checkout master
  - git tag -a master_20190911_tag -m 'xxx备份'
  - git tag 
  - git show master_20190911_tag //tag详情
  - git reset --hard xxxsasa(commit id)//回退
  - git reflog //查看log 包括reset记录
  - git push -f origin master //回滚后  因为落后一个版本  要强制更新