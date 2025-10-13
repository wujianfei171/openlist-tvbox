# OpenList-TVBox

> 一个基于 **OpenList API** 的 **TVBox** 兼容爬虫脚本（Spider），用于在 **TVBox** 中直接浏览、搜索和播放 **OpenList** 上的多媒体资源，无需依赖外部 JAR。


## **功能特性**

* ✅ 支持 ****OpenList** 接口规范****
* ✅ 支持 **多驱动配置**（可同时接入多个 OpenList 源）
* ✅ 支持使用账户密码登录
* ✅ 支持目录树浏览、分页与文件类型识别
* ✅ 支持视频、图片、字幕等文件识别与直链播放
* ✅ 支持关键词搜索（模糊匹配），需要在 **Openlist** 上提前建立索引
* ✅ 兼容 TVBox **type=3** Spider 接口结构

## 快速开始

1. **tvbox.json** 和 **openlist.json** 放到你的 guest 用户能访问 openlist 目录中，guest 不设密码，如果有 nginx，可以直接托管 nginx。
2. 修改 openlist.json，填写上你的 openlist 服务器信息，并删除注释信息:
    ```
    [
      {
        "name": "openlist",
        "server": "http://10.1.1.12:5244/",
        "startPage": "/",
        "realStartPage": "/tvbox",
        "search": true,
        "username": "tvbox",
        "password": "mypass"
      }
      ,
      ...
    ]

    ```
3. 修改 tvbox.json，并删除注释信息:
    ```
    {
      "sites": [
        {
          "key": "Openlist",
          "name": "OpenList｜合集",
          "type": 3,
          "api": "https://ghfast.top/https://raw.githubusercontent.com/lisaac/openlist-tvbox/refs/heads/main/openlist_spider.js",
          "searchable": 1,
          "filterable": 0,
          "changeable": 0,
          "style": {
            "type": "list"
          },
          // 将这里的 "./openlist.json" 改为 openlist 的直链地址，可以在openlist页面打开openlist.json后复制，通常是：
          // "http://xxxx:5244/d/tvbox/sub/openlist.json?sign=xxxxxxxxxxxxxxxxxxxxxxxxxxxx=:0"
          "ext": "./openlist.json"
        }
      ]
    }
    ```

## 感谢

基于hjdhnx [https://github.com/hjdhnx/dr_py](https://github.com/hjdhnx/dr_py) 修改
