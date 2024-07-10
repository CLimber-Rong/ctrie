# CTrie

Ctrie是一个基于C标准库的字典树库，采用C语言开发，方便，快捷，简单。
Ctrie包含了[CStack](https://github.com/CLimber-Rong/cstack)项目。

### 使用方法

将``strie.h``和``stack.h``复制到指定目录中。只需``#include "strie.h"``即可开始使用。

### 接口介绍

新建名为trie的字典树指针：``STRIE* trie;``

* ``STRIE* InitTrie();``：初始化树，成功返回地址，失败返回NULL
* ``int SetTrieKeyVal(STRIE* trie,char* key,void* val);``：设置键-值，成功返回1，失败返回0，可以用此接口创建键-值和更改已有键-值
* ``int DelTrieKeyVal(STRIE* trie,char* key);``：删除键-值，成功返回1，失败返回0
* ``void* GetTrieKeyVal(STRIE* trie,char* key);``：根据键获得获得值，成功返回值，失败返回NULL（返回NULL时不排除数据域的指针本来就等于NULL，需配合TrieExistKeyVal()接口判断）
* ``int TrieExistKeyVal(STRIE* trie,char* key);``：键-值是否存在，存在则返回1，不存在则返回0
* ``int ClearTrie(STRIE* trie);``：清空所有键-值，成功返回1，失败返回0
* ``int DestroyTrie(STRIE* trie);``：销毁树，成功返回1，失败返回0
* ``int TrieEmpty(STRIE* trie);``：树是否为空，是则返回1，否则返回0，错误返回-1
* ``int TrieTraverse(STRIE* trie,TRIE_VISIT visit);``对树中所有元素依次调用visit函数，要求visit函数参数为数据，visit返回1代表处理成功，并开始处理下一个元素，返回0代表处理失败，StackTraverse则终止处理并退出，返回成功处理的元素个数。