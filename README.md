# PPT 素材浏览库（公开精简包）

本包是 PPT 素材分类结果的公开浏览副本，由源仓库中的
`tools/material_library/publish_bundle.py` 生成。构建脚本本身不随本包分发。

- 本批：**129 张第一版 + 54 张第二版 + 82 张第三版 + 64 张小红书精美PPT + 54 张优秀成果（含跨版本重合，去重后 306 张）**
- 单页：**4,686 个 JPG**；完整页 4,686，局部页 0
- 来源：**306 张**；有单页的来源 263
- 小尺寸页：**407**（低于 500×270 参考尺寸）
- 裁切待复核：**0**，保留异常原因，不作为已确认成品。
- 完全重复来源图：1 对记录

> 本批**在原有正式库基础上新增用户指定“优秀成果”54套、3925页，统一评分4分（视觉效果4分、排版4分）；原文件逐页渲染，逐页分类待复核。**。单页来自缩略页或拼图裁切，清晰度受来源缩略页限制；
> 分类为自动候选，尚未逐页人工认证。这里的“完整”只表示来源页在裁切范围内可见完整，
> 不代表设计质量或可编辑性已经验收。

## 浏览

### 直接打开

双击根目录的 `index.html` 即可。页面使用本地 `data/catalog.js` 内嵌数据，
不依赖服务器、不发起网络请求，`file://` 下可直接工作。

### 可选本地服务器

需要测试 GitHub Pages 行为时，可在本包根目录运行：

```powershell
python -m http.server 8000
```

然后访问 `http://localhost:8000/`。

### GitHub Pages

把本包内容提交到仓库根目录，在仓库 Settings → Pages 中选择从分支根目录部署即可。
所有图片和脚本均使用相对路径，不需要改配置。

## 界面

- 默认打开 **独立幻灯片**，每张图片对应一页 PPT，可单独打开和保存。
- **来源拼图（备份）**保存裁切前的预览图，便于查看出处；独立图片位于 `images/pages/`。
- **批次、风格、布局、来源类型**筛选器，以及 **全部 / 正常裁切 / 裁切待复核 / 来源局部**状态筛选。
- “正常裁切”仅表示没有已记录的几何异常和来源局部标记，不代表人工验收；异常页及来源局部均保留待复核状态。
- **搜索**：标题、用途、风格、布局、角色、来源 ID、单页 ID。
- **缩略图**按需加载，点击卡片查看大图、尺寸、哈希和分类字段。
- **计数**：顶部显示总量，列表上方显示当前筛选结果数量。

## 目录

```text
index.html                 无依赖静态浏览页
data/catalog.json          完整公开目录（来源 + 单页 + 统计 + 词表）
data/catalog.js            同一目录的浏览器内嵌数据
data/sources.json          仅来源清单
data/summary.json          本批统计与限制
data/sources.csv           来源表（UTF-8 BOM）
data/pages.csv             单页表（UTF-8 BOM）
data/summary.csv           汇总表（UTF-8 BOM）
images/sources/*.jpg       来源 JPG 副本
images/pages/*.jpg         单页 JPG 副本
MATERIALS-RIGHTS.md        素材权利说明
.gitignore                 凭据、临时文件、缓存排除规则
```

## 数据字段

来源记录保留：`source_id`、`unit_id`、`batch`、`selected_style`、`source_kind`、
`primary_style`、`sha256`、`page_count`、`duplicate_of`、`name`、
`file_name`、`image`、`style_distribution`、`layout_distribution`。

单页记录保留：`page_id`、`source_id`、`batch`、`source_kind`、`page_no`、
`title`、`style`、`style_tags`、`style_techniques`、`layout`、`role`、
`purpose`、`confidence`、`complete_page`、`small_size`、`width`、`height`、
`sha256`、`image`。`role` 对应页面角色，`purpose` 对应页面用途。
`crop_review_needed` 和 `crop_review_reason` 对应交付记录的“裁切待复核”和“复核原因”；
`source_partial` 来自 uncertainties 中的“来源页面不完整”。这两种标记可以同时存在，筛选时分别保留。
来源 `sha256` 是原件清单哈希，`image_sha256` 是公开 JPG 哈希；单页 `sha256` 是实际裁切 JPG 哈希。
相同 JPG 内容只保存一份；重复来源通过 `unit_id` 共享单页。`preview` 为相对图片路径，不输出 `source_image` 或 `source_path`。
小缩略图按原始像素显示，不放大造细节。

所有 `image` 都是 `images/...` 开头的相对路径；本包不包含源机器上的绝对路径、
用户名、凭据、私有接口配置或原仓库的应用代码。

## 来源类型

| 来源类型 | 数量 |
| --- | ---: |
| 多页预览 | 248 |
| 教程 | 0 |
| 背景素材 | 0 |
| 推广或其他 | 0 |
| 单页 | 4 |
| 设计素材 | 0 |
| PPTX | 30 |
| PDF | 24 |

## 单页风格分布

| 主风格 | 单页数 |
| --- | ---: |
| 科技 | 4195 |
| 中国风 | 280 |
| 商务简约 | 189 |
| 未确定 | 14 |
| 杂志编辑 | 4 |
| 活力创意 | 2 |
| 卡通插画 | 1 |
| 极简 | 1 |

## 单页布局分布

| 主布局 | 单页数 |
| --- | ---: |
| 未确定 | 3925 |
| 复合分区 | 343 |
| 左右分区 | 186 |
| 上下分区 | 66 |
| 多栏 | 65 |
| 中心环绕 | 40 |
| 通栏大图 | 24 |
| 网格 | 23 |
| 单一主体 | 12 |
| 自由错落 | 2 |

## 重建

维护者在源仓库运行（构建脚本不会复制原仓库的 `app/`、处理脚本或凭据）：

```powershell
python tools/material_library/publish_bundle.py --source "<SOURCE_DIR>" --dest "<PUBLIC_DIR>"
```

- `--dry-run`：只校验输入和统计，不写目标目录。
- `--force`：仅当目标目录带有本工具生成的 `.publish-bundle.json` 标记时，
  才替换上一次生成的公开包；无法识别的非空目录会被拒绝。
- `--workers 8`：并发复制 JPG，默认 8 线程。
- `--limit-sources N`：调试用，只取前 N 个来源及其单页。

建议先构建到空目录，再执行 `git init` 和推送；`--force` 不会删除 `.git`。

## 权利与边界

本包**没有**添加根 `LICENSE`，也**没有**对第三方图片作出开源、商用或再分发许可。
代码与图片权利分开：`index.html`、数据文件和构建脚本是整理工具产物；
图片权利归原作者或权利人。使用前请阅读 [MATERIALS-RIGHTS.md](MATERIALS-RIGHTS.md)。

已知限制：

- 分类和裁切来自自动模型与视觉抽查，不是逐页人工认证。
- 小尺寸页是原图限制，不通过放大伪造细节。
- 单页是 JPG 像素裁切，不是 PPTX、SVG 或矢量原稿。
- 来源图中的水印、模板站名称、二维码或推广信息未做清除；本包只做分类和浏览。
