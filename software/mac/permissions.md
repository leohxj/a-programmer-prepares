# 权限问题
如果有过linux基础的人，就会明白这个权限问题。其实*nix的系统，都是一个root用户，然后自己创建其他用户使用。用户和用户之前通过权限互相独立。

对一般的用户而言，不需要太关注这个权限问题，但是对程序员来说，这一点应该是必知必会的。不然我们常常会被`npm install -g xx`出现的报错而不知所措。

## root：“超级用户”
在 Mac OS X 中，在安装系统时将会创建一个名为 root 的超级用户。 root 用户对计算机上的所有文件和文件夹都有完全的访问权限，并且还具有一般用户没有的其他管理访问权限。在计算机的正常使用中，您并不需要以 root 用户的身份登录。事实上，默认情况下， root 用户是被禁用的。

## 普通用户
mac系统创建的用户，会和root在一个group中，一般叫做`staff`或者`admin`。root用户的权限高于其他用户。


## 定义的权限
- 读取 (r--)
- 写入 (-w-)
- 执行 (--x)

当您可以做到所有三种操作时，您就拥有了“rwx”权限。文件夹的权限与此类似。具有内含文档的文件夹的只读权限，您可以打开和读取其中的文档，但不能保存对该文件夹所做的更改，也不能为该文件夹添加新的文档。只读 (r--) 权限是常用于客户访问的文件共享。

## 所有者、组、其他
像“rwx”和“r-x”这样的简写描述了一个用户或一个实体的权限。每个文件或文件夹的权限设置都定义了三个实体的访问能力：所有者、组和其他。

- 所有者: 所有者通常是创建该文件的用户。在您的 root 目录下的几乎所有文件和文件夹都将您的用户名列作所有者。
- 组: Admin 用户就是一些被称为“staff”和“admin”的组的成员。超级用户“root”是这些及其他一些组的成员。通常情况下，所有文件和文件夹都被分配到“staff”、“admin”或“wheel”等组中。
- 其他: 其他是指某个文件或文件夹的所有者或组成员之外的其他所有用户。

因为每个实体都有其自己的权限，如一个完整的权限组可能为“-rwxrw-r--”。前面的连字符指定该项目是一个文件而不是文件夹。文件夹的权限以“d”开头，如“drwxrw-r--”。“d”代表 directory（目录），表示文件夹。

## 使用 Terminal 查看权限
在终端中输入`list -l`，你会得到类似如下的信息:

```
total 0
drwx------   6 leohxj  staff   204B Jan 27 21:50 Applications
drwx------+  3 leohxj  staff   102B Mar 11 14:54 Desktop
drwx------+  7 leohxj  staff   238B Jan 18 22:11 Documents
drwx------+  5 leohxj  staff   170B Mar 10 23:39 Downloads
drwx------@ 16 leohxj  staff   544B Mar 11 14:54 Dropbox
drwx------@ 62 leohxj  staff   2.1K Jan 17 23:22 Library
drwx------+  4 leohxj  staff   136B Jan  3 21:37 Movies
drwx------+  7 leohxj  staff   238B Jan  6 09:45 Music
drwx------+  8 leohxj  staff   272B Feb  7 15:23 Pictures
drwxr-xr-x+  6 leohxj  staff   204B Jan  6 10:28 Public
```

- `drwx------ `：这一段是对文件或者目录的用户权限描述，d代表目录，后面九个字符，每三个为一组，代表所有者，组成员和其他用户。
- `leohxj`：这一栏表示所有者。
- `staff`: 这一栏表示所在组。


## 参考资料
- [Mac OS X 中权限问题的故障排除](https://support.apple.com/zh-cn/HT2963)

