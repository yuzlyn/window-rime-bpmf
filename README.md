# window-rime-bpmf

小狼毫 / Rime 的注音台湾正体配置，基于内置 `bopomofo_tw` 方案，额外加入 emoji 候选、kaomoji 颜文字和「宋」瑞鹤图取色外观。

> 说明：仓库名使用 `bpmf`，但当前小狼毫内置方案 ID 是 `bopomofo_tw`。因此补丁文件必须命名为 `bopomofo_tw.custom.yaml`，否则重新部署后会找不到方案，表现为只能输入拉丁字母。

## 功能

- 默认启用 `bopomofo_tw`
- 为 `bopomofo_tw` 增加 emoji 候选开关
- 在 `bopomofo_tw` 内直接用 `/happy`、`/sad` 等符号编码输入颜文字
- 使用小狼毫外观补丁 `weasel.custom.yaml`
- 内置 `Song` 配色：青绿候选框、赭金高亮、米白文字、深褐边线
- 去除候选框阴影，横排显示候选

## 安装

把仓库内文件复制到 Rime 用户目录，例如 Windows 小狼毫通常是：

```text
%APPDATA%\Rime
```

然后在小狼毫托盘菜单选择“重新部署”。

## 使用

### 注音输入

默认方案是 `bopomofo_tw`。这个方案底层使用 Rime 的 `terra_pinyin` 词典，所以生成 `terra_pinyin.userdb` 是正常现象，不代表切到了拼音方案。

### Emoji 候选

在 `bopomofo_tw` 中输入中文词时，候选里会出现相关 emoji。

可以通过方案选项切换：

```text
無繪文字 / 有繪文字
```

### 颜文字

不用切换方案，在 `bopomofo_tw` 中直接输入 `/` 加编码即可。

常用编码：

```text
/happy      开心
/sad        难过
/angry      生气
/shy        害羞
/surprise   惊讶
/shrug      摊手
/tableflip  掀桌
/sleep      躺平
/all        常用合集
/kao        全部原始候选
```

示例：

```text
/happy -> ≧▽≦ / ヽ(ﾟ∀ﾟ*)ﾉ / ～(￣▽￣～)(～￣▽￣)～
/sad -> 〒▽〒 / ┬＿┬ / ＞﹏＜
```

### 小狼毫外观

`weasel.custom.yaml` 默认选择 `Song` 配色。色板来自瑞鹤图风格：

```text
#47665A  候选框背景
#A38158  高亮候选背景
#F2EDE3  编码、候选文字
#4A3D25  边框、标签、注释
```

候选框阴影已关闭：

```yaml
"style/layout/shadow_radius": 0
"style/layout/shadow_offset_x": 0
"style/layout/shadow_offset_y": 0
```

## 文件说明

- `default.custom.yaml`：启用 `bopomofo_tw`
- `bopomofo_tw.custom.yaml`：注音台湾正体补丁，加入 emoji 过滤器和颜文字符号表
- `kaomoji.schema.yaml`：颜文字独立方案
- `kaomoji.dict.yaml`：颜文字码表
- `opencc/`：emoji OpenCC 转换数据
- `weasel.custom.yaml`：小狼毫「宋」外观补丁

## 来源

- emoji 配置来自 [`rime/rime-emoji`](https://github.com/rime/rime-emoji)
- kaomoji 配置来自 GitHub Gist `Godoword/52a37d38b31d8906a844cea880dd95d4`

`rime-emoji` 的许可证见 [LICENSE.rime-emoji](./LICENSE.rime-emoji)。
