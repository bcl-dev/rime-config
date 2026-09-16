# rime-config

雾凇拼音（rime-ice）+ 小鹤双拼的个人偏好，打包为 [plum](https://github.com/rime/plum) recipe。

## 安装

```
rime-install iDvel/rime-ice:others/recipes/full
rime-install bcl-dev/rime-config:flypy
```

然后「重新部署」。补丁以 `__patch` 块追加到各 `.custom.yaml`，重复执行会原地更新，不会覆盖设置界面写入的内容。

## 内容

| 文件 | 补丁 |
|---|---|
| `default.custom.yaml` | 候选词 7 个 |
| `weasel.custom.yaml` | 字号候选 12、序号 12、注释 11；皮肤见下 |
| `double_pinyin_flypy.custom.yaml` | 默认英文标点；输入框不把双拼展开为全拼 |
| `rime_ice.custom.yaml` | 默认英文标点 |

## 皮肤

同一 recipe 内附带仿 macOS 原生输入法的配色 `macos_light` / `macos_dark`：系统蓝高亮、序号无点号、横排、紧凑留白。

| 文件 | 补丁 |
|---|---|
| `squirrel.custom.yaml` | 注册两套配色并启用，跟随系统浅色/深色外观；字号候选 14、序号 10、注释 12；圆角 6、高亮圆角 4、留白横 8 竖 6 |
| `weasel.custom.yaml` | 注册两套配色并启用，跟随系统深色模式（需小狼毫 0.15+）；布局沿用 rime-ice 的 `style/layout` |

两端都设了 `style/color_scheme`，装上即生效。代价是小狼毫「输入法设定」里改皮肤会在下次部署时被配方覆盖；想改回界面切换，删掉 `flypy.recipe.yaml` 中 weasel 部分的 `style/color_scheme*` 两行再重装即可。

鼠鬚管留白 = `border_width/height` + `corner_radius`，收紧时两项一起调。配色方案里出现的字段会覆盖 `style/` 下的同名全局值，所以布局类字段只写在 `style/`。

## Windows 小狼毫注意

若 Git 不在 `C:\Program Files\Git`，小狼毫「获取更多输入方案」会误用 WSL 的 `bash.exe`。
在 `C:\Program Files\Rime\weasel-<版本>\rime-install-config.bat` 末尾加：

```bat
set PATH=<Git 安装目录>\usr\bin;<Git 安装目录>\cmd;%PATH%
```
