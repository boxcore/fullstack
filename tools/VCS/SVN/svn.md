SVN常用操作命令
================
@(tools)[svn, 版本控制]

[TOC]

### 1. svn检出
- `svn checkout {svn地址} {本地目录}`, 简写：`svn co`
- `svn co --username="boxcore" --password='xxx' svn://192.168.1.1/xx /www/xx`: 使用账号检出svn代码到指定目录



### 2. 添加文件
- `svn add file1 file2 ...`

### 3. 提交版本
- `svn commit -m "描述"`
- ` svn commit -m "LogMessage" [-N] [--no-unlock] PATH `(如果选择了保持锁，就使用--no-unlock开关)

### 4. 查看svn历史
- `svn log svn://svn.test.co/foo/`
- `svn log -c 版本`


### 5. 更新到某个版本
语法： `svn update -r {version} {path}`。简写是`svn up`


#### 文件和目录的修改还原
- `svn revert PATH...`
> 恢复所有对文件和目录的修改，并且解决所有的冲突状态。svn revert不会只是恢复工作拷贝中一个项目的内容，也包括了对属性修改的恢复。最终，你可以使用它来取消所有已经做过的预定操作（例如，文件预定要添加或删除可以“恢复”）。 

- `svn revert index.php`  丢弃对一个文件的修改
- `svn revert --recursive .`  恢复一整个目录的文件，可以使用--recursive选项
- `svn update -r 200 test.php` 还原到以前版本(将版本库中的文件test.php还原到版本200) 

### 列出本地与SVN当前版本差异 
`svn status -v path`(显示文件和子目录状态) 
简写：`svn st `
第一列保持相同，第二列显示工作版本号，第三和第四列显示最后一次修改的版本号和修改人。 
另外，可执行`script -q tty.log`后,就开始记录终端的输入输出信息,结束的时候按ctrl+D即可得到终端的内容文件tty.log 

### svn比较差异 
`svn diff path` 将修改的文件与基础版本比较
例如：
- `svn diff test.php `
- `svn diff -r m:n path` 对版本m和版本n比较差异

### svn排除文件
`svn propget svn:ignore` 查看过滤的文件和目录

此方法只适用于 未加入版本管理的文件。
可先将svn 版本里的文件先删除，再重新导入，使得文件未加入版本管理

已经在版本控制的目录或者文件是不能加入svn:ignore，加入了也无效，如果要加入，必须先删除然后commit,然后再加入

执行命令:
```bash
svn st
export SVN_EDITOR=vim #设置SVN的默认编辑器为vim
svn propedit svn:ignore .
svn commit -m "ignore the file"
```

### svn代码回滚命令
取消对代码的修改可分2种情况：
第一种情况：**改动没有被提交（commit）**的时候可以使用svn revert：
```bash
svn revert filename
svn revert -R dirname
```

第二种情况：**改动已经被提交（commit）**则需要用svn merge命令来进行回滚：
```bash
svn update
svn log [your version]
svn diff -r v10:v2 filename
svn merge -r v10:v2 filename
svn commit -m "Revert revision from v10 to v2,because of ..." 
```




> 注：svn status、svn diff和 svn revert这三条命令在没有网络的情况下也可以执行的，原因是svn在本地的.svn中保留了本地版本的原始拷贝。 


svn解决冲突
-----------
`svn resolved`
