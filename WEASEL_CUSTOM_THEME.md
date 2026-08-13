# 小狼毫自定義配色主題設定

這份說明適用於 Windows 小狼毫 Weasel。外觀主題只需要修改 `weasel.custom.yaml`，不要改 `default.custom.yaml` 或輸入方案檔，因為那些檔案控制方案清單、注音行為、字典和轉換規則。

## 需要新增什麼

在 `weasel.custom.yaml` 的 `patch:` 底下新增或擴充：

```yaml
patch:
  preset_color_schemes/+:
    my_theme:
      name: "我的主題"
      author: "your_name"
      back_color: 0x303446
      border_color: 0x51576D
      candidate_text_color: 0xC6D0F5
      comment_text_color: 0xB5BFE0
      hilited_back_color: 0xCA9EE6
      hilited_candidate_back_color: 0xCA9EE6
      hilited_candidate_text_color: 0x303446
      hilited_comment_text_color: 0x303446
      hilited_label_color: 0x303446
      hilited_text_color: 0xCA9EE6
      label_color: 0xA5ADCE
      shadow_color: 0x00000000
      text_color: 0xC6D0F5
```

`my_theme` 是主題 key，這個名稱最重要，後面預設使用時要完全一致。`name` 是顯示名稱，可以用中文。

## 需要修改什麼

在同一個 `patch:` 底下，把小狼毫預設使用的主題指定成你的主題 key：

```yaml
patch:
  "style/color_scheme": my_theme
```

如果檔案裡已經有 `"style/color_scheme": Song` 或其他主題，把值改成你的主題 key 即可：

```yaml
"style/color_scheme": my_theme
```

## 完整範例

```yaml
customization:
  distribution_code_name: Weasel
  distribution_version: 0.17.4
  generator: "yuzlyn"
  rime_version: 1.13.1

patch:
  preset_color_schemes/+:
    my_theme:
      name: "我的主題"
      author: "yuzlyn"
      back_color: 0x303446
      border_color: 0x51576D
      candidate_text_color: 0xC6D0F5
      comment_text_color: 0xB5BFE0
      hilited_back_color: 0xCA9EE6
      hilited_candidate_back_color: 0xCA9EE6
      hilited_candidate_text_color: 0x303446
      hilited_comment_text_color: 0x303446
      hilited_label_color: 0x303446
      hilited_text_color: 0xCA9EE6
      label_color: 0xA5ADCE
      shadow_color: 0x00000000
      text_color: 0xC6D0F5

  "style/color_scheme": my_theme
  "style/font_face": "Noto Emoji, 更纱黑体 UI SC"
  "style/label_font_face": "更纱黑体 UI SC"
  "style/comment_font_face": "更纱黑体 UI SC"
  "style/font_point": 13
  "style/label_font_point": 11
  "style/comment_font_point": 12
  "style/horizontal": true
  "style/inline_preedit": true
  "style/layout/align_type": bottom
  "style/layout/border": 1
  "style/layout/spacing": 5
  "style/layout/candidate_spacing": 20
  "style/layout/hilite_spacing": 5
  "style/layout/hilite_padding": 5
  "style/layout/margin_x": 0
  "style/layout/margin_y": 0
  "style/layout/round_corner": 5
  "style/layout/corner_radius": 10
  "style/layout/shadow_radius": 0
  "style/layout/shadow_offset_x": 0
  "style/layout/shadow_offset_y": 0
```

## 色值格式

小狼毫配色使用 `0xRRGGBB` 格式。例如：

```text
#303446 -> 0x303446
#CA9EE6 -> 0xCA9EE6
```

透明色可使用：

```yaml
shadow_color: 0x00000000
```

## 常用欄位

| 欄位 | 用途 |
| --- | --- |
| `back_color` | 候選窗背景 |
| `border_color` | 候選窗邊框 |
| `text_color` | 輸入碼文字 |
| `candidate_text_color` | 候選詞文字 |
| `comment_text_color` | 註釋文字，例如編碼 |
| `label_color` | 候選序號 |
| `hilited_back_color` | 高亮輸入區背景 |
| `hilited_text_color` | 高亮輸入文字 |
| `hilited_candidate_back_color` | 選中候選詞背景 |
| `hilited_candidate_text_color` | 選中候選詞文字 |
| `hilited_comment_text_color` | 選中候選詞註釋 |
| `hilited_label_color` | 選中候選詞序號 |
| `shadow_color` | 陰影顏色 |

## 套用步驟

1. 修改 `D:\rime-data\weasel.custom.yaml`。
2. 確認 `preset_color_schemes/+` 裡的主題 key 和 `"style/color_scheme"` 完全一致。
3. 重新部署小狼毫。

在這台電腦可以執行：

```powershell
& 'D:\rime\weasel-0.17.4\WeaselDeployer.exe' /deploy
```

部署後可檢查生成檔：

```powershell
Select-String -LiteralPath 'D:\rime-data\build\weasel.yaml' -Pattern 'color_scheme|my_theme'
```

如果結果出現：

```yaml
color_scheme: my_theme
```

就代表預設主題已套用。

## 注意事項

- `preset_color_schemes/+` 下面的 key 不能寫錯；`my_theme` 和 `"style/color_scheme": my_theme` 必須完全相同。
- 不要只改 `name`。`name` 只是顯示名稱，真正被引用的是主題 key。
- `weasel.custom.yaml` 是 Windows 小狼毫外觀設定，不要把 Android Trime 主題設定混進來。
- 重新部署後才會更新 `build/weasel.yaml`，只改原始檔不會立刻生效。
- `build/` 是生成目錄，正常情況下不要手動改 `build/weasel.yaml`。
