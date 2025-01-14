# hugo搭建个人博客笔记


1. windows 电脑安装 hugo

   首先进入<https://github.com/gohugoio/hugo/releases>，选择自己电脑对应的版本下载，我这里下载的是

   ![](/images/1709873461219.png)

   安装并解压，这里我选择把它解压到 D:\hugo\bin，可自行创建对应文件夹。

   接下来需要配置环境变量，鼠标右键我的电脑-属性-高级系统设置-环境变量-系统变量-双击 path-新建，然后将 hugo.exe 的位置输入进去，这里我输入的就是”D:\hugo\bin“。

   win+R，输入 cmd，进入终端。在终端输入

   ```
   hugo new site（你希望设置的博客名字）
   ```

   这里我使用的博客名字是 chanke，所以输入的是

   ```
   hugo new site chanke
   ```

   然后你可以发现在 C 盘-user-（你电脑名字那个文件夹）可以找到以你博客名字命名的文件夹

   ![70987375116](/images/1709873751164.png)

   [^]: 这里我把文件夹创建到了自己建的新文件夹内，便于展示。

   同时可以看到终端出现这样的内容：

   ![70987399783](/images/1709873997832.png)

   恭喜你！你的 hugo 站点创建成功~

2. 使用 hugo 初步建立静态网站，使用 loveit 作为主题

   首先去 hugo 官网给自己的博客下载主题：<https://themes.gohugo.io/>，我这里选择的是 loveit 主题，简洁优雅，另一个主要原因是我看的视频是用这个来演示的，别的主题我不会用。

   下载 loveit：<https://github.com/dillonzq/LoveIt>，点击绿色的 code 按钮，选择 download zip，下载解压，把解压得到的文件夹放入你的博客同名文件夹下的"theme"[^1]中。

   ### 请务必注意！解压得到的文件名字应该是 loveit-master，我们需要把"-master"删掉！否则 hugo 会找不到你的主题！

   [^1]: 比如说我的博客名字叫 Chanke，就要去 Chanke 文件夹里找，不出意外的话这个文件夹一般都在 C 盘-user-xxx 里面

   进入 loveit 网站：<https://hugoloveit.com/zh-cn/theme-documentation-basics/#site-configuration>

   右上角可以自行更改语言，我们略过前面的步骤直接从 2.4 开始，在此之前先复制下面的代码块到博客文件夹内的 toml 后缀文件中，替换掉原本的内容

   ```
   baseURL = "http://example.org/"

   # 更改使用 Hugo 构建网站时使用的默认主题
   theme = "LoveIt"

   # 网站标题
   title = "我的全新 Hugo 网站"

   # 网站语言, 仅在这里 CN 大写 ["en", "zh-CN", "fr", "pl", ...]
   languageCode = "zh-CN"
   # 语言名称 ["English", "简体中文", "Français", "Polski", ...]
   languageName = "简体中文"
   # 是否包括中日韩文字
   hasCJKLanguage = true

   # 作者配置
   [author]
     name = "xxxx"
     email = ""
     link = ""

   # 菜单配置
   [menu]
     [[menu.main]]
       weight = 1
       identifier = "posts"
       # 你可以在名称 (允许 HTML 格式) 之前添加其他信息, 例如图标
       pre = ""
       # 你可以在名称 (允许 HTML 格式) 之后添加其他信息, 例如图标
       post = ""
       name = "文章"
       url = "/posts/"
       # 当你将鼠标悬停在此菜单链接上时, 将显示的标题
       title = ""
     [[menu.main]]
       weight = 2
       identifier = "tags"
       pre = ""
       post = ""
       name = "标签"
       url = "/tags/"
       title = ""
     [[menu.main]]
       weight = 3
       identifier = "categories"
       pre = ""
       post = ""
       name = "分类"
       url = "/categories/"
       title = ""
   # Hugo 解析文档的配置
   [markup]
     # 语法高亮设置
     [markup.highlight]
       codeFences = true
       guessSyntax = true
       lineNos = true
       lineNumbersInTable = true
       # false 是必要的设置
       # (https://github.com/dillonzq/LoveIt/issues/158)
       noClasses = false

   baseURL = "http://example.org/"

   # 更改使用 Hugo 构建网站时使用的默认主题
   theme = "LoveIt"

   # 网站标题
   title = "我的全新 Hugo 网站"

   # 网站语言, 仅在这里 CN 大写 ["en", "zh-CN", "fr", "pl", ...]
   languageCode = "zh-CN"
   # 语言名称 ["English", "简体中文", "Français", "Polski", ...]
   languageName = "简体中文"
   # 是否包括中日韩文字
   hasCJKLanguage = true

   # 默认每页列表显示的文章数目
   paginate = 12
   # 谷歌分析代号 [UA-XXXXXXXX-X]
   googleAnalytics = ""
   # 版权描述，仅仅用于 SEO
   copyright = ""

   # 是否使用 robots.txt
   enableRobotsTXT = true
   # 是否使用 git 信息
   enableGitInfo = true
   # 是否使用 emoji 代码
   enableEmoji = true

   # 忽略一些构建错误
   ignoreErrors = ["error-remote-getjson", "error-missing-instagram-accesstoken"]

   [params]
     # 网站默认主题样式 ["auto", "light", "dark"]
     defaultTheme = "auto"
     # 公共 git 仓库路径，仅在 enableGitInfo 设为 true 时有效
     gitRepo = ""
     #  哪种哈希函数用来 SRI, 为空时表示不使用 SRI
     # ["sha256", "sha384", "sha512", "md5"]
     fingerprint = ""
     #  日期格式
     dateFormat = "2006-01-02"
     # 网站标题, 用于 Open Graph 和 Twitter Cards
     title = "我的网站"
     # 网站描述, 用于 RSS, SEO, Open Graph 和 Twitter Cards
     description = "这是我的全新 Hugo 网站"
     # 网站图片, 用于 Open Graph 和 Twitter Cards
     images = ["/logo.png"]

     # 页面头部导航栏配置
     [params.header]
       # 桌面端导航栏模式 ["fixed", "normal", "auto"]
       desktopMode = "fixed"
       # 移动端导航栏模式 ["fixed", "normal", "auto"]
       mobileMode = "auto"
       #  页面头部导航栏标题配置
       [params.header.title]
         # LOGO 的 URL
         logo = ""
         # 标题名称
         name = ""
         # 你可以在名称 (允许 HTML 格式) 之前添加其他信息, 例如图标
         pre = ""
         # 你可以在名称 (允许 HTML 格式) 之后添加其他信息, 例如图标
         post = ""
         #  是否为标题显示打字机动画
         typeit = false

     # 页面底部信息配置
     [params.footer]
       enable = true
       #  自定义内容 (支持 HTML 格式)
       custom = ''
       #  是否显示 Hugo 和主题信息
       hugo = true
       #  是否显示版权信息
       copyright = true
       #  是否显示作者
       author = true
       # 网站创立年份
       since = 2019
       # ICP 备案信息，仅在中国使用 (支持 HTML 格式)
       icp = ""
       # 许可协议信息 (支持 HTML 格式)
       license = '<a rel="license external nofollow noopener noreffer" href="https://creativecommons.org/licenses/by-nc/4.0/" target="_blank">CC BY-NC 4.0</a>'

     #  Section (所有文章) 页面配置
     [params.section]
       # section 页面每页显示文章数量
       paginate = 20
       # 日期格式 (月和日)
       dateFormat = "01-02"
       # RSS 文章数目
       rss = 10

     #  List (目录或标签) 页面配置
     [params.list]
       # list 页面每页显示文章数量
       paginate = 20
       # 日期格式 (月和日)
       dateFormat = "01-02"
       # RSS 文章数目
       rss = 10

     #  应用图标配置
     [params.app]
       # 当添加到 iOS 主屏幕或者 Android 启动器时的标题, 覆盖默认标题
       title = "我的网站"
       # 是否隐藏网站图标资源链接
       noFavicon = false
       # 更现代的 SVG 网站图标, 可替代旧的 .png 和 .ico 文件
       svgFavicon = ""
       # Android 浏览器主题色
       themeColor = "#ffffff"
       # Safari 图标颜色
       iconColor = "#5bbad5"
       # Windows v8-10磁贴颜色
       tileColor = "#da532c"

     #  搜索配置
     [params.search]
       enable = true
       # 搜索引擎的类型 ["lunr", "algolia"]
       type = "lunr"
       # 文章内容最长索引长度
       contentLength = 4000
       # 搜索框的占位提示语
       placeholder = ""
       #  最大结果数目
       maxResultLength = 10
       #  结果内容片段长度
       snippetLength = 50
       #  搜索结果中高亮部分的 HTML 标签
       highlightTag = "em"
       #  是否在搜索索引中使用基于 baseURL 的绝对路径
       absoluteURL = false
       [params.search.algolia]
         index = ""
         appID = ""
         searchKey = ""

     # 主页配置
     [params.home]
       #  RSS 文章数目
       rss = 10
       # 主页个人信息
       [params.home.profile]
         enable = true
         # Gravatar 邮箱，用于优先在主页显示的头像
         gravatarEmail = ""
         # 主页显示头像的 URL
         avatarURL = "/images/avatar.png"
         #  主页显示的网站标题 (支持 HTML 格式)
         title = ""
         # 主页显示的网站副标题 (允许 HTML 格式)
         subtitle = "这是我的全新 Hugo 网站"
         # 是否为副标题显示打字机动画
         typeit = true
         # 是否显示社交账号
         social = true
         #  免责声明 (支持 HTML 格式)
         disclaimer = ""
       # 主页文章列表
       [params.home.posts]
         enable = true
         # 主页每页显示文章数量
         paginate = 6
         #  被 params.page 中的 hiddenFromHomePage 替代
         # 当你没有在文章前置参数中设置 "hiddenFromHomePage" 时的默认行为
         defaultHiddenFromHomePage = false

     # 作者的社交信息设置
     [params.social]
       GitHub = "xxxx"
       Linkedin = ""
       Twitter = "xxxx"
       Instagram = "xxxx"
       Facebook = "xxxx"
       Telegram = "xxxx"
       Medium = ""
       Gitlab = ""
       Youtubelegacy = ""
       Youtubecustom = ""
       Youtubechannel = ""
       Tumblr = ""
       Quora = ""
       Keybase = ""
       Pinterest = ""
       Reddit = ""
       Codepen = ""
       FreeCodeCamp = ""
       Bitbucket = ""
       Stackoverflow = ""
       Weibo = ""
       Odnoklassniki = ""
       VK = ""
       Flickr = ""
       Xing = ""
       Snapchat = ""
       Soundcloud = ""
       Spotify = ""
       Bandcamp = ""
       Paypal = ""
       Fivehundredpx = ""
       Mix = ""
       Goodreads = ""
       Lastfm = ""
       Foursquare = ""
       Hackernews = ""
       Kickstarter = ""
       Patreon = ""
       Steam = ""
       Twitch = ""
       Strava = ""
       Skype = ""
       Whatsapp = ""
       Zhihu = ""
       Douban = ""
       Angellist = ""
       Slidershare = ""
       Jsfiddle = ""
       Deviantart = ""
       Behance = ""
       Dribbble = ""
       Wordpress = ""
       Vine = ""
       Googlescholar = ""
       Researchgate = ""
       Mastodon = ""
       Thingiverse = ""
       Devto = ""
       Gitea = ""
       XMPP = ""
       Matrix = ""
       Bilibili = ""
       Discord = ""
       DiscordInvite = ""
       Lichess = ""
       ORCID = ""
       Pleroma = ""
       Kaggle = ""
       MediaWiki= ""
       Plume = ""
       HackTheBox = ""
       RootMe= ""
       Phone = ""
       Email = "xxxx@xxxx.com"
       RSS = true #

     #  文章页面全局配置
     [params.page]
       #  是否在主页隐藏一篇文章
       hiddenFromHomePage = false
       #  是否在搜索结果中隐藏一篇文章
       hiddenFromSearch = false
       #  是否使用 twemoji
       twemoji = false
       # 是否使用 lightgallery
       lightgallery = false
       #  是否使用 ruby 扩展语法
       ruby = true
       #  是否使用 fraction 扩展语法
       fraction = true
       #  是否使用 fontawesome 扩展语法
       fontawesome = true
       # 是否在文章页面显示原始 Markdown 文档链接
       linkToMarkdown = true
       #  是否在 RSS 中显示全文内容
       rssFullText = false
       #  目录配置
       [params.page.toc]
         # 是否使用目录
         enable = true
         #  是否保持使用文章前面的静态目录
         keepStatic = true
         # 是否使侧边目录自动折叠展开
         auto = true
       #  代码配置
       [params.page.code]
         # 是否显示代码块的复制按钮
         copy = true
         # 默认展开显示的代码行数
         maxShownLines = 50
       #  KaTeX 数学公式
       [params.page.math]
         enable = true
         #  默认行内定界符是 $ ... $ 和 \( ... \)
         inlineLeftDelimiter = ""
         inlineRightDelimiter = ""
         #  默认块定界符是 $$ ... $$, \[ ... \],  \begin{equation} ... \end{equation} 和一些其它的函数
         blockLeftDelimiter = ""
         blockRightDelimiter = ""
         # KaTeX 插件 copy_tex
         copyTex = true
         # KaTeX 插件 mhchem
         mhchem = true
       #  Mapbox GL JS 配置
       [params.page.mapbox]
         # Mapbox GL JS 的 access token
         accessToken = ""
         # 浅色主题的地图样式
         lightStyle = "mapbox://styles/mapbox/light-v10?optimize=true"
         # 深色主题的地图样式
         darkStyle = "mapbox://styles/mapbox/dark-v10?optimize=true"
         # 是否添加 NavigationControl
         navigation = true
         # 是否添加 GeolocateControl
         geolocate = true
         # 是否添加 ScaleControl
         scale = true
         # 是否添加 FullscreenControl
         fullscreen = true
       #  文章页面的分享信息设置
       [params.page.share]
         enable = true
         Twitter = true
         Facebook = true
         Linkedin = false
         Whatsapp = false
         Pinterest = false
         Tumblr = false
         HackerNews = true
         Reddit = false
         VK = false
         Buffer = false
         Xing = false
         Line = true
         Instapaper = false
         Pocket = false
         Flipboard = false
         Weibo = true
         Blogger = false
         Baidu = false
         Odnoklassniki = false
         Evernote = false
         Skype = false
         Trello = false
         Mix = false
       #  评论系统设置
       [params.page.comment]
         enable = false
         # Disqus 评论系统设置
         [params.page.comment.disqus]
           #
           enable = false
           # Disqus 的 shortname，用来在文章中启用 Disqus 评论系统
           shortname = ""
         # Gitalk 评论系统设置
         [params.page.comment.gitalk]
           #
           enable = false
           owner = ""
           repo = ""
           clientId = ""
           clientSecret = ""
         # Valine 评论系统设置
         [params.page.comment.valine]
           enable = false
           appId = ""
           appKey = ""
           placeholder = ""
           avatar = "mp"
           meta= ""
           pageSize = 10
           # 为空时自动适配当前主题 i18n 配置
           lang = ""
           visitor = true
           recordIP = true
           highlight = true
           enableQQ = false
           serverURLs = ""
           #  emoji 数据文件名称, 默认是 "google.yml"
           # ["apple.yml", "google.yml", "facebook.yml", "twitter.yml"]
           # 位于 "themes/LoveIt/assets/lib/valine/emoji/" 目录
           # 可以在你的项目下相同路径存放你自己的数据文件:
           # "assets/lib/valine/emoji/"
           emoji = ""
         # Facebook 评论系统设置
         [params.page.comment.facebook]
           enable = false
           width = "100%"
           numPosts = 10
           appId = ""
           # 为空时自动适配当前主题 i18n 配置
           languageCode = "zh_CN"
         #  Telegram Comments 评论系统设置
         [params.page.comment.telegram]
           enable = false
           siteID = ""
           limit = 5
           height = ""
           color = ""
           colorful = true
           dislikes = false
           outlined = false
         #  Commento 评论系统设置
         [params.page.comment.commento]
           enable = false
         #  utterances 评论系统设置
         [params.page.comment.utterances]
           enable = false
           # owner/repo
           repo = ""
           issueTerm = "pathname"
           label = ""
           lightTheme = "github-light"
           darkTheme = "github-dark"
         # giscus comment 评论系统设置 (https://giscus.app/zh-CN)
         [params.page.comment.giscus]
           # 你可以参考官方文档来使用下列配置
           enable = false
           repo = ""
           repoId = ""
           category = "Announcements"
           categoryId = ""
           # 为空时自动适配当前主题 i18n 配置
           lang = ""
           mapping = "pathname"
           reactionsEnabled = "1"
           emitMetadata = "0"
           inputPosition = "bottom"
           lazyLoading = false
           lightTheme = "light"
           darkTheme = "dark"
       #  第三方库配置
       [params.page.library]
         [params.page.library.css]
           # someCSS = "some.css"
           # 位于 "assets/"
           # 或者
           # someCSS = "https://cdn.example.com/some.css"
         [params.page.library.js]
           # someJavascript = "some.js"
           # 位于 "assets/"
           # 或者
           # someJavascript = "https://cdn.example.com/some.js"
       #  页面 SEO 配置
       [params.page.seo]
         # 图片 URL
         images = []
         # 出版者信息
         [params.page.seo.publisher]
           name = ""
           logoUrl = ""

     #  TypeIt 配置
     [params.typeit]
       # 每一步的打字速度 (单位是毫秒)
       speed = 100
       # 光标的闪烁速度 (单位是毫秒)
       cursorSpeed = 1000
       # 光标的字符 (支持 HTML 格式)
       cursorChar = "|"
       # 打字结束之后光标的持续时间 (单位是毫秒, "-1" 代表无限大)
       duration = -1

     # 网站验证代码，用于 Google/Bing/Yandex/Pinterest/Baidu
     [params.verification]
       google = ""
       bing = ""
       yandex = ""
       pinterest = ""
       baidu = ""

     #  网站 SEO 配置
     [params.seo]
       # 图片 URL
       image = ""
       # 缩略图 URL
       thumbnailUrl = ""

     #  网站分析配置
     [params.analytics]
       enable = false
       # Google Analytics
       [params.analytics.google]
         id = ""
         # 是否匿名化用户 IP
         anonymizeIP = true
       # Fathom Analytics
       [params.analytics.fathom]
         id = ""
         # 自行托管追踪器时的主机路径
         server = ""
       # Plausible Analytics
       [params.analytics.plausible]
         dataDomain = ""
       # Yandex Metrica
       [params.analytics.yandexMetrica]
         id = ""

     #  Cookie 许可配置
     [params.cookieconsent]
       enable = true
       # 用于 Cookie 许可横幅的文本字符串
       [params.cookieconsent.content]
         message = ""
         dismiss = ""
         link = ""

     #  第三方库文件的 CDN 设置
     [params.cdn]
       # CDN 数据文件名称, 默认不启用
       # ["jsdelivr.yml"]
       # 位于 "themes/LoveIt/assets/data/cdn/" 目录
       # 可以在你的项目下相同路径存放你自己的数据文件:
       # "assets/data/cdn/"
       data = ""

     #  兼容性设置
     [params.compatibility]
       # 是否使用 Polyfill.io 来兼容旧式浏览器
       polyfill = false
       # 是否使用 object-fit-images 来兼容旧式浏览器
       objectFit = false

     # Goldmark 是 Hugo 0.60 以来的默认 Markdown 解析库
     [markup.goldmark]
       [markup.goldmark.extensions]
         definitionList = true
         footnote = true
         linkify = true
         strikethrough = true
         table = true
         taskList = true
         typographer = true
       [markup.goldmark.renderer]
         # 是否在文档中直接使用 HTML 标签
         unsafe = true
     # 目录设置
     [markup.tableOfContents]
       startLevel = 2
       endLevel = 6

   # 网站地图配置
   [sitemap]
     changefreq = "weekly"
     filename = "sitemap.xml"
     priority = 0.5

   # Permalinks 配置
   [Permalinks]
     # posts = ":year/:month/:filename"
     posts = ":filename"

   # 隐私信息配置
   [privacy]
     #  Google Analytics 相关隐私 (被 params.analytics.google 替代)
     [privacy.googleAnalytics]
       # ...
     [privacy.twitter]
       enableDNT = true
     [privacy.youtube]
       privacyEnhanced = true

   # 用于输出 Markdown 格式文档的设置
   [mediaTypes]
     [mediaTypes."text/plain"]
       suffixes = ["md"]

   # 用于输出 Markdown 格式文档的设置
   [outputFormats.MarkDown]
     mediaType = "text/plain"
     isPlainText = true
     isHTML = false

   # 用于 Hugo 输出文档的设置
   [outputs]
     #
     home = ["HTML", "RSS", "JSON"]
     page = ["HTML", "MarkDown"]
     section = ["HTML", "RSS"]
     taxonomy = ["HTML", "RSS"]
     taxonomyTerm = ["HTML"]
   ```

   这里按网上的教程进行会出一些问题，显示如下报错

   ```
   ERROR Failed to reload config: failed to load config: "D:\xxx\mysite\hugo.toml:1:1": unmarshal failed: toml: table markup already exists
   ```

   这是因为在 loveit 官网复制的两段代码有些项重复，解决方法如下：

   ```
   【# Hugo 解析文档的配置
   【markup】
     # 语法高亮设置 (https://gohugo.io/content-management/syntax-highlighting)
     【markup.highlight】
       # false是必要的设置 (https://github.com/dillonzq/LoveIt/issues/158)
       noClasses = false】
   改成第二次copy的【# Hugo 解析文档的配置：
   【markup】
     # 语法高亮设置
     【markup.highlight】
       codeFences = true
       guessSyntax = true
       lineNos = true
       lineNumbersInTable = true
       # false 是必要的设置
       # (https://github.com/dillonzq/LoveIt/issues/158)
       noClasses = false】
   再把第二次copy中刚刚替换的【】内容删掉
   再删去第二次copy的# 作者配置和# 菜单配置下面的内容
   最后将删好的第二次copy内容贴上去
   ```

   因为过程比较繁琐，所以直接复制上面六百多行的代码即可。

   在终端利用 cd 来进入子目录，举例

   ![70987443764](/images/1709874437644.png)

   进入博客文件夹，然后输入

   ```
   hugo new posts/first_post.md
   ```

   然后我们就可以在 content 文件夹发现建立了一个"post"文件夹，里面是一个 md 后缀的 markdown 文件，这是你博客的第一篇文章，进入后，将第三行的 true 改为 false。

   在终端输入

   ```
   hugo serve
   ```

   然后在浏览器网页栏输入：<http://localhost:1313>

   然后你会看到类似于这个的一个简单网页

   ![70987450977](/images/1709874509778.png)

   恭喜你，网页的简单框架就搭建好了~

3. vs code 的下载、汉化与配置以及 markdown 语句的简单学习

   进入 vs 官网：<https://code.visualstudio.com/>，下载对应 windows 的 vs code

   下载成功之后进入软件，点击右侧从上往下数第五个图标，

   搜索"chinese"，安装后重启即可完成汉化。

   此外我额外安装了以下插件

   ![70987846255](/images/1709878462555.png)

   markdown 的学习是创建个人博客的必经之路，好在它简单轻便并不复杂，所以容易上手。

   在<https://hugoloveit.com/zh-cn/basic-markdown-syntax/>中可以学习其基本用法，略微了解之后即可尝试在自己的博客上发布文章。

4. 使用 vs code 建立博客

   点击左上角的文件，打开之前的博客文件夹。

   如果你没有按之前的步骤进行汉化的话，你需要点击的就是点击左上角-File-Open Folder，

   ![](/images/Snipaste_2024-03-09_23-43-51.png)[^2]

   [^2]: doki 是我新建的博客文件夹

   点击右下角的"选择文件夹"。不出意外的话，你应该会看到类似下图的样子！

   ![](/images/vx_20240309235217.png)

   接下来我们点进 hugo.toml，我们可以通过检索注释，适当删改里面的部分内容，让网页显示为我们希望它显示的那样，举个例子：

   ![70988401168](/images/1709884152161.png)

   这里我通过观看注释，修改了主页的头像、网站的标题以及副标题，具体效果如下：

   ![70988418030](/images/1709884180301.png)

   像这样的简单的修改不过多赘述，诸位自行在 loveit 官网查阅了解，很快就能熟悉操作~

   如果大家希望把自己的图片转换为网络连接，推荐使用<https://postimages.org/>

5. 发布文章并用 markdown 语句丰富文章内容

   一个合格的博客必然要有文章，用 vs code 打开咱们的博客文件夹，ctrl+“~”打开终端，不出意外的话你那边显示的和我应该差不多（doki 是我新建的博客的名字）：

   ![70988533272](/images/1709885332727.png)

   在这里输入

   ```
   hugo new posts/(这个是你第一个文章的文件夹的名字，最好是中文).md
   ```

   注意：.md 是 markdown 文件的后缀，也可以使用.org，这里我选择使用.md。

   然后你会发现 content 文件夹下创建了一个 posts 文件夹，在这个文件夹下出现了咱们刚刚创建的 markdown 文件，，在 vs code 中点进文件，会发现有一行

   ```
   draft: true
   ```

   意思是这个文章是草稿，不会在网页中显示，删除它并输入

   ```
   draft: false
   ```

   然后就可以在我们的博客网站看到一篇新的文章！

   下面是 loveit 官网提供的前置配置代码，复制粘贴覆盖先前.md 文件中的内容即可

   ```
   ---
   title: "我的第一篇文章"
   subtitle: ""
   date: 2020-03-04T15:58:26+08:00
   lastmod: 2020-03-04T15:58:26+08:00
   draft: false
   author: ""
   authorLink: ""
   description: ""
   license: ""
   images: []

   tags: []
   categories: []

   featuredImage: ""
   featuredImagePreview: ""

   hiddenFromHomePage: false
   hiddenFromSearch: false
   twemoji: false
   lightgallery: true
   ruby: true
   fraction: true
   fontawesome: true
   linkToMarkdown: true
   rssFullText: false

   toc:
     enable: true
     auto: true
   code:
     copy: true
     maxShownLines: 50
   math:
     enable: false
     # ...
   mapbox:
     # ...
   share:
     enable: true
     # ...
   comment:
     enable: true
     # ...
   library:
     css:
       # someCSS = "some.css"
       # 位于 "assets/"
       # 或者
       # someCSS = "https://cdn.example.com/some.css"
     js:
       # someJS = "some.js"
       # 位于 "assets/"
       # 或者
       # someJS = "https://cdn.example.com/some.js"
   seo:
     images: []
     # ...
   ---
   ```

   在“---”下面是输入内容的区域，先前学习的 markdown 语法就可以在这里派上用场~

   接下来是自由发挥时间，大家可以在 loveit 官网上自行学习摸索。

   以下是我的简单示范：

   ![70988742522](/images/1709887425222.png)

   效果如下：

   ![70988745684](/images/1709887456848.png)

   好了！到现在位置，最基本的博客搭建和文章发布你都已经学会了~接下来你就可以在自己的博客里面发挥自己的创造力，让自己的博客变得更加有生命力了！

6. 把网站部署到 github 服务器上

   我们需要拥有一个 github 的账号和 GitHub desktop 软件。

   浏览器输入：<www.github.com>进入github官网，在官网注册账号。

   注意，如果你是学生，可以申请学校邮箱，注册 github，认证学生身份，部分学校会为学生购买 github 的增值服务，好处多多。

   如果你无法点进这个网址，在微软商店下载 watt toolkit，其内有 github 的免费加速服务，不做过多赘述，此处不懂可以自行上网搜索 github 加速方法。

   github 桌面版官网：<https://desktop.github.com/>，下载好软件选择 github 登录即可。

   紧接着在博客文件夹的终端下输入 hugo，可以发现文件夹内多了 public 文件夹，这个文件夹存储了我们静态网页的信息。

   接着在终端输入

   ```
   cd public
   ```

   进入 public 文件夹，然后依次输入

   ```
   git init
   git add .(add后有空格)
   git commit -m"MyFirstCommit"(引号内容随意输入)
   ```

   这样就完成了把 public 文件夹交给 git 接管。

   进入 github desktop，点击鼠标所指的地方

   ![70990061421](/images/1709900614214.png)

   添加一个已经存在的仓库，选择路径，也就是刚刚 public 文件夹的位置。

   ![70990068505](/images/1709900685053.png)

   大致如上图所示，路径以 public 结尾，添加仓库即可。

   然后点击下图鼠标所指的位置，

   ![70990074453](/images/1709900744535.png)

   会跳出一个弹窗：

   name：（这里要输入你 github 的 id.github.io，比如我 github 的 id 是 chank，我就输入 chank.github.io）

   description:（随意填写）

   **接下来的框框不要勾选。**

   然后点击 publish repository 即可。

   进入www.github.com，点击右上角头像，点击第四行Your Repositories，

   你会看到类似这样的仓库：

   ![70990107291](/images/1709901072914.png)

   进入，点击右侧的 setting，找到 pages；

   ![70990113591](/images/1709901135914.png)

   将 branch 下的 none 改为 master 并 save，如果本来就是 master 不用理会。

   ![70990119039](/images/1709901190393.png)

   接着你就可以在浏览器输入

   ```
   你的github id.github.io
   ```

   来访问你的博客网站了！

   比如我的博客网站是：<https://yichan521.github.io/>。

7. 博客的更新和修改

   我们在本地 vs code 上修改的配置文件如果不重新上传是不会在网站上同步的，重新上传的步骤与之前的步骤大同小异。

   同样是在博客文件夹的终端下输入 humo，再建一个 public 文件夹，重复上述步骤，直到 git commit -m"anything"结束。

   接着打开 github desktop 就会发现它给了你一个提示，同意即可，大约五分钟过后，我们在本地的修改就会被同步到网站上。

   至此，hugo 搭建个人博客以及网站部署的全部工作都已经完成！如果想进行网页美化等工作，可以进一步学习前端三件套（HTML/CSS/JaveScript），如果想了解更多基础功能，请移步 loveit 官网进行更细致的了解。

   相信看到这里的朋友已经对 hugo 有了基础的了解，大家也可以去尝试别的主题，不拘泥于 loveit，进行更多的尝试，诚祝大家的博客搭建之路一路畅通！

