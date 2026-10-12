# 行为积分记账本

孩子每天行为完成情况的奖惩记账本。月历显示每日得分，点击某天查看并加减分，顶部自动汇总本月总分。
单个 HTML 文件 + 一个可选的离线缓存脚本，无后端、无依赖、无需联网。

## 文件说明

| 文件 | 是否必须 | 作用 |
|---|---|---|
| `index.html` | 必须 | 全部功能，界面 + 逻辑 + 样式都在里面 |
| `sw.js` | 可选 | 让页面断网也能打开（PWA 离线缓存）。不要可以不传，删掉不影响任何功能 |
| `.nojekyll` | 可选 | 让 GitHub 跳过 Jekyll 处理，避免个别资源被过滤 |
| `README.md` | 可选 | 就是这个文件 |

数据保存在浏览器的 localStorage 里，**每台设备各自独立**，不会自动同步。

## 部署方法 A：网页上传（不用装 git）

1. 打开 https://github.com/new ，仓库名填 `你的用户名.github.io`
   （比如用户名是 `zhangsan`，就填 `zhangsan.github.io`），选 **Public**，勾上 Add a README，点 Create repository
2. 进入仓库 → 点 **Add file** → **Upload files**，把 `index.html`（和 `sw.js`、`.nojekyll`）拖进去 → 点 **Commit changes**
3. 进 **Settings** → 左侧 **Pages** → Build and deployment 里 Source 选 **Deploy from a branch**，
   Branch 选 `main`、目录选 `/ (root)` → Save
4. 等 1～2 分钟，访问 `https://你的用户名.github.io`

如果你不想占用个人主页仓库，也可以建一个普通仓库（比如叫 `jifen`），Pages 设置一样，
地址会变成 `https://你的用户名.github.io/jifen/` —— 照样能用，本页所有路径都是相对的，不需要改代码。

## 部署方法 B：命令行 git

```bash
# 在本目录执行，把 <USER> 换成你的 GitHub 用户名
git init
git add index.html sw.js .nojekyll README.md
git commit -m "行为积分记账本"
git branch -M main
git remote add origin https://github.com/<USER>/<USER>.github.io.git
git push -u origin main
```

然后按方法 A 的第 3 步打开 Pages 即可。

## 手机上当 App 用

- iPhone：Safari 打开 → 分享按钮 → 「添加到主屏幕」
- 安卓：Chrome 打开 → 右上角菜单 → 「添加到主屏幕 / 安装应用」

之后从桌面图标进入是全屏的，看不到浏览器地址栏。

## 注意

- GitHub Pages 的免费仓库都是公开的，知道网址的人都能打开这个页面。
  在意的话，进「管理 → 访问口令」设一个口令。
- 数据只在当前浏览器里，**清理浏览器数据 / 换设备会丢失**。
  请偶尔在「管理 → 备份与迁移」导出一次 JSON 存好。
- 更新版本：只需要替换仓库里的 `index.html`，等一两分钟刷新即可。
  如果开了 sw.js 还是看到旧页面，多刷新一次或清一下缓存。
