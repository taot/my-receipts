识别这张收据，列出详细信息。
对每个商品，识别出：
    - 英文商品名称 (name_en)
    - 中文商品名称 (name_cn) (如果没有，则空着)
    - 单价 (unit_price) (如果没有，则空着)
    - 数量 (quantity) 或 重量 (weight) (如果没有，则空着)
    - 总价 (total_price)
    - tags (如果有，则尽量识别输出)
对于整张收据，识别出:
    - 超市名称 (store)
    - 日期 (date) (如 2025-11-29)
    - 时间 (time) (精确到分钟，如 13:41)
    - 商品个数 (item_count)
    - 税前总价 (subtotal)
    - 税 (tax)
    - 税后总价 (total_amount)
并且输出其他的信息:
    - receit_id (日期 + 超市名称 + 自增id)
    - image_path (以日期为目录, receipt_id 为文件名)
    - currency (币种，如未特殊说明，通常为 CAD)

输出这样的 json:
```
{
  "receipt_id": "20251129_FirstChoice_001",
  "store": "First Choice Supermarket",
  "date": "2025-11-29",
  "time": "13:41",
  "item_count": 25,
  "subtotal": 83.88,
  "tax": 0.26,
  "total_amount": 84.14,
  "currency": "CAD",
  "image_path": "20251129/20251129_FirstChoice_001.jpg",
  "items": [
    {
      "name_en": "YUTAKA IMITATION CRAB STI",
      "name_cn": "豐字蟹柳500G",
      "category": "FROZEN",
      "quantity": 1,
      "unit_price": 5.99,
      "total_price": 5.99
    },
    {
      "name_en": "PAK FOK FRESH TOFU",
      "name_cn": "百福新鮮大桶豆腐 12PCS",
      "category": "FROZEN",
      "quantity": 1,
      "unit_price": 5.49,
      "total_price": 5.49
    },
    {
      "name_en": "BLUEBRRIES BLEUETS",
      "name_cn": "盒裝藍莓",
      "category": "FRUIT",
      "quantity": 1,
      "unit_price": 3.99,
      "total_price": 3.99,
      "tags": ["ON SALE"]
    },
    {
      "name_en": "BLUEBRRIES BLEUETS",
      "name_cn": "盒裝藍莓",
      "category": "FRUIT",
      "quantity": 1,
      "unit_price": 3.99,
      "total_price": 3.99,
      "tags": ["ON SALE"]
    },
    {
      "name_en": "MERILIN MUSHROOM SHIITAKE",
      "name_cn": "美林金錢菇250G",
      "category": "GROCERY",
      "quantity": 1,
      "unit_price": 7.99,
      "total_price": 7.99
    },
    {
      "name_en": "CBL REDUCED-SALT BEAN PA",
      "name_cn": "蔥伴侶減鹽豆瓣醬 450G",
      "category": "GROCERY",
      "quantity": 1,
      "unit_price": 2.99,
      "total_price": 2.99
    },
    {
      "name_en": "ERJIE MARINADE SEASONING",
      "name_cn": "二姐無渣鹵料五香味90G",
      "category": "GROCERY",
      "quantity": 1,
      "unit_price": 1.99,
      "total_price": 1.99
    },
    {
      "name_en": "TUNG-I NOODLE SNACK - SP",
      "name_cn": "小浣熊乾脆面辣蟹味 35G",
      "category": "GROCERY",
      "quantity": 4,
      "unit_price": 0.50,
      "total_price": 2.00,
      "note": "4 /for $2.00"
    },
    {
      "name_en": "MERILIN LILY BULBS",
      "name_cn": "美林百合120G",
      "category": "GROCERY",
      "quantity": 1,
      "unit_price": 6.39,
      "total_price": 6.39
    },
    {
      "name_en": "PRB SHANDONG RAMEN NOO",
      "name_cn": "珠江橋牌山東拉麵2KG",
      "category": "GROCERY",
      "quantity": 1,
      "unit_price": 3.99,
      "total_price": 3.99,
      "tags": ["ON SALE"]
    },
    {
      "name_en": "AJ DRIED RED DATE",
      "name_cn": "亞傑去核雞心棗 170G",
      "category": "GROCERY",
      "quantity": 1,
      "unit_price": 2.29,
      "total_price": 2.29
    },
    {
      "name_en": "AJ WHITE LOTUS SEED",
      "name_cn": "亞傑優品坊通心白蓮 200G",
      "category": "GROCERY",
      "quantity": 1,
      "unit_price": 6.99,
      "total_price": 6.99
    },
    {
      "name_en": "CUIHONG MARINADE SEASONI",
      "name_cn": "翠宏老鹵調料190G",
      "category": "GROCERY",
      "quantity": 1,
      "unit_price": 3.29,
      "total_price": 3.29
    },
    {
      "name_en": "PRB BROWN SUGAR IN PIECE",
      "name_cn": "珠江橋牌特級冰片糖454G",
      "category": "GROCERY",
      "quantity": 1,
      "unit_price": 0.99,
      "total_price": 0.99,
      "tags": ["ON SALE"]
    },
    {
      "name_en": "PRB TOP GRADE OYSTER FLA",
      "name_cn": "珠江橋牌頂級蠔油510G",
      "category": "GROCERY",
      "quantity": 1,
      "unit_price": 2.99,
      "total_price": 2.99,
      "tags": ["ON SALE"]
    },
    {
      "name_en": "ORGANIC GINGER",
      "name_cn": "有機生姜 (红袋)",
      "category": "VEGETABLE",
      "weight": 1.97,
      "price_per_unit": 1.99,
      "total_price": 3.92
    },
    {
      "name_en": "BUTTERCUP SQUASH",
      "name_cn": "媽咪瓜",
      "category": "VEGETABLE",
      "weight": 3.63,
      "price_per_unit": 0.79,
      "total_price": 2.87
    },
    {
      "name_en": "CROWN BROCCOLI",
      "name_cn": "無莖西蘭花",
      "category": "VEGETABLE",
      "weight": 0.75,
      "price_per_unit": 1.99,
      "total_price": 1.49
    },
    {
      "name_en": "NAI YU BOK CHOY",
      "name_cn": "奶油白菜",
      "category": "VEGETABLE",
      "weight": 1.62,
      "price_per_unit": 1.79,
      "total_price": 2.90
    },
    {
      "name_en": "CHIVES FLOWER (WRAPPED)",
      "name_cn": "韭菜花 (包裝)",
      "category": "VEGETABLE",
      "weight": 0.79,
      "price_per_unit": 5.59,
      "total_price": 4.42
    },
    {
      "name_en": "VEGETABLE",
      "name_cn": "",
      "category": "VEGETABLE",
      "quantity": 1,
      "unit_price": 3.63,
      "total_price": 3.63
    },
    {
      "name_en": "VEGETABLE",
      "name_cn": "",
      "category": "VEGETABLE",
      "quantity": 1,
      "unit_price": 3.29,
      "total_price": 3.29
    }
  ]
}
```
