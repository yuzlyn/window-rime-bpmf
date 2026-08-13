# window-rime-bpmf

小狼毫 / Rime 的注音臺灣正體配置，基於內建 `bopomofo_tw` 方案，加入 emoji 候選、kaomoji 顏文字，以及 Catppuccin 小狼毫外觀。

> 說明：倉庫名使用 `bpmf`，但目前小狼毫內建方案 ID 是 `bopomofo_tw`。補丁檔必須命名為 `bopomofo_tw.custom.yaml`，否則重新部署後會找不到方案，表現為只能輸入拉丁字母。

## 功能

- 預設啟用 `bopomofo_tw`
- 預設使用臺灣正體字形
- 為 `bopomofo_tw` 增加 emoji 候選開關
- 在 `bopomofo_tw` 內直接用 `/happy`、`/sad` 等符號編碼輸入顏文字
- 使用小狼毫外觀補丁 `weasel.custom.yaml`
- 預設 `Catppuccin` 配色
- 去除候選框陰影，橫排顯示候選

## 安裝

把倉庫內檔案複製到 Rime 使用者目錄。這台電腦的小狼毫使用者目錄是：

```text
D:\rime-data
```

一般小狼毫預設目錄通常是：

```text
%APPDATA%\Rime
```

複製後在小狼毫托盤選單選擇「重新部署」。

## 使用

### 注音輸入

預設方案是 `bopomofo_tw`。這個方案底層使用 Rime 的 `terra_pinyin` 詞典，所以生成 `terra_pinyin.userdb` 是正常現象，不代表切到了拼音方案。

### Emoji 候選

在 `bopomofo_tw` 中輸入中文詞時，候選裡會出現相關 emoji。

可以透過方案選項切換：

```text
無繪文字 / 有繪文字
```

### 顏文字

不用切換方案，在 `bopomofo_tw` 中直接輸入 `/` 加編碼即可。

常用編碼：

```text
/happy      開心
/sad        難過
/angry      生氣
/shy        害羞
/surprise   驚訝
/shrug      攤手
/tableflip  掀桌
/sleep      躺平
/all        常用合集
/kao        全部原始候選
```

示例：

```text
/happy -> ≧▽≦ / ヽ(ﾟ∀ﾟ*)ﾉ / ～(￣▽￣～)(～￣▽￣)～
/sad -> 〒▽〒 / ┬＿┬ / ＞﹏＜
```

### 小狼毫外觀

`weasel.custom.yaml` 預設選擇 `Catppuccin` 配色。

```yaml
"style/color_scheme": Catppuccin
```

候選框陰影已關閉：

```yaml
"style/layout/shadow_radius": 0
"style/layout/shadow_offset_x": 0
"style/layout/shadow_offset_y": 0
```

## 檔案說明

- `default.custom.yaml`：啟用 `bopomofo_tw`
- `bopomofo_tw.custom.yaml`：注音臺灣正體補丁，加入 emoji 過濾器和顏文字符號表
- `kaomoji.schema.yaml`：顏文字獨立方案
- `kaomoji.dict.yaml`：顏文字碼表
- `opencc/`：emoji OpenCC 轉換資料
- `weasel.custom.yaml`：小狼毫 Catppuccin 外觀補丁
- `WEASEL_CUSTOM_THEME.md`：小狼毫自訂配色主題筆記

## 來源

- Catppuccin 小狼毫配色來自既有本機配置，作者標註見 `weasel.custom.yaml`
- emoji 配置來自 [`rime/rime-emoji`](https://github.com/rime/rime-emoji)
- kaomoji 配置來自 GitHub Gist `Godoword/52a37d38b31d8906a844cea880dd95d4`

`rime-emoji` 的授權見 [LICENSE.rime-emoji](./LICENSE.rime-emoji)。
