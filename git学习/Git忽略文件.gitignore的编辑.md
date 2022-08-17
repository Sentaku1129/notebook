# Git ignore的编辑使用

## 为什么使用.ignore

当我们使用'git add .'的时候,不想将某些文件或文件夹的内容添加到缓存中时,可以使用.gitignore文件,这可以使我们忽略掉.ignore中的声明的文件或文件夹.

## 忽略文件原则

- 忽略系统自动生成的文件,如缩略图等;
- 忽略编译生成的中间文件,可执行文件等.例如C语言生成的.O文件;
- 忽略带有自己信息的配置文件,如token等配置文件;

## 例子

> 例如你的项目是51单片机的项目,C语言文件编译之后会生成.hex,.o等文件,这时候不想将这些文件上传到仓库中去,就可以直接使用.gitignore文件忽略

### 部分示例
    *.rar
    *.o
    *.d
    *.uvguix.*
    .mxproject
    .gitignore
    RTE/
    Templates/
    Examples/
    !*.uvprojx
    !*.h
    !*.c
    !*.hex

> 例如说我们想忽略掉hello_world.o文件我们可以在.gitignore文件中添加如下配置:

    hello_world.o

> 或者说想忽略所有的.o文件,可以添加如下配置:

    *.o

### 强制添加

> 像上面我们将hello_world.o文件给忽略了,当我们使用git add时是无法添加的,会提示我们使用-f才能强制添加

    $ git add hello_world.o
    The following paths are ignored by one of your .gitignore files:
    hello_world.o
    hint: Use -f if you really want to add them.
    hint: Turn this message off by running
    hint: "git config advice.addIgnoredFile false"

> 如果我们不小心添加可以使用git rm 文件名 --cached将其删除

    $ git rm hello_world.o --cached
    rm 'hello_world.o'

> 如果不小心上传了不想上传的文件,我们可以先将远程仓库的文件删除了,再pull到本地;或者删除本地的再push到远程仓库

## 查看gitignore规则

> 如果发现.gitignore有问题,我们可以使用git check-ignore命令检查

    $ git vheck-ignore -v hello_world.o
    .gitignore:1:hello_world.o hello_world.o

>> 可以看到输出说明在.gitignore文件中的第一行的匹配规则hello_world.o与我们所要检查的文件hello_world.o相匹配,而将文件忽略了

## 忽略规则文件语法

### 忽略指定的文件/目录

    #忽略指定文件
    hello_world.o

    #忽略指定文件夹
    bin/
    bin/gdb/

### 通配符忽略规则

    #忽略所有的.o文件
    *.o

    #忽略名称中间有o的文件
    *o*

    #忽略以ignore结尾的文件夹
    *ignore/

    #忽略名称中间含有ignore的文件夹
    *ignore*/
