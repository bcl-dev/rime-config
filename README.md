# rime-config

雾凇拼音（rime-ice）+ 小鹤双拼的个人偏好，打包为 [plum](https://github.com/rime/plum) recipe。

## 安装

```
rime-install iDvel/rime-ice:others/recipes/full
rime-install bcl-dev/rime-config:flypy
```

然后在小狼毫中「重新部署」。补丁以 `__patch` 块追加到各 `.custom.yaml`，重复执行会原地更新，不会覆盖设置界面写入的内容。

## 内容

| 文件 | 补丁 |
|---|---|
| `default.custom.yaml` | 候选词 7 个 |
| `weasel.custom.yaml` | 皮肤 `purity_of_form_custom`；字号候选 12、序号 12、注释 11 |
| `double_pinyin_flypy.custom.yaml` | 默认英文标点；输入框不把双拼展开为全拼 |
| `rime_ice.custom.yaml` | 默认英文标点 |

## Windows 小狼毫注意

若 Git 不在 `C:\Program Files\Git`，小狼毫「获取更多输入方案」会误用 WSL 的 `bash.exe`。
在 `C:\Program Files\Rime\weasel-<版本>\rime-install-config.bat` 末尾加：

```bat
set PATH=<Git 安装目录>\usr\bin;<Git 安装目录>\cmd;%PATH%
```
