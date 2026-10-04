# 智能分拣演示：GLB 优化试验版

此目录是独立试验副本。原 `D:\工创\output\智能分拣网页上传包` 未修改。

## 本地预览

GLB 由网页请求加载，因此请用本地 HTTP 服务预览，不能直接双击 `index.html`：

```powershell
cd D:\工创\output\GLB优化版
python -m http.server 8765
```

在浏览器打开 `http://localhost:8765/`。上传 GitHub Pages 时，将本目录的 `index.html`、`style.css`、`app.js`、`scene-metadata.js`、`scene.glb` 放在同一发布目录。

## 试验结果

- 原上传包的场景数据 JS 合计约 26 MB；本版 `scene.glb` 约 3.7 MB，另有约 1.9 MB 的应用脚本。
- 保留 47 个独立模型网格及全部 408,089 个三角形，没有减面；滑块、丝杆、连接板和夹爪仍按原有层级控制。
- 使用 Meshopt 压缩，位置和法线在解码后使用浮点顶点。未采用使本机 WebGL 渲染明显变慢的量化顶点方案。
- 浏览器整轮验证：12 件全部完整入盒，各盒 2 件；无页面异常。`加载完成.png` 为初始画面截图。
- `source` 目录保留本次试验的加载代码与构建脚本；上线只需上述五个网页文件。

这是网页演示优化，不修改 SolidWorks 源装配体，也不代表实机的运动精度或接触力已验证。
