# 收据管理 (my-receipts)

## 扫描收据步骤

1. 用 vFlat Scan 扫描成 jpg 图片文件。
2. 上传到电脑。
3. 使用 Gemini (https://gemini.google.com) 识别收据。需要上传收据的图片文件，并且粘贴上[提示词](./prompt.md)。
4. 把 Gemini 识别出的 json 复制粘贴到一个 json 文件，文件命名为 日期+超市名称.json，如 20251129_FirstChoice.json，并放到相应目录。
5. 把扫描得到的 jpg 文件重命名为 日期+超市名称.jpg，如 20251129_FirstChoice.jpg，并放到相应目录。
