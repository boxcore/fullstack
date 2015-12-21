Gitbook使用
============

gitbook是写文档利器，目前开发的项目以及公司的操作相关文档也将迁移使用。为方便操作，特记录一份使用说明。需要官方详细的教材可以参考 :[Gitbook 使用入门](http://wanqingwong.com/gitbook-zh/output/pdfandebook.html).

## gitbook的安装和使用

```bash
# 安装gitbook
npm install gitbook -g


gitbook serve
gitbook serve -p 8080 # 指定端口运行
```

文件说明：
1. README.md

2. SUMMARY.md

```
* [FTP](ftp/README.md)
* [项目模板](module/README.md)
    * [PC页面模板](module/pc/index.md)
    * [手机页面模板](module/m/index.md)
* [制作页面相关流程](process/README.md)
* [外包审查流程](process/waibao.md)
* [业务需求](library/README.md)
    * [Jq库](library/jquery.md)
    * 基础类
        * [新闻列表](library/basis/txt-list.md)
        * [图片列表](library/basis/pic-list.md)
        * [新闻切换](library/basis/list-tab.md)
        * [分享组件](library/basis/share.md)
```


