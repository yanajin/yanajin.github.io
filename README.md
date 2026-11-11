# 靳雅娜个人学术网站

这是为 `https://yanajin.github.io/` 准备的静态网站。首页为英文，中文仅用于姓名和一段简介。没有构建步骤、后端、数据库或第三方字体依赖。

当前交付为本地预览，尚未上传 GitHub 或正式发布。

## 本地查看

直接双击本目录的 `index.html`，即可在浏览器中查看完整页面。图片、样式和学生名单展开功能均可离线使用；论文和 Google Scholar 链接需要联网。邮箱以 dot/at 普通文字展示，不设置 `mailto` 链接，结构化数据中也不保留明文邮箱。

也可以通过本地 HTTP 服务查看。在本目录打开终端，运行：

```powershell
python -m http.server 8765 --bind 127.0.0.1
```

然后访问 `http://127.0.0.1:8765/`。如系统未安装 Python，直接双击首页即可。

## 文件与内容维护

| 文件 | 用途 |
| --- | --- |
| `index.html` | 简介、13 篇发表论文、4 篇 working papers、课程、学生与搜索元数据 |
| `styles.css` | 配色、文字大小、留白、手机布局与打印样式 |
| `assets/yana-jin.webp`、`assets/yana-jin.jpg` | 优化后的照片，JPG 为兼容备用格式 |
| `assets/social-preview.jpg` | 分享网站链接时的预览图片 |
| `assets/favicon.svg`、`assets/favicon.ico`、`assets/apple-touch-icon.png` | 浏览器和手机图标 |
| `sitemap.xml`、`robots.txt` | 搜索引擎发现页面所需的配置 |
| `.nojekyll` | 让 GitHub Pages 直接发布静态文件，无需 Jekyll |

使用支持 UTF-8 的文本编辑器修改 HTML，保存后刷新浏览器即可。所有正文直接写在 HTML 中，不需要重新生成页面。

### 视觉样式约定

- 页面保持白底，主色为 `#275f50`，正文深灰 `#303735`，辅助文字灰色 `#606D66`。链接、章节标题和导航交互采用主色，状态与引用标签采用浅灰底。
- 全站统一使用 `"Segoe UI", Arial, "Microsoft YaHei", sans-serif`，字重采用 400、600、700。姓名为桌面端 44px、手机端 36px；章节标题 26px / 24px；论文标题和正文 16px；作者、期刊和学生名单 14px；辅助文字和导航 13px；教学及学生分组标题 18px。
- 桌面端首屏左侧照片宽 216px、与简介间距 48px；平板端照片宽 180px、间距 32px；手机端照片在简介上方。照片保持原始比例。
- 顶部姓名为 `Yana Jin`，末尾不加装饰句点。YJ 图标使用深灰底、白字；分享预览图使用白底、灰色文字及无衬线字体，不加彩色装饰，照片保留原图。

### 修改发表论文

在 `index.html` 中搜索 `paper-solar` 等论文 ID，或直接搜索论文标题。每篇论文是一个 `<article class="paper">…</article>` 区块，包含年份、标题链接、作者、期刊及可选的引用或媒体链接。

发表论文标题下方保留斜体说明：`Please email me to request a copy of any paper if you do not have institutional or personal access.`

新增论文时复制相邻的一整块，修改 ID、内容和链接后放入目标位置。所有 ID 必须唯一。作者名使用全文顺序，不使用 “with…”。

```html
<h3 class="paper-title"><a href="https://doi.org/实际DOI">Sentence case title: Subtitle</a></h3>
<p class="authors">Student Name<sup>†</sup>, <strong>Yana Jin</strong><sup>*</sup>, and Other Author</p>
<p class="publication-meta"><strong class="journal">Full Journal Name</strong></p>
```

- 标题统一为 sentence case：标题首词、冒号后副标题首词、问号后新句首词首字母大写；其余按普通英文句子处理，保留 China、Beijing、AnMBR、GHG 等专名与缩写。
- 期刊使用全称，放在 `<strong class="journal">` 中加粗；省略卷、期、页码和文章编号。
- 姓名 `Yana Jin` 放在 `<strong>` 中加粗；标记单独放在姓名后的 `<sup>` 中。
- `†` 的说明统一使用 `Student or advisee coauthor`，涵盖学生或受指导的合作者，不表示每位带标记的学生都由 Yana Jin 正式指导；`*` 表示通讯作者，`§` 表示同等贡献。多个标记可写为 `<sup>*§</sup>`。
- NCC 固定排第一，Water Research 第二；其他论文按年份倒序。
- Water Research 正式书目年份为 2027，同时标注 2026 年在线发表。
- NCC 尚无已确认的正式论文链接，当前标题保留纯文本，并标注 Accepted。取得 DOI 后再添加链接及更新状态。
- NCC 的最终题目为 `Rooftop solar responds to extreme heat and reduces energy poverty among rural households`。
- Water Research 通讯作者为 Ziwei Liu、Kang Xiao；IJERPH 的通讯作者为 Shiqiu Zhang；IRERE 不给 Shiqiu Zhang 标通讯作者。
- 其他已发表论文的顺序、学生及通讯标记依据提供的简历，并优先采用本次明确更正。

### 更新引用次数

引用数字是用户提供的 Google Scholar 快照，不是自动抓取的实时值。

| 论文 ID | 数字 | Google Scholar `cites` 参数 |
| --- | --- | --- |
| `paper-jeem` | 101 | `6058969727618002579,10149483457864703842,5982184499284622667` |
| `paper-allowances` | 86 | `13607675536026009407` |
| `paper-heating` | 129 | `350640741213609892` |
| `paper-pollution-policies` | 557 | `8958190048141401679` |

更新时同时修改链接可见文字中的数字、`aria-label` 中的数字，以及论文区末尾的引用统计月份。链接中保留原有 `cites` 参数，不替换为其他数据库的统计。

HTML 属性里的 `&` 写成 `&amp;`，例如 `?oi=bibs&amp;hl=zh-CN&amp;cites=...`。

### 修改 working papers

搜索 `working-hedonics`、`working-repeated-dce`、`working-cancer`、`working-survey-mode`。本区使用 “with…” 列合作者，不在合作者行重复列 Yana Jin；学生仍标 `†`。hedonics 和两篇与 Yanying Wang 合作的论文另注明 `Corresponding author: Yana Jin`；与 Henrik Andersson、Shiqiu Zhang 合作的 survey mode 论文注明 `First and corresponding author: Yana Jin`。

working paper 标题同样使用 sentence case。两期 DCE 对比文章（`working-repeated-dce`）和 survey mode 文章（`working-survey-mode`）标注 `Under review`；其他文章不补写尚未确定的投稿状态、摘要或下载链接。

### 修改课程和学生

搜索 `id="teaching"` 或 `id="students"`。当前北大 Environmental Economics 为研究生课程，Benefit-Cost Analysis 为本研合上，两门均为 2 学分、独立授课；不列具体开课学期。

学生名单、在读状态和去向采用提供的简历并按本次用户更正更新。高庭苇不列共同指导，和房晨的去向均使用清华经管简称 `Tsinghua SEM`，完整名称 `School of Economics and Management, Tsinghua University` 保留在缩写提示中。

Qiandelong Zhang 同时列在硕士在读和本科校友中。Zixiao Li 同时列在硕士校友和博士在读中，硕士毕业去向为继续在本组攻读北大博士。硕士在读新增傅泽尉，暂按拼音写为 `Zewei Fu`；本科校友新增黄浩洋，写为 `Haoyang Huang`，去向为北大环境学院环境管理博士。Jingtong Lin 的去向更新为 ByteDance。学生区说明采用 `Initial placements and internships`。

William & Mary 本科生校友名单使用原生 `<details>`，点击标题可展开，无需 JavaScript。

更新内容时，记得同步修改页脚 `<time>` 的可见日期和 `datetime`，以及 `sitemap.xml` 中的 `<lastmod>`。若改姓名、任职或网站地址，还应同步修改 `<head>` 内的描述及 JSON-LD 结构化数据；邮箱继续采用 dot/at 写法，不在页面源码或结构化数据中添加完整邮箱。

环境管理系使用英文名称 `Department of Environmental Management`，在学院名上方单列，并同步记入 JSON-LD 的院系层级。

## 后续部署到 GitHub Pages

以下为部署说明，本次没有执行这些步骤。

1. 登录 GitHub 的 `yanajin` 账户，打开 <https://github.com/new>。仓库名填写 `yanajin.github.io`，选择 **Public**，打开 **Add README**，点击 **Create repository**。如果这个仓库已经存在，直接进入现有仓库。
2. 在仓库的 **Code → Add file → Upload files** 页面，从本目录拖入 `index.html`、`styles.css`、`assets` 文件夹、`robots.txt`、`sitemap.xml`、`.nojekyll`。本地的 `README.md` 是维护说明，可留在电脑上。上传的是这些文件和 `assets` 文件夹，不要把外层 `site` 文件夹或压缩包上传进去。
3. 确认上传列表直接显示 `index.html`、`styles.css` 和 `assets/…` 等路径。填写提交说明，如 `Publish personal website`，选择直接提交到 `main`，点击 **Commit changes**。
4. 在仓库的 **Settings → Pages** 中，**Source** 选择 **Deploy from a branch**，**Branch** 选择 `main`，目录选择 `/(root)`，点击 **Save**。
5. 等待部署完成，通过 **Visit site** 访问 `https://yanajin.github.io/`。首次发布或更新可能需要最多 10 分钟；部署进度可在仓库的 **Actions** 中查看。
6. 在正式地址复核照片、导航、论文 DOI、引用链接和手机布局。以后在电脑上修改并保存后，将有变动的文件上传到仓库原位置并提交，网站就会自动更新；只改文字通常只需重新上传 `index.html`。看到旧内容时可用 `Ctrl+F5` 强制刷新。

当前 canonical、分享图片网址、Person 结构化数据、sitemap 和 robots 均按 `https://yanajin.github.io/` 设置。如改用其他域名，搜索并替换这些文件中的站点地址。

原始 DOC 简历、工作要求和 `.site-review` 中的检查截图都在本目录之外；部署只需要本目录中的网站文件。

GitHub 官方说明：
- [创建 GitHub Pages 网站](https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site)
- [配置发布来源](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site)

## 已核对的论文链接

| 论文 | DOI |
| --- | --- |
| Water Research | `10.1016/j.watres.2026.127087` |
| Engineering | `10.1016/j.eng.2025.05.001` |
| International Review of Environmental and Resource Economics | `10.1561/101.00000179` |
| Environmental Science & Technology | `10.1021/acs.est.4c10752` |
| Social Science & Medicine | `10.1016/j.socscimed.2024.117471` |
| Journal of Environmental Economics and Management | `10.1016/j.jeem.2020.102355` |
| Energy Economics | `10.1016/j.eneco.2020.105012` |
| Environmental Research Letters | `10.1088/1748-9326/ab99fe` |
| Energy Policy | `10.1016/j.enpol.2018.12.008` |
| Environment and Development Economics | `10.1017/S1355770X18000414` |
| Journal of Benefit-Cost Analysis | `10.1017/bca.2017.10` |
| International Journal of Environmental Research and Public Health | `10.3390/ijerph13121219` |
