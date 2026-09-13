# 我的个人 CV 网站

仿照 [abzhaobo.github.io](https://abzhaobo.github.io/)(al-folio 学术主题风格)制作的**纯静态**个人主页。
不需要安装任何环境、不需要编译,改完内容发布到 GitHub Pages 即可上线。

```
cv-website/
├── index.html          ← 首页(简介 / 教育经历 / CV 链接)
├── cv/
│   └── index.html      ← 简历页(完整 CV)
└── assets/
    ├── css/main.css    ← 样式(主题色在这里改)
    ├── img/avatar.svg  ← 头像(换成你的照片)
    └── pdf/            ← 把你的 CV.pdf 放进来
```

---

## 上线步骤(依次做)

### 第 0 步:本地预览(可选)
直接**双击 `index.html`** 用浏览器打开,就能看到网站效果。

### 第 1 步:填写你的个人信息
所有需要修改的地方都写了 `<!-- ★ 数字. 说明 -->` 注释,用编辑器(VS Code / 记事本)打开文件,搜索 `★` 逐个替换:

- **`index.html`**:标签页标题、导航栏名字、页面大标题、头像下方联系方式、英文简介、教育经历、中文简介、页脚版权名
- **`cv/index.html`**:联系方式、研究兴趣、教育经历、论文、经历、奖项等各栏
- 把所有 `【……】` 占位内容替换成你的真实信息

### 第 2 步:换成你的头像
1. 准备一张照片(正方形或 3:4 竖版效果最好),重命名为 `avatar.jpg`
2. 放进 `assets/img/` 文件夹(可以把 `avatar.svg` 删掉)
3. 打开 `index.html`,把 `src="assets/img/avatar.svg"` 改成 `src="assets/img/avatar.jpg"`

### 第 3 步:放入简历 PDF
把简历导出为 PDF,命名为 `CV.pdf`,放进 `assets/pdf/` 文件夹。
首页的 "CV" 链接和 CV 页的下载按钮会自动生效。

### 第 4 步:注册 GitHub 并创建仓库
1. 打开 [github.com](https://github.com) 注册账号(已有可跳过),**记住你的用户名**(下面以 `zhangsan` 为例)
2. 登录后点右上角 **+** → **New repository**
3. Repository name 必须填:**`zhangsan.github.io`**(格式固定 = 你的用户名 `.github.io`)
4. 可见性选 **Public**;下面的 "Add a README" 等初始化选项**都不要勾**
5. 点 **Create repository**

### 第 5 步:上传网站文件(二选一)

**方式 A:网页拖拽上传(最简单,推荐新手)**
1. 在刚创建的仓库页面,点击 **"uploading an existing file"** 链接
2. 打开本地 `cv-website` 文件夹,**把里面的所有内容**(`index.html`、`cv` 文件夹、`assets` 文件夹、`README.md`)拖到网页上传区
   ⚠️ 注意是文件夹"里面"的内容,不要把 `cv-website` 这一层文件夹本身拖进去,否则网址会多一层目录
3. 等上传完成,点底部绿色按钮 **Commit changes**

**方式 B:Git 命令行(需已安装 Git)**
```bash
cd cv-website
git init
git add .
git commit -m "init: my personal website"
git branch -M main
git remote add origin https://github.com/zhangsan/zhangsan.github.io.git
git push -u origin main
```

### 第 6 步:访问你的网站
等待 1~2 分钟,浏览器打开:

> **https://zhangsan.github.io** (换成你的用户名)

如果显示 404:进入仓库 **Settings → Pages**,确认 Source 为 **Deploy from a branch**、Branch 为 **main / (root)**,点 Save,再等一两分钟刷新。

### 以后怎么更新内容
- 方式 A:进 GitHub 仓库页面,点开对应文件 → 铅笔图标 ✏️ 直接在线编辑 → Commit;或再拖拽上传同名文件覆盖
- 方式 B:本地改完后 `git add . && git commit -m "update" && git push`
- 保存后 1~2 分钟自动生效(如果没变化,强刷 `Ctrl + F5`)

---

## 可选的个性化

| 想做什么 | 怎么做 |
|---|---|
| 换主题颜色 | `assets/css/main.css` 顶部的 `--global-theme-color`(默认 `#b509ac`,可改 `#006bb8` 蓝色、`#b71c1c` 红色等) |
| 增加导航页面 | 复制 `cv/` 文件夹改内容,并在两个页面的导航 `<ul>` 里各加一行 `<li><a href="xxx/">页面名</a></li>` |
| 字体加载慢 | 字体来自 Google Fonts,若访问慢可删除 `<head>` 里的两条 `fonts.googleapis.com` 链接,改为系统字体 |
| 更强的功能(博客、暗色模式、论文自动列表) | 直接使用原版 Jekyll 模板:[github.com/alshedivat/al-folio](https://github.com/alshedivat/al-folio),fork 后按其文档部署 |
| 绑定自己的域名 | 仓库 Settings → Pages → Custom domain |
