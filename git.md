# 删除大文件

查看打文件
```
 git rev-list --objects --all |   git cat-file --batch-check='%(objecttype) %(objectname) %(objectsize) %(rest)' |   grep '^blob' |   sort -k3nr |   head -n 20
```

pip install git-filter-repo

git filter-repo --path UpgradeLog.htm --invert-paths --force


git filter-repo --path Framework.Net.Mobile.rar --invert-paths --force
