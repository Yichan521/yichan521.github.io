# 关于hugo搭建个人博客可能会遇到的一些问题


还是更推荐大家去 loveit 官网学习，那里的知识更全面更专业……

不过肯定有人看不懂，导致在网上找教程也找不到……比如我，所以写此篇来记录我博客搭建过程中遇到的问题。

本篇持续更新，直至我彻底完善我的博客（那当然是不可能的）

我尽量压制我说废话的欲望，让本文尽量精简。

###### 1. 插入图片的问题！

首先是利用网页链接来上传图片。

你可以在[将本地图片转为网页连接的网站](https://postimages.org/)将你的图片上传，这样就可以得到图片的网页连接，这样你直接在自己的博客里利用 markdown 插入图片即可，不会遇到什么阻力。

其次你可以通过利用相对路径的方法来上传图片，优点是不需要把图片转为网页链接，操作简单。

我们需要在博客文件夹的 static 目录下创建 images 文件夹，然后直接把我们想要上传的图片复制到 images 文件夹就可以了。

相对路径是图片相对于文档的路径，想要插入图片我们可以使用类似下图的格式：

![](/images/1709963827948.jpg)

中间方括号的内容是对图片的描述，如果觉得麻烦可以不写。

不光只有使用 markdown 语法添加图片的方法，你也可以使用 shortcodes 来插入图片

```
{{</* figure src="/path/to/image.jpg" alt="Alt text" caption="Image caption" */>}}

```

类似于使用 markdown 的方法，你可以选择使用网页链接或者相对路径的方法来上传图片。
