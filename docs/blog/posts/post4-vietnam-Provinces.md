# 🇻🇳 Vietnamese Provinces Database（ベトナム行政区データベース）

`vietnamese-provinces-database` は、ベトナムの行政区情報（省・市、郡・区、町・村）を階層構造で提供する JSON データセットです。  
開発者やデータ分析者がアプリやシステムに簡単に統合できるよう、わかりやすく構造化されています。

---

## ✅ 特徴

- ベトナムの行政単位に関する完全なSQL（非SQL）データベース。ベトナム全34省と、それに関連する地区、区、小区分が含まれています。
- データは最新の法令19/2025/QĐ-TTgに基づいて更新されています。

---

## 📦 主な用途

- フォーム入力での都道府県・市町村選択  
- 配送アプリや地域マップでの利用  
- 地方ごとの統計分析、可視化  
- ERP・CRMシステムでの顧客管理

---

## 🚀 使用例

```json
{
  "name": "Hà Nội",
  "code": "01",
  "districts": [
    {
      "name": "Quận Ba Đình",
      "wards": [
        { "name": "Phường Phúc Xá" },
        { "name": "Phường Trúc Bạch" }
      ]
    }
  ]
}
````

---

## 📁 データソース

* ベトナム統計総局 (Tổng cục Thống kê)
* 公的なオープンデータ
* 最新の行政改編に基づいて更新

---

## 🌏 関連リソース
日本版のオープンデータとして、open-data-jp-municipalities リポジトリがあります。これは日本の市区町村データを JSON 形式で提供し、ベトナム版と同様に開発者向けに構造化されています。日本には47都道府県があり、このリポジトリでそのリストを提供しています。国際的なアプリ開発や比較分析に役立ちます。
```json
{
  "code": "131024",
  "name_kanji": "中央区",
  "name_romaji": "Chuo Ku",
  "lat": "35.666667",
  "lon": "139.766667",
  "prefecture_kanji": "東京都",
  "prefecture_kana": "とうきょうと",
  "prefecture_romaji": "Tokyo To"
}
```

---

📍 GitHub リンク:
- https://github.com/thanglequoc/vietnamese-provinces-database
- https://github.com/piuccio/open-data-jp-municipalities

