# 智能分拣演示：GLB 优化试验版

此目录是独立试验副本。原 `D:\工创\output\智能分拣网页上传包` 未修改。

## 本地预览

GLB 由网页请求加载，因此请用本地 HTTP 服务预览，不能直接双击 `index.html`：

```powershell
cd D:\工创\output\GLB优化版
python -m http.server 8765
```

在浏览器打开 `http://localhost:8765/`。上传 GitHub Pages 时，将本目录的 `index.html`、`style.css`、`ui-glass.css`、`app.js`、`scene-metadata.js`、`scene.glb` 放在同一发布目录。

## 试验结果

- 原上传包的场景数据 JS 合计约 26 MB；本版 `scene.glb` 约 3.7 MB，另有约 1.9 MB 的应用脚本。
- 保留 47 个独立模型网格及全部 408,089 个三角形，没有减面；滑块、丝杆、连接板和夹爪仍按原有层级控制。
- 使用 Meshopt 压缩，位置和法线在解码后使用浮点顶点。未采用使本机 WebGL 渲染明显变慢的量化顶点方案。
- 浏览器整轮验证：12 件全部完整入盒，各盒 2 件；无页面异常。`加载完成.png` 为初始画面截图。
- 界面参考 [liquid-glass-js](https://github.com/dashersw/liquid-glass-js) 的玻璃层次、边缘高光和圆角风格。为避免与三维模型争夺 WebGL 资源，采用 CSS 绘制这些效果，未加入该库的实时折射画布。
- 模型下载阶段显示真实下载量与百分比；下载结束后继续显示解码、场景组装和路径规划阶段。`加载进度.png` 为限速网络下的进度截图。
- `source` 目录保留本次试验的加载代码与构建脚本；上线只需上述六个网页文件。

这是网页演示优化，不修改 SolidWorks 源装配体，也不代表实机的运动精度或接触力已验证。
