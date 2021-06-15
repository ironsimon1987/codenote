# cat

refer [Writing Text to File Using Linux Cat Command](https://www.baeldung.com/linux/cat-writing-file)

合并文件
```
> cat part1 part2 >> test.txt
```

## 写文件

Note: `>` 覆盖文件内容， 而`>>`追加文件内容

```
cat > readme.txt
```

使用标志符告知程序输出结束
```
cat >> test3.md << EOF
```