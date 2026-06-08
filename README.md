# 每日全球經濟新聞

自動收集每天全球經濟相關重大新聞的項目。

## 📋 項目目的

本項目每天自動爬取主要中文經濟新聞網站的新聞，整理成結構化的 JSON 格式，方便查看和分析。

## 📂 目錄結構

```
daily-news/
├── README.md                 # 本文件
├── data/                     # 新聞數據存儲
│   ├── news_YYYY-MM-DD.json # 每日新聞（按日期命名）
│   └── index.json            # 新聞索引
├── scripts/                  # 爬蟲和數據處理腳本
│   ├── scraper.py            # 新聞爬蟲
│   ├── requirements.txt       # Python 依賴
│   └── config.json           # 爬蟲配置
├── .github/
│   └── workflows/
│       └── daily_scrape.yml  # GitHub Actions 工作流程
└── templates/
    └── news_template.json    # 新聞JSON模板
```

## 📰 新聞來源

當前爬取以下中文經濟新聞網站：

- 和訊財經 (hexun.com)
- 新浪財經 (finance.sina.com.cn)
- 東方財富 (eastmoney.com)
- 騰訊財經 (finance.qq.com)
- 搜狐財經 (business.sohu.com)

## 📊 數據格式

每日新聞以 JSON 格式保存在 `data/` 目錄中：

```json
{
  "date": "2026-06-08",
  "last_updated": "2026-06-08T12:30:00Z",
  "source_count": 5,
  "news": [
    {
      "id": "unique_id",
      "title": "新聞標題",
      "source": "來源網站名稱",
      "url": "新聞URL",
      "published_at": "2026-06-08T10:00:00Z",
      "summary": "新聞摘要",
      "category": "股市|匯率|大宗商品|央行|政策|其他",
      "importance": "高|中|低",
      "tags": ["標籤1", "標籤2"]
    }
  ]
}
```

## 🚀 使用方法

### 本地運行爬蟲

```bash
# 安裝依賴
pip install -r scripts/requirements.txt

# 運行爬蟲
python scripts/scraper.py

# 指定日期運行
python scripts/scraper.py --date 2026-06-08
```

### 自動更新

本項目使用 GitHub Actions 每天 UTC+8 時區 00:00 自動運行爬蟲，獲取最新新聞。

## 📝 數據查詢

最新的新聞數據保存在 `data/news_YYYY-MM-DD.json` 中。

可以通過以下方式查看：
- 直接查看 JSON 文件
- 使用 `data/index.json` 查看所有新聞索引

## 🔧 配置

編輯 `scripts/config.json` 修改爬蟲配置：

```json
{
  "sources": ["hexun", "sina", "eastmoney", "qq", "sohu"],
  "timeout": 10,
  "retry_count": 3,
  "min_summary_length": 20
}
```

## ⚙️ 技術棧

- Python 3.9+
- Requests - HTTP 請求
- BeautifulSoup4 - 網頁解析
- Lxml - XML 解析
- GitHub Actions - 自動化定時任務

## 📄 許可證

MIT License

## 🤝 貢獻

歡迎提交 Issue 和 Pull Request！

---

最後更新：2026-06-08