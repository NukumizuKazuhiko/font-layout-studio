# 终末地字体自由排版工具 · Endfield Font Layout Studio

单文件、完全离线的字体预览 / 自由排版 / 导出工具。双击 `index.html` 即可使用，**零网络依赖**——字体与 opentype.js 全部以 base64 内嵌，不请求任何 CDN 或外部资源。

在线体验（GitHub Pages）：<https://nukumizukazuhiko.github.io/font-layout-studio/>

## 功能

- **实时预览**：字号、字距、行高、颜色、背景色 / 透明背景
- **导入字体**：本地 `.ttf` / `.otf` / `.woff` / `.woff2`
- **内置字体**：EndfieldByButan（默认）、Noto Sans Hans Black、Novecento Wide UltraBold，下拉切换；base64 采用懒解码，首次选中时才转成 ArrayBuffer 并缓存，页面启动不受体积影响
- **自由排版**：启用后每个字符成为独立字形，可鼠标 / 手指拖到任意位置，并单独设置字号、旋转角度与颜色；导出范围与画布完全一致（所见即所得）
- **参考线**：可添加水平 / 垂直参考线，拖动移动、双击删除；「吸附：开 / 关」随时切换
- **智能吸附**：拖动字形时自动吸附到参考线、画布中线与其他字形碰撞箱的边缘 / 中心，并显示对齐辅助线
- **紧贴碰撞箱**：按「当前字体 + 该字」真实渲染逐字测量墨迹（含浏览器回退字体），每种字体独立计算、不套统一模板；无墨迹的字（空格等）不参与吸附与裁切；旋转后同步旋转
- **键盘微调**：方向键移动、`[` `]` 旋转、`-` `=` 缩放、`Delete` 删除
- **导出**：PNG（支持透明背景）与 SVG（字形转为 `path` 轮廓而非 `<text>`，可无损缩放与二次编辑）；可选「自动裁切空白」，输出只保留全部墨迹的外接矩形，不带四周大片空白

## 使用

1. 下载仓库中的 `index.html`（约 12 MB，含内嵌字体）
2. 双击用浏览器打开（Chrome / Edge 等现代浏览器）
3. 输入文本 → 调整样式 → 需要逐字摆放时点「启用自由排版」→ 导出 PNG / SVG

> 文件较大是因为字体被完整内嵌；首次打开或首次切换内置字体时浏览器需要解码，可能有 1–2 秒延迟，属正常现象。

## 许可

**前端代码**（本仓库全部 HTML / CSS / JavaScript，包括自由排版、参考线吸附、碰撞箱解析、PNG / SVG 导出等实现）以 **GPL-3.0** 许可发布，完整文本见 [LICENSE](LICENSE)。

**字体不属于本项目，GPL-3.0 不适用于任何字体文件。** 字体版权归原作者 / 原厂商所有，仓库中仅为离线预览目的内嵌：

| 字体 | 权利归属 | 许可 |
| --- | --- | --- |
| EndfieldByButan | 《明日方舟：终末地》相关同人字体，版权归原作者 | 未附授权，请勿再分发或商用 |
| Noto Sans Hans Black | Google | SIL Open Font License 1.1 |
| Novecento Wide UltraBold | Sintype（商业字体） | 版权归原作者，分发 / 商用需自行取得授权 |

内嵌的 [opentype.js](https://github.com/opentypejs/opentype.js) 以 MIT 许可发布，版权归其原作者。

若你只是想要一个不含上述字体的纯净版本，可移除 `index.html` 中的 `@font-face` base64 数据与 `BUILTIN_EXTRA_FONTS` 脚本块，工具本身的「导入字体」功能不受影响。
