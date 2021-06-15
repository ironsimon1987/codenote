# Commands



命令行使用指定应用程序打开文件

```
open -a "typora" techdoc/dev_env_config/mac/命令行工具.md 
```

命令行打开当前目录

```
open .
jo <folder>
```



**复制和粘贴**

```
pbcopy < input.txt
pbpaste > output.txt
```

`pbpaste`与 `jq`搭配使用

```
pbpaste | jq '.'
```


## jq


[https://stedolan.github.io/jq/manual/#TypesandValues](https://stedolan.github.io/jq/manual/#TypesandValues)






## tree

中文乱码

```
tree -N
```

命令行打印文件夹结构

```
# L 指定只打印的层数
tree -N -L 2
```

只打印文件夹

```
tree -d
```



