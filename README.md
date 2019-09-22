# ForestBlog

> ForestBlog 是基于 go 语言开发的，不依赖第三方 go 库，适合用来学习和展示 markdown 文档的精美博客。


示例： [xusenlin.com](http://xusenlin.com) （个人博客，正在使用）

源码： [github.com/xusenlin/ForestBlog](https://github.com/xusenlin/ForestBlog)

---  

## 项目背景
博客从最早的静态Html+Css主页到Wordpress 、Typecho 、Hexo 、Hugo 一路尝试过来，虽然他们都是很优秀的开源项目，但是没有一款符合我内心真正的诉求。
他们有的要么太重了要么部署不方便要么对存储的文章不友好，我就放弃了之前在Typecho上的文章，同时调整分类也不那么灵活，有的迁移也不方便。
其实，是自己太懒，不想自己做文章备份，不想安装数据库，快速响应也是必须的。
当然，自己的这个项目并不能和这些优秀的开源项目相比较，它只是符合我自己的诉求顺便用来学习GOLANG的项目。(写文章也能增加github的活跃度，逃 :))


## 安装
你可以克隆并编译源代码来运行你的博客，如果不想自己编译，可以使用下面的二进制包，下载运行即可：
1. win：链接: https://pan.baidu.com/s/1btblaIZGbBED165FJESp0g 提取码: khtv 
2. mac: 
3. linux: 

## 使用

- 请将你的博客文档克隆到ForestBlog的resources目录下，并配置好documentPath字段，
ForestBlog会根据你配置的时间定时切换到你的博客目录下执行git pull 命令来更新你的文章,
所以正确配置documentPath指向你的博客文档很关键。

- 还有，你的博客文档目录里面最少需要assets、content目录和About.md、Works.md文件(未来完成todo这个将不再是强制性的)。
content目录下的一级目录代表一个分类，如果有多个子级目录也不会产生分类,子级的文档也会属于第一级的分类。
如下：
```
    |-- assets       //博客静态文件，存放一些图片资源，方便显示到文档里
    |-- content
    |   |-- GOLANG   //分类目录
    |       |-- GOLANG基础   //  子分类目录，但是在页面上不会产生分类目录
    |       |--- GOLANG基础语法.md   
    |   |-- 其他分类
    |       |--- xxx.md
    |-- About.md    //关于
    |-- Works.md    //作品
    
```


- 在文章的开头可以配置一些文章的属性，我觉得这个应该是必须的，最少也应该有一个日期，否则默认使用文件创建的时间，
当你迁移文档时间就会改变导致文章排序到前面，添加上时间则不会有这个问题。



```
    ```json
    {
        "date":"2019.01.02 14:33"，//最少需要
        "tags": ["BLOG"，"其它tag"]，//可以不填，不过最好添加一些tag，后面可以做一些好玩的东西。
        "title": "文章的标题，一般不用填写，默认使用文件名"，
        "description": "文章描述，不填写自动取正文200个字，可以在app.json中配置"，
        "author": "xusenlin" //文章作者，可以不用填写，现在也没有使用到
    }
    ```
```
我会根据关键字```json来解析，不用担心这个会显示到文章内容里面，我在解析的时候就将它去掉了，同时会生成缓存。
如果不再文章前面添加这一段json也是可以的，不过我不建议这么做，因为这样就和V1.0版本没什么区别了，没有了文章属性，排序都是个问题。
最后，markdown文章编辑器推荐Typora。

> 提示：```json 前面不能有其它字符。

- 切换主题色和搜索文章在仪表盘里，访问/admin 可以查看仪表盘，
如果不想让别人知道你的仪表盘地址可以自己配置dashboardEntrance字段。
更多配置请自行查看app.json



## TODO
- [x] 1.移动端更好的适配
- [ ] 2.根目录可以添加其他文件生成导航
- [x] 3.仪表盘支持切换主题
- [x] 4.仪表盘支持搜索
- [ ] 5.tags的展示
- [x] 6.仪表盘添加手动更新文章功能
- [ ] 7.添加webHook支持(去掉自动更新)
- [ ] 7.单元测试

## 特性

1. 响应迅速  ---没有什么依赖，得益于GOLANG的运行速度，部署在阿里云的博客平均响应在50毫秒内。
2. 迁移方便  ---GOLANG交叉编译可以方便的发布二进制文件到不同的操作系统，执行二进制文件并克隆博客文件即可运行你的博客。
3. 小巧精美  ---非常简单的代码方便学习和改造，即使有一天你厌倦ForestBlog，你的文章也能很好的迁移和阅读。
4. 分类调整  ---随时调整你的文章分类，你可以把一个文件夹里所有的东西移动到其他分类里的某个地方，不管有多少层级，分类发生了什么翻天覆地的变化，下一次更新就能展示。


## License

MIT © Richard McRichface