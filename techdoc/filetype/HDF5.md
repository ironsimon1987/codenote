# HDF5

What:一种文件格式

应用场景:
1. 存储大量数据，而txt文件效率不高
2. 快速访问数据的子集


HDF5文件内自成体系，你可以理解这个文件的内部世界里包含有文件夹和子文件夹。


## python操作

module:h5py
其中一个特征：当需要某一块数据时，才会从文件中读取该数据，而不是全部加载。如当你有很大的数组，而你的设备的可用RAM内存无法满足。

例如，你可以在一台具有不同于“用于分析数据的计算机”规格配置的计算机生成该数组。
HDF5格式允许您使用与numpy相同的语法去选择要读取数组中的哪些元素
然后，你可以处理存储在硬盘上而不是RAM内存中的数据，而无需对现有的代码进行太多修改


When we assigned f['default'] to the variable data we are not actually reading the data from the file, instead, we are generating a pointer to where the data is located on the hard drive. 

