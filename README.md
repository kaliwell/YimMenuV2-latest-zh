# YimMenuV2 最新版中文本地化

基于 [YimMenu/YimMenuV2](https://github.com/YimMenu/YimMenuV2) 的 GTA 5 Enhanced 非官方中文版本。独立维护，不向官方上游自动提交。

当前官方基础提交：`bda0d0c7cb5be9721aead38d243f2e5cd5b9ea31`（2026-10-11）。这是本仓库首次构建时的最新提交，并不代表自动跟踪未来更新。

中文词典与界面适配来自 [legeling/YimMenuV2-zh-cn](https://github.com/legeling/YimMenuV2-zh-cn) 的 `v1.3.1-zh-cn`，保留作者版权及 GPL-2.0 许可证。

## 本地化范围

- 分类、子菜单、按钮、开关、列表、热键窗口和功能说明。
- 首次使用提示及 169 处页面固定文本。
- 从 Windows 系统字体加载中文字形，优先微软雅黑。
- 保留官方当前后台及游戏功能实现。部分最新功能文本、动态字符串和日志可能仍为英文。

## 构建

```powershell
cmake -S . -B build -G "Visual Studio 18 2026" -A x64
cmake --build build --config Release --target YimMenuV2 --parallel 8
```

输出为 `build/Release/YimMenuV2.dll`。GitHub Actions 构建附件提供 DLL 和 SHA256。

详见 [构建说明和来源](docs/localization/BUILD.md)。

## 使用与验证边界

菜单开关：`Insert` 或 `Ctrl+\`。本地测试中关闭 BattlEye 后注入成功，中文菜单正常显示；开启 BattlEye 时普通注入返回访问被拒绝。未验证所有功能和长期稳定性。

请先退出已加载其他菜单版本的游戏，再加载此版本，避免重复 Hook。项目不保证线上模式兼容性或账号安全，也不提供完整反作弊绕过保证。

## 许可证

沿用上游及汉化来源的 [GPL-2.0](LICENSE)。本仓库不是 YimMenu 官方发布渠道。
