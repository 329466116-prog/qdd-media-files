# qdd-media-files

> 个人站点媒体文件托管仓库 · 通过 GitHub + jsdelivr CDN 加速访问

存放 [qdd-website](https://github.com/329466116-prog/qdd-website) 和 [prisma-studio](https://github.com/329466116-prog/prisma-studio) 等个人站点所需的**短音频 / 短视频**资源，通过 jsdelivr CDN 提供全球加速访问。

## 📁 目录结构

```
qdd-media-files/
├── audio/         # 短音频（语音、背景音、播客片段等），建议 ≤ 20MB
│   └── .gitkeep
└── video/         # 短视频（demo、动画、片段等），建议 ≤ 100MB
    └── .gitkeep
```

## 🚀 通过 jsdelivr CDN 访问

仓库公开后，所有文件可通过 jsdelivr CDN 加速访问，URL 格式：

```
https://cdn.jsdelivr.net/gh/329466116-prog/qdd-media-files@<branch>/<path>
```

**示例**：
```html
<!-- 音频 -->
<audio src="https://cdn.jsdelivr.net/gh/329466116-prog/qdd-media-files@main/audio/intro.mp3"></audio>

<!-- 视频 -->
<video src="https://cdn.jsdelivr.net/gh/329466116-prog/qdd-media-files@main/video/demo.mp4"></video>
```

**自动版本化**（推荐）：用 `@main` 始终拉取最新版本，或用 tag/commit 锁版本。

## ⚠️ 资源限制

| 类型 | 单文件建议上限 | 实际稳定 |
|---|---|---|
| 短音频 | 20MB | 20MB |
| 短视频 | 100MB | **50MB** ⚠️ |

- **jsdelivr 对 50MB 以上的文件加速不可靠**，大视频建议走 Cloudflare R2 或 B 站外链
- GitHub 单文件硬上限 100MB

## 🛠️ 使用方式

### 上传新文件
```bash
cd /Users/qiandd/.openclaw/workspace/qdd-media-files
git config --local user.name "qdd-media"  # 隐私作者
git config --local user.email "qdd-media@users.noreply.github.com"

# 复制文件到对应目录
cp /path/to/your.mp3 audio/
# 或
cp /path/to/your.mp4 video/

git add audio/your.mp3
git commit -m "feat(audio): add intro voice"
git push origin main
```

### CDN 缓存更新
jsdelivr 缓存约 24 小时，文件更新后**不会立刻生效**。可通过强制刷新：
```
https://cdn.jsdelivr.net/gh/329466116-prog/qdd-media-files@main/audio/intro.mp3?timestamp=$(date +%s)
```

## 📜 许可证

仅供个人站点使用，未经授权请勿下载或转发。

---

**Owner**: 个人站点维护（隐私作者身份提交）  
**Deploy**: jsdelivr CDN  
**Related**: [qdd-website](https://github.com/329466116-prog/qdd-website) · [prisma-studio](https://github.com/329466116-prog/prisma-studio)
