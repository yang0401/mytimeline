# 时间轴更新指南

## 更新流程

### 1. 添加照片到 record/ 文件夹

目录结构：
```
record/
├── [年份]/
│   ├── [月份]月/
│   │   └── [地点]/
│   │       ├── [日期1]/
│   │       │   ├── 照片.jpg
│   │       │   └── 路线图.jpg (可选，文件名含：路线图/行程图/路线/行程/旅程)
│   │       └── [日期2]/
│   │           └── ...
```

### 2. 压缩大图片并生成 events.json

```bash
cd /Users/yangbiao/myTrip
node gen_events.js
```

`gen_events.js` 会自动：
- 扫描 record/ 目录
- 生成 events.json 到 dist/ 文件夹
- 压缩超过 25MB 的图片

### 3. 推送更新到 GitHub

```bash
cd /Users/yangbiao/myTrip/dist
git add .
git commit -m "更新描述"
git push
```

### 4. 等待部署

- GitHub Pages 自动部署，约 1-2 分钟
- 访问地址：https://yang0401.github.io/mytimeline
- jsDelivr CDN 缓存可能需要几分钟刷新

## 相关文件

- `gen_events.js` - 生成 events.json（位于 /Users/yangbiao/myTrip/）
- `dist/` - 部署文件夹，包含所有准备上传的文件
- `dist/events.json` - 时间轴数据
- `dist/record/` - 压缩后的照片

## 注意事项

- 单个文件超过 25MB 无法上传到 GitHub，已自动压缩
- 封面设置功能在 GitHub Pages 版本不可用（需要本地 Node.js 服务器）
- 照片命名规则：行程图/路线图/路线/行程/旅程 会识别为行程图
