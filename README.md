# Trading Journal

A professional trading journal dashboard for tracking and analyzing your trading performance on Scalable Capital.

🌐 **Multi-Device Sync:** Access your trading journal from any device (work laptop, personal laptop, phone) with automatic GitHub Gist synchronization!

## 📁 Project Structure

```
trading/
├── strategies/              # Strategy template documentation (JSON files)
│   └── .gitkeep
├── trading-journal.html     # Trading journal dashboard (standalone)
├── GITHUB_SETUP.md          # GitHub Pages deployment & sync setup guide
└── README.md
```

## 🎯 Overview

### Trading Workflow

1. **Technical Analysis** - Analyze markets using TradingView or your preferred charting platform
2. **Trade Execution** - Execute trades on Scalable Capital based on your strategy signals
3. **Performance Tracking** - Log and analyze trades using the Trading Journal Dashboard

### Trading Journal Dashboard

A self-contained, browser-based dashboard for tracking and analyzing your trading performance. No installation required - just open the HTML file in your browser.

## 📊 Trading Journal Dashboard

### Features

✅ **Track Both Open and Closed Trades**
- Log open positions with risk tracking
- Record closed trades with P&L and R:R analysis

✅ **Auto-Calculations**
- P&L automatically calculated based on position size
- Risk:Reward ratios computed from entry, exit, and stop loss
- Risk exposure tracked for open positions

✅ **Performance Metrics**
- Win Rate, Total P&L, Average R:R
- Profit Factor, Expectancy, Average Win/Loss
- Open positions summary with total risk exposed

✅ **Data Management**
- Export trades to CSV (European format: DD/MM/YYYY)
- Full backup/restore via JSON import/export
- Import strategy templates from JSON files
- All data persists in browser localStorage

✅ **Multi-Device Sync** 🆕
- Automatic sync across all devices using GitHub Gist
- Works on work laptop, personal laptop, and phone
- Auto-sync every 30 seconds
- Offline support with automatic sync when reconnected
- One-time setup with GitHub Personal Access Token

✅ **Professional UI**
- Dark mode theme optimized for trading
- Responsive design (desktop, tablet, mobile)
- Search, filter, and sort functionality
- Pagination for large trade histories

### Getting Started

#### Option A: Access via GitHub Pages (Recommended for Multi-Device Use)

🌐 **Access from anywhere:** https://boydiego.github.io/trading/trading-journal.html

**Benefits:**
- Access from work laptop, personal laptop, and phone
- No need to download files
- Always the latest version
- Automatic GitHub Gist sync keeps all devices in sync

**Setup Required:**
1. Enable GitHub Pages (one-time, 2 minutes) - see [GITHUB_SETUP.md](GITHUB_SETUP.md)
2. Configure GitHub sync (one-time per device, 1 minute) - see [GITHUB_SETUP.md](GITHUB_SETUP.md)

📖 **Full deployment guide:** [GITHUB_SETUP.md](GITHUB_SETUP.md)

#### Option B: Open Locally (Single Device)

Simply double-click `trading-journal.html` - it opens in your browser. No installation or setup required!

**Supported Browsers:** Chrome, Firefox, Safari, Edge, Brave

**Note:** This option uses localStorage only (no multi-device sync)

#### 2. Import Your Strategies (Optional)

Create strategy template files in the `strategies/` folder:

```json
{
  "name": "Trend Following",
  "description": "Follow strong trends with momentum confirmation",
  "entry_rules": [
    "Price above 50 EMA",
    "RSI > 50",
    "Volume confirmation"
  ],
  "exit_rules": [
    "Price crosses below 20 EMA",
    "RSI < 40",
    "Stop loss triggered"
  ],
  "risk_management": {
    "stop_loss_type": "ATR-based",
    "atr_multiplier": 2.0,
    "position_sizing": "1% account risk per trade"
  }
}
```

Then click **"Import Strategies"** in the dashboard to load them into the strategy dropdown.

#### 3. Setup Multi-Device Sync (Optional but Recommended)

**If you want to sync across multiple devices:**

1. **Create GitHub Personal Access Token** (one-time, 2 minutes)
   - Go to https://github.com/settings/tokens/new
   - Note: "Trading Journal Sync"
   - Expiration: "No expiration" (or 90 days)
   - Select scope: **✓ gist** (only this permission)
   - Click "Generate token" and copy it

2. **Configure Sync** (on each device)
   - Open the dashboard
   - Click **"⚙️ Setup GitHub Sync"** button
   - Paste your GitHub token
   - Click "Save & Enable Sync"

**That's it!** Your trades will now sync automatically across all devices every 30 seconds.

See [GITHUB_SETUP.md](GITHUB_SETUP.md) for detailed instructions.

#### 4. Add Your First Trade

**For Open Positions:**
- Fill in: Date, Symbol, Direction (Long/Short), Entry Price, Stop Loss, Position Size, Status: **Open**
- The dashboard shows your risk exposure

**For Closed Trades:**
- Fill in all fields above PLUS Exit Price
- Set Status to **Closed**
- P&L and R:R are calculated automatically

#### 5. Track Your Performance

- **Metrics Dashboard** - View win rate, total P&L, profit factor, and more
- **Trade History** - Search, filter, and analyze all your trades
- **Export Data** - Regular backups to CSV or JSON

### Dashboard Sections

#### Performance Metrics (Closed Trades)
- Win Rate, Total P&L, Avg R:R, Total Trades
- Winning/Losing trade counts and percentages
- Average Win/Loss amounts
- Profit Factor and Expectancy
- Best and Worst trades

#### Open Positions
- Number of open positions
- Total risk exposed (in EUR)
- Average entry price

#### Trade Entry Form
- Date (DD/MM/YYYY format)
- Symbol (e.g., BTCUSD, AAPL, etc.)
- Direction (Long/Short)
- Entry Price, Exit Price (optional for open trades), Stop Loss
- Position Size
- Status (Open/Closed)
- Strategy (dynamically loaded from imported strategies)
- Notes (for trade analysis and observations)

#### Trade History Table
- Sortable columns (click headers to sort)
- Color-coded rows:
  - 🟦 Blue = Open positions
  - 🟩 Green = Winning trades
  - 🟥 Red = Losing trades
- Filter by: Status, Symbol, Strategy
- Search by symbol
- Edit or delete trades

### Data Format

All data is stored in your browser's localStorage:

- **Currency:** EUR (€)
- **Date Format:** DD/MM/YYYY (European format)
- **Time:** Date only (no time component)

### Auto-Calculations

#### For All Trades:
```
Risk = |Entry Price - Stop Loss| × Position Size
```

#### For Closed Trades Only:
```
P&L (Long)  = (Exit Price - Entry Price) × Position Size
P&L (Short) = (Entry Price - Exit Price) × Position Size

Reward = |Exit Price - Entry Price| × Position Size
Risk:Reward = Reward / Risk  (displayed as "1:X.XX")
```

### Data Export/Import

**Export to CSV** - For analysis in Excel/Google Sheets
- European date format (DD/MM/YYYY)
- All trade details included

**Export to JSON** - Full backup with all fields
- Includes metadata (version, export date)
- Perfect for backup and restore

**Import from JSON** - Restore your trades
- Validates JSON structure before importing
- Replaces current data (export first to backup!)

### Strategy Management

**Import Strategies:**
1. Create JSON files in the `strategies/` folder with a "name" field
2. Click **"Import Strategies"** in the dashboard
3. Select one or more JSON strategy files
4. Strategy names are added to the dropdown and persisted

**Default Strategy:** "Custom" (always available for ad-hoc trades)

### Tips for Best Results

✅ **Regular Updates** - Log trades as soon as they close for accurate tracking

✅ **Detailed Notes** - Use the Notes field to record your thought process and lessons learned

✅ **Backup Regularly** - Export to JSON weekly to prevent data loss

✅ **Review Metrics** - Check your performance metrics weekly/monthly to identify improvement areas

✅ **Strategy Tracking** - Categorize trades by strategy to see which setups work best

✅ **Risk Management** - Monitor your open positions total risk exposure

### Browser Compatibility

The dashboard works on all modern browsers:
- ✅ Google Chrome
- ✅ Mozilla Firefox
- ✅ Safari
- ✅ Microsoft Edge
- ✅ Brave Browser

**Note:** Requires JavaScript and localStorage enabled.

### Data Storage

All data is stored locally in your browser using localStorage:
- **Capacity:** ~5-10MB (approximately 5,000-10,000 trades)
- **Privacy:** Your data never leaves your device
- **Offline:** Works completely offline after initial load

### Troubleshooting

**Q: My data disappeared!**
- localStorage is browser-specific. Did you switch browsers?
- Did you clear browser data? Always export backups regularly!

**Q: I get "Storage quota exceeded" error**
- Export old trades to CSV/JSON
- Delete historical trades you no longer need
- Consider starting a new journal for the next year

**Q: Can I use this on multiple devices?**
- localStorage is device-specific
- Use Export/Import to sync between devices manually
- Export on Device A → Import on Device B

**Q: The dashboard won't load**
- Check that JavaScript is enabled in your browser
- Try a different browser
- Clear browser cache and reload

## 🔧 Development

The trading journal is a single HTML file with embedded CSS and JavaScript:
- **No build process** required
- **No dependencies** needed
- **Pure vanilla** HTML/CSS/JavaScript
- **BEM naming convention** for CSS classes

To modify:
1. Open `trading-journal.html` in a text editor
2. Make your changes
3. Save and refresh in browser

## 📝 License

This project is for personal use in trading analysis and performance tracking.

## 🙏 Acknowledgments

- Scalable Capital for trade execution platform
- Modern web technologies for offline-capable applications

---

**Happy Trading! 📈**
