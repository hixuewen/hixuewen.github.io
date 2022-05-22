实例

```
# 批量修改文件内容
find . -type f -name *.md -print0 | xargs -0 sed -i 's/https:\/\/gitee.com\/hixuewen\/PicLib\/raw\/master/http:\/\/rc6tqm6vc.hn-bkt.clouddn.com/g'
```

