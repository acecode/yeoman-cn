## 部署你的应用

当你运行 ```grunt build``` 后，它会在 ```dist``` 目录中为你的应用生成一个完整的，优化过的可部署版本。

部署 ```dist``` 目录的推荐方式是使用 ```git subtree```。

1. 从 ```.gitignore``` 文件中移除 ```dist```目录。


2. 添加 ```dist``` 目录到你的代码仓库中并且随着你的项目提交。

   ```
   git add dist && git commit -m "Initial dist subtree commit"
   ```

3. 一旦 ```dist``` 目录成为了你项目的一部分，我们可以使用 [```git subtree```](https://github.com/apenwarr/git-subtree) 来设置一个独立的代码仓库到一个另外的分支上。

   ```
   // 部署dist到GitHub Pages
   git subtree push --prefix dist origin gh-pages
   ```

   注意: prefix必须是相对你 ```dist``` 目录的相对路径。这里假设 ```dist``` 是你的根目录。


4. 现在你可以提交你的整个代码仓库到你的默认的（master）分支上，当你想要部署 ```dist``` 目录的时候你可以运行：

   ```
   git subtree push --prefix dist origin gh-pages
   ```

### 一些常见错误
 * 在默认情况下，```dist``` 目录将会被git命令忽略，从.gitignore文件中移除它是很重要的。
 * 你必须在运行git subtree命令前先提交你的 ```dist``` 目录到默认的（master）分支。
 * ```git subtree``` 命令必须从根目录进行调用。
 * ```--prefix``` 选项必须是相对于你 ```dist``` 目录的相对路径。
 * GitHub Pages使用 ```gh-pages``` 分支来部署项目页面。用户或者组织页面使用 ```master``` 分支。这意味着你有可能会使用master作为你的subtree分支，并且为你的应用源码设置一个不同的分支。
 * 你可能会得到一个像这样的错误 `Updates were rejected because the tip of your current branch is behind`。你可以通过[强制推送到远程](http://stackoverflow.com/a/13403588/64949) 解决它（但是请小心一点，它将会销毁那儿已经存在的所有文件）。


### 额外的资料
 [Git Subtree 文档](https://github.com/git/git/blob/master/contrib/subtree/git-subtree.txt)

 [Yeoman Build](https://github.com/yeoman/yeoman/wiki/yeoman-build)

 [Github Pages](https://help.github.com/articles/user-organization-and-project-pages)

 [generator-heroku](https://github.com/passy/generator-heroku)