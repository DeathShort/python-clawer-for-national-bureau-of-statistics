# python-clawer-for-national-bureau-of-statistics
抓取国家统计局的国家数据的小爬虫
之前虽然对爬虫也仅仅停留在最基础的地方，但是既然有这个机会，为什么不借着这个机会学习一下呢？于是就答应了下来，开始了一周的爬坑之旅。

需要爬取的数据是国家统计局里的国家数据，主要爬取固定资产与房地产两个父指标下，所有子指标里所有省市自2013年以后的数据。（http://data.stats.gov.cn/easyquery.htm?cn=E0101）
![image.png](http://upload-images.jianshu.io/upload_images/4982520-182f0a72609029ad.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
使用浏览器自带的开发者工具，观察一下需要爬取的页面，发现需要采集的数据是使用js生成的，这样是无法通过requests直接获取数据的。在这里我没有去解析请求获取数据的js代码块，而是采取了通过selenium模拟操作chrome浏览器，获得渲染后的页面，再使用beautifulsoup对源码进行解析，抓取需要的数据。
