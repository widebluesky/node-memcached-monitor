# node-memcached-monitor
nodejs版本实现memcached服务监控、keys管理

使用nodejs+vuejs+element-ui+webpack进行开发 作为学习项目，欢迎有需要的朋友一起进行探讨！

>本项目使用了es2015部分语法，请使用最新的运行环境，譬如不错的chrome

实现功能：
1. 服务器基础数据：系统分配内存、存储占用内存、其他实时数据
2. 连接数：实时客户端连接数
3. 命令数：实时每秒处理命令数、key值命中率
4. 流量：实时每秒服务器发送流量
5. key：实现key搜索、查看、删除功能、占用大小、过期时间
6. 集群：支持集群模式


[github](https://github.com/aofong/node-memcached-monitor, "github") [码云](https://gitee.com/aofong/node-memcached-monitor, "oschina 码云")

# 运行示例

```
//获取代码
git clone https://gitee.com/aofong/node-memcached-monitor.git

//进入代码目录
cd node-memcached-monitor

//安装依赖
npm i 或者 npm install

//运行nodejs后台服务
node server/index   或者vscode直接按F5运行

//运行web页面
//开发环境
npm run dev

//生产环境
npm run build

//浏览
http://localhost:8010

```

# 默认配置
默认采用mockjs数据模拟相关数据

您可要在配置页进行实例数据配置，配置完后记得重做服务！

## 默认存储
内置使用mssql存储缓存key值，表结构如下：

表名：caches

字段：name 建唯一索引，并忽略重复，建议配置定时任务来清理数据（每日清空一次）

|id|name|size|ttl|platform| 
|-|-|-|-|-| 
|1|cachekey|123|123456789|memcached| 

## 默认参数：

nodejs服务运行端口：3000 

web界面运行端口：8010

缓存同步时间：15分钟 


## 文件目录
server 存储nodejs服务代码

src 存储vuejs源文件

disk 生成环境代码

config.js 运行配置

server/sync/mssqlhelper.js  内置mssql连接问题，可在此修改数据库连接

server/api.js 接口服务，可在此移除mockjs数据 或者实现其他的存储

# 技术文档
[nodejs](https://nodejs.org) [vuejs](https://cn.vuejs.org/) [element-ui](http://element-cn.eleme.io/#/zh-CN) [webpack-cn](https://doc.webpack-china.org/concepts/)


# 运行预览截图

![服务监控](https://gitee.com/uploads/images/2017/1108/172122_8012b273_341398.png "服务监控")

![key管理](https://gitee.com/uploads/images/2017/1118/154942_1911cb8c_341398.png "key管理")

![查看key](https://gitee.com/uploads/images/2017/1118/155153_b93d1fd1_341398.png "查看key")

![删除key](https://gitee.com/uploads/images/2017/1118/155126_cd142cb3_341398.png "删除key")

![配置](https://gitee.com/uploads/images/2017/1118/155332_0dcffbc1_341398.png "配置")