# pc-clean-trustdb

「电脑清理小工具」的**识别库**（开机启动项白名单 / 推广库），供工具在线更新使用。

软件在「关于 · 联系」页的「更新识别库」按钮、或命令行 `/trustupdate` 会把这份 `trust.txt` 拉下来合并：
内置 68 条 + 在线库若干条，一起参与判定。

## 怎么用

1. 在线更新：在 `profile.txt` 里写 `trustUrl=https://raw.githubusercontent.com/guhang42-jpg/pc-clean-trustdb/main/trust.txt`
2. 手动更新：点「更新识别库」
3. 批量更新：`电脑清理小工具.exe /trustupdate`
4. 国内 raw 抽风时会自动改用 jsDelivr 镜像（`https://cdn.jsdelivr.net/gh/guhang42-jpg/pc-clean-trustdb@main/trust.txt`）

## 文件格式

一行一条，UTF-8 编码：

```
# ver=20261124
keep|ctfmon|输入法框架，关了打字会乱
bloat|pingbao|360 的弹窗推手
```

- `keep` = 别关（系统组件、驱动、安全软件、外设驱动、远程协助）
- `bloat` = 建议关闭（推广、捆绑、弹窗推手、常驻更新器）
- 两者都命中时按 `keep` 处理（防误伤）
- 顶部 `# ver=` 会显示在软件界面上，改内容时顺手改日期

## 维护原则

- `bloat` 只写**具体到某个程序**的词，不写 `update` 这种大词，避免把正常软件误判
- 每月把客户机上真实遇到的 5–10 个程序加进来，尤其"看着像正经软件、其实是推广常驻"的
- 库里只给"建议"，不会自动动手，最终由人勾选
