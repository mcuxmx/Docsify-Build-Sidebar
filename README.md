# 🐵 DocsifyBuildSidebar For C#

自动生成 docsify 的 sidebar  和 每个子目录中的 sidebar

[Docsify 官网](https://docsify.js.org/#/zh-cn/)


## 其他语言
用 go 复刻的源码👉 [xxxxue/GoBuildDocsifySidebar](https://github.com/xxxxue/GoBuildDocsifySidebar)

~~Releases 中文件支持 3大主流平台, golang 可执行文件较小,方便下载.~~ 

( 仅供学习, go 太难用,再也不想写 go 了 )


# 网站的部署
- ⭐ Vercel (免费全自动部署): 直接关联github私有/公有仓库,nodejs那几个命令不用填, 直接部署即可,3秒即可成功.每次提交代码,Vercel都会自动部署.
- ⭐ Netlify : 同 Vercel, 可作为 Vercel 的替代.
- Github Page: 国内访问太慢了.
- ☠ Gitee Pages (码云) : 比较辣鸡,白嫖党需要每次手动点击更新. 而且还有违禁违规内容审查, 有些正常的内容都被误报. 还要实名认证,需要上传手持身份证的照片

---
还没使用过的平台
- GitCode : CSDN 旗下的代码托管平台 https://gitcode.net/
- Coding Pages : 腾讯旗下的一个代码托管平台 https://coding.net/

#  使用方法:
>
> 1. 在 github 页面右侧的 "Releases" 中下载编译好的软件
> 2. 修改 Config 中的 `HomePath` 为 `自己电脑上的目标根目录`
> 3. 双击 exe 执行

# 小技巧:

## 快捷方式
可以右键单击 exe ,创建一个 快捷方式, 

把这个`快捷方式`剪切到自己的项目根目录,

以后就不用每次都去找 exe 了

![image](https://github.com/xxxxue/Docsify-Build-Sidebar/assets/32764266/db131d3a-1caa-4ce9-a86f-a4622912d129)

## 快速运行 docsify
docsify 目录中新建一个 `运行docsify.bat` 文件, 代码如下
```bash
@echo off
docsify serve ./
```
以后双击这个文件,就可以本地运行 docsify 了


# Config.json 配置项

| 名称                      | 说明                                        | 例子                                    |
| ------------------------- | ------------------------------------------- | --------------------------------------- |
| HomePath                  | Docsify 项目的根目录                        | `E:\\Work\\coding\\xxxue`               |
| IgnoreFile                | 忽略的文件 (判断规则: 相等)                 | `Readme.md`                             |
| IgnoreDir                 | 忽略的目录 (判断规则: 相等)                 | `.git`                                  |
| IgnoreDirNameContain      | 忽略的目录 (判断规则: 目录名称任意位置包含) | `.assets` 匹配 `*.assets*`              |
| DisableGenerateReadmeFile | 禁用 "生成 Readme.md 文件"  (默认生成)      | `true` (不生成) / `false`(生成)(默认值) |



# 首页效果

```markdown
- [C_Sharp](C_Sharp/)
  - [TestPaper](C_Sharp/TestPaper/)
    - [1](C_Sharp/TestPaper/1.md)
    - [2](C_Sharp/TestPaper/2.md)
  - [Docker](C_Sharp/Docker.md)
  - [EFCore](C_Sharp/EFCore.md)
  - [Furion](C_Sharp/Furion.md)
  - [RX](C_Sharp/RX.md)
  - [SpectreConsole](C_Sharp/SpectreConsole.md)
  - [Utils](C_Sharp/Utils.md)
- [Java](Java/)
  - [Github](Java/Github.md)
- [JavaScript](JavaScript/)
  - [AutoJs](JavaScript/AutoJs/)
    - [code](JavaScript/AutoJs/code.md)
    - [test1](JavaScript/AutoJs/test1/)
      - [te](JavaScript/AutoJs/test1/te.md)
      - [test2](JavaScript/AutoJs/test1/test2/)
        - [aaa](JavaScript/AutoJs/test1/test2/aaa.md)
  - [Docsify](JavaScript/Docsify.md)
  - [Github](JavaScript/Github.md)
- [Ubuntu](Ubuntu/)
  - [Commands](Ubuntu/Commands.md)
```

# 1级子目录

```markdown
- [返回首页](/)
- [C_Sharp](C_Sharp/)
  - [TestPaper](C_Sharp/TestPaper/)
    - [1](C_Sharp/TestPaper/1.md)
    - [2](C_Sharp/TestPaper/2.md)
  - [Docker](C_Sharp/Docker.md)
  - [EFCore](C_Sharp/EFCore.md)
  - [Furion](C_Sharp/Furion.md)
  - [RX](C_Sharp/RX.md)
  - [SpectreConsole](C_Sharp/SpectreConsole.md)
  - [Utils](C_Sharp/Utils.md)
```

## n级子目录

```markdown
- [返回上一级 [C_Sharp]](C_Sharp/)
- [TestPaper](C_Sharp/TestPaper/)
  - [1](C_Sharp/TestPaper/1.md)
  - [2](C_Sharp/TestPaper/2.md)
```

# 界面效果

![image-20220501150050290](img.assets/image-20220501150050290.png)

# docsify index.html 模版

```html
<!-- index.html -->

<!DOCTYPE html>
<html>
  <head>
    <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1" />
    <meta name="viewport" content="width=device-width,initial-scale=1" />
    <meta charset="UTF-8" />
    <link rel="stylesheet" href="//cdn.jsdelivr.net/npm/docsify@4/themes/vue.css" />

    <!-- 文件夹样式 -->
    <link rel="stylesheet" href="//cdn.jsdelivr.net/npm/docsify-sidebar-collapse/dist/sidebar-folder.min.css" />
    <!-- 箭头样式 -->
    <!-- <link rel="stylesheet" href="//cdn.jsdelivr.net/npm/docsify-sidebar-collapse/dist/sidebar.min.css" /> -->
  </head>
  <body>
    <div id="app"></div>
    <script>  
      window.$docsify = {
        name: "Blog",
        // 侧边栏文档目录
        loadSidebar: true,

        subMaxLevel: 2,
        alias: {
          "/.*/_sidebar.md": "/_sidebar.md",
        },
        // 跳转后自动到顶部
        auto2top: true,

        coverpage: true,
        // PLUGINS
        // ----------------------------------------------------------------
        // 页面右侧toc
        toc: {
          tocMaxLevel: 2,
          target: "h2, h3, h4, h5, h6",
        },

        // 全文搜索
        search: {
          depth: 6,
          noData: "没有搜到!",
          placeholder: "搜索...",
          // 避免搜索索引冲突,同一域下的多个网站之间
          namespace: "website-1",
        },
        // 底部导航
        pagination: {
          previousText: "上一页",
          nextText: "下一页",
          crossChapter: true,
          crossChapterText: true,
        },
        // 字数统计
        count: {
          countable: true,
          position: "top",
          margin: "10px",
          float: "right",
          fontsize: "0.9em",
          color: "red",
          language: "chinese",
          localization: {
            words: "",
            minute: "",
          },
          isExpected: true,
        },
      };
    </script>
    <!-- docsify -->
    <script src="https://cdn.jsdelivr.net/npm/docsify@4/lib/docsify.min.js"></script>  

    <!-- 代码高亮  https://cdn.jsdelivr.net/npm/prismjs@1/components/ -->
	
    <script src="//cdn.jsdelivr.net/npm/prismjs@1/components/prism-bash.min.js"></script>	
    <script src="//cdn.jsdelivr.net/npm/prismjs@1/components/prism-python.min.js"></script>
    <script src="//cdn.jsdelivr.net/npm/prismjs@1/components/prism-cmake.min.js"></script>
    <script src="//cdn.jsdelivr.net/npm/prismjs@1/components/prism-java.min.js"></script>
    <script src="//cdn.jsdelivr.net/npm/prismjs@1/components/prism-csharp.min.js"></script>     
    <script src="//cdn.jsdelivr.net/npm/prismjs@1/components/prism-docker.min.js"></script>  
	<script src="//cdn.jsdelivr.net/npm/prismjs@1/components/prism-powershell.min.js"></script>  


    <!-- 多tab支持 -->
    <script src="https://cdn.jsdelivr.net/npm/docsify-tabs@1/dist/docsify-tabs.min.js"></script>

    <!-- 代码复制 -->
    <script src="https://cdn.jsdelivr.net/npm/docsify-copy-code@2/dist/docsify-copy-code.min.js"></script>

    <!-- 底部 上一页下一页 -->
    <script src="https://cdn.jsdelivr.net/npm/docsify-pagination@2/dist/docsify-pagination.min.js"></script>

    <script src="https://cdn.jsdelivr.net/npm/docsify@4/lib/plugins/external-script.min.js"></script>

    <script src="https://cdn.jsdelivr.net/npm/docsify@4/lib/plugins/ga.min.js"></script>

    <!-- 全文搜索 -->
    <script src="https://cdn.jsdelivr.net/npm/docsify@4/lib/plugins/search.js"></script>

    <!-- 图片放大缩小 -->
    <script src="https://cdn.jsdelivr.net/npm/docsify@4/lib/plugins/zoom-image.min.js"></script>

    <!-- 字数统计 -->
    <script src="https://cdn.jsdelivr.net/npm/docsify-count@latest/dist/countable.min.js"></script>

    <!-- 侧边栏目录折叠 -->
    <script src="https://cdn.jsdelivr.net/npm/docsify-sidebar-collapse/dist/docsify-sidebar-collapse.min.js"></script>

    <!-- 页面右侧 TOC -->
    <script src="https://cdn.jsdelivr.net/npm/docsify-plugin-toc@1.1.0/dist/docsify-plugin-toc.min.js"></script>

      <!-- emoji -->
      <script src="//cdn.jsdelivr.net/npm/docsify/lib/plugins/emoji.min.js"></script>
  </body>
</html>

```

# 联系方式

> QQ: 1659809758

# 支持作者

![pay](img.assets/pay.png)

