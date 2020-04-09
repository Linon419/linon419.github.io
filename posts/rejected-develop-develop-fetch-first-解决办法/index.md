#  ! [rejected]        develop -> develop (fetch first)解决办法

1、`git pull origin master --allow-unrelated-histories` //把远程仓库和本地同步，消除差异

2、重新add和commit相应文件

3、git push origin develop

4、此时就能够上传成功了
