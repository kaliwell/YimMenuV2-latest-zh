# 构建及本地化来源

- 官方基础：YimMenu/YimMenuV2，enhanced，`bda0d0c7cb5be9721aead38d243f2e5cd5b9ea31`（2026-10-11）。
- 中文词典及 UI 适配来源：legeling/YimMenuV2-zh-cn，`v1.3.1-zh-cn`，`076f1aadde52fd64866b9d0b85208b7a5672ce5b`。
- 沿用 GPL-2.0；原始 LICENSE 和版权声明保留。
- 当前仓库为独立源码快照，提交历史从本地汉化快照开始；不是 YimMenu 官方发布渠道。

移植包括词典、菜单分类/布局、控件标签/说明、热键窗口、首次提示、中文字体支持；另外基于词典翻译 169 个页面固定 UI 调用。没有整套移植旧汉化分支的后台功能、Hook 和特征扫描改动。新增官方功能及动态文本可能仍显示英文。

字体从 Windows Fonts 目录加载，优先微软雅黑，其次黑体等；不重新分发系统字体。

本地构建使用 Visual Studio 2026、MSVC 19.51、Windows SDK 10.0.26100，x64 Release。开启 /utf-8 保证中文文本编码。

```powershell
cmake -S . -B build -G "Visual Studio 18 2026" -A x64
cmake --build build --config Release --target YimMenuV2 --parallel 8
```

编译产物为 `build/Release/YimMenuV2.dll`。其他 Visual Studio 版本可以选择对应 CMake generator；本地未验证其他工具链。

本地验证：编译/链接成功，x64 PE DLL、UTF-8 中文字符串和 diff 空白检查通过；在关闭 BattlEye 后成功加载，游戏画面中中文菜单正常显示。未覆盖所有功能及长期稳定性；此次观察不作为线上兼容性或账号安全保证。

本地 DLL SHA256：`898869c51c9cb6322d0778232aaf5f9a1fd159162970f55e911a6ddb16960fd2`。GitHub CI 使用不同工具链，产物哈希不保证相同。
