传统json格式文件：

1. 从json数组中读取某条记录，需要解析整个json文档

而jsonline格式从语法意义讲不是一个合法的json文档，因为其中包含了太多条json数据

从读写的效率来看，数组类且数据大的情况下，使用jsonline格式会更合理

选择jsonline存储大数据量json结构数据的原因

1. No need do read the whole file in memory before parse. 
2.  You can  easily add further lines to the file by simply appending to the file. If the entire file were a JSON array then you would have to parse it, add  the new line, and then convert back to JSON.

JSON Lines files may be saved with the file extension `.jsonl`.