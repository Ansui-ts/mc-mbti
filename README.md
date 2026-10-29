# 测测你是哪只 MC 生物

一个 16 型人格测试：20 道关于日常的小题，测出你是哪一只 Minecraft 生物。
生物形象全部用游戏官方模型与官方贴图，在浏览器里实时渲染（WebGL），走路动作也是按原版步态做的。

纯静态页面，没有后端、没有数据库、没有外部请求，贴图全部内嵌。

页面底部常驻一行声明「仅供娱乐，如有侵权即刻下架，感谢支持」；结果页与图鉴页末尾附有赞赏码（已 base64 内嵌，不依赖外部图片）。

## 文件说明

| 文件 | 作用 |
|---|---|
| `index.html` | 整个测试（单文件，含模型、贴图、题库、文案） |
| `og.png` | 微信 / QQ 转发时显示的分享卡片（1200×630） |
| `icon-180.png` | iOS 添加到主屏时的图标 |
| `icon-512.png` | 高清图标（部分平台抓取用） |
| `.nojekyll` | 告诉 GitHub Pages 不要跑 Jekyll，发布更快 |

## 图鉴与答题记录

- 图鉴里的 16 种生物**都会显示形象**：答出来的显示原色，没答到的做灰度处理，不再用问号占位。
- 每答完一次会往本地记一条，页底「我的记录」列出最近 12 次结果（生物名 + 四维编码 + 时间）。
- 下次再打开这个页面，封面会显示「上次测出 X · 几天前」。
- 记录只存在你自己的浏览器里（localStorage），不上传服务器；换设备、换浏览器、清缓存都会丢，属于静态页面的固有限制。

## 部署到 GitHub Pages

1. 登录 GitHub，右上角 `+` → **New repository**
2. Repository name 填 `mc-mbti`，选 **Public**，不要勾选任何初始化文件 → **Create repository**
3. 进入仓库，点 **uploading an existing file**（或 `Add file → Upload files`）
4. 把本目录下的**所有文件**拖进去（`index.html` 必须在根目录，不能套一层文件夹）→ **Commit changes**
5. 仓库顶部 **Settings** → 左侧 **Pages**
6. Source 选 **Deploy from a branch**；Branch 选 **main**、目录选 **/ (root)** → **Save**
7. 等 30~90 秒，刷新页面，顶部会出现网址：
   **https://ansui-ts.github.io/mc-mbti/**

## 关于网址

`index.html` 开头的分享地址已经按 `Ansui-ts` + 仓库名 `mc-mbti` 填好了：

```html
<link rel="canonical" href="https://ansui-ts.github.io/mc-mbti/">
<meta property="og:image" content="https://ansui-ts.github.io/mc-mbti/og.png">
<meta property="og:url" content="https://ansui-ts.github.io/mc-mbti/">
<meta name="twitter:image" content="https://ansui-ts.github.io/mc-mbti/og.png">
```

所以**仓库名必须叫 `mc-mbti`**。如果换了别的名字，把这 4 行里的 `mc-mbti` 一起改掉即可（不改也能做题，只是分享出去抓不到缩略图）。

## 更新内容

改完文件后，仓库页 `Add file → Upload files` 拖进去覆盖，Commit，等 1 分钟。
浏览器会缓存，自己看要 `Ctrl + F5`（Mac 是 `Cmd + Shift + R`）强制刷新。

## 常见问题

**打开是 404**
Pages 还没构建完，等 1~2 分钟；或者仓库是 Private（免费版 Pages 只对 Public 仓库开放）。

**别人点开很慢**
`github.io` 在国内部分网络下不稳定。可以给仓库绑一个自己的域名（Settings → Pages → Custom domain），域名服务商加一条 CNAME 指向 `ansui-ts.github.io`，HTTPS 证书 GitHub 会自动签发。

**图鉴里的记录没了 / 换了设备看不到**
答题记录和解锁进度都存在浏览器的 localStorage 里，按域名隔离，不会上传到任何服务器。换设备、换浏览器、清缓存、无痕模式都会清零，属于静态页面的固有限制。

**分享链接直达某个结果**
结果页的编码可以直接当链接用，例如 `https://ansui-ts.github.io/mc-mbti/#r=hszd` 会直接打开「苦力怕」的结果页。测试里的「分享给朋友」按钮会自动带上当前域名。

**老设备不支持 WebGL**
页面会自动降级成预渲染好的静态图，不会白屏。
