# Trading Project

A comprehensive trading analysis and journaling project combining TradingView technical indicators with a performance tracking dashboard.

## 📁 Project Structure

```
trading/
├── indicators/              # TradingView Pine Script indicators
│   ├── indicator.pine       # MACD Dual indicator
│   ├── strategy.pine        # MACD Dual + KAMA strategy
│   └── triple_macd_histogram.pine  # Triple MACD histogram indicator
├── strategies/              # Strategy template documentation (JSON files)
│   └── .gitkeep
├── trading-journal.html     # Trading journal dashboard (standalone)
└── README.md
```

## 🎯 Overview

### Trading Workflow

1. **Technical Analysis** - Use TradingView with custom Pine Script indicators for market analysis
2. **Trade Execution** - Execute trades on Scalable Capital based on strategy signals
3. **Performance Tracking** - Log and analyze trades using the Trading Journal Dashboard

### Components

#### 1. TradingView Indicators (`indicators/`)

Custom Pine Script indicators for technical analysis:

- **MACD Dual + KAMA Strategy** - Complete trading strategy with entry/exit signals
  - Primary MACD (60/130/45) for trend confirmation
  - Secondary MACD (12/26/9) on 4H timeframe
  - KAMA baseline as trend filter
  - ATR-based stop loss management

- **MACD Dual Indicator** - Multi-timeframe MACD visualization

- **Triple MACD Histogram** - Three-level MACD analysis across different timeframes

#### 2. Trading Journal Dashboard (`trading-journal.html`)

A self-contained, browser-based dashboard for tracking and analyzing your trading performance.

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

✅ **Professional UI**
- Dark mode theme optimized for trading
- Responsive design (desktop, tablet, mobile)
- Search, filter, and sort functionality
- Pagination for large trade histories

### Getting Started

#### 1. Open the Dashboard

Simply double-click `trading-journal.html` - it opens in your browser. No installation or setup required!

**Supported Browsers:** Chrome, Firefox, Safari, Edge, Brave

#### 2. Import Your Strategies (Optional)

Create strategy template files in the `strategies/` folder:

```json
{
  "name": "MACD Dual + KAMA",
  "description": "Strategy using dual MACD with KAMA baseline",
  "entry_rules": [
    "Histogram rising (green)",
    "Secondary MACD above zero",
    "Price above KAMA baseline"
  ],
  "exit_rules": [
    "Price falls below KAMA",
    "Secondary MACD falls below zero",
    "Stop loss triggered"
  ],
  "risk_management": {
    "stop_loss_type": "ATR-based",
    "atr_multiplier": 3.0,
    "position_sizing": "1% account risk per trade"
  }
}
```

Then click **"Import Strategies"** in the dashboard to load them into the strategy dropdown.

#### 3. Add Your First Trade

**For Open Positions:**
- Fill in: Date, Symbol, Direction (Long/Short), Entry Price, Stop Loss, Position Size, Status: **Open**
- The dashboard shows your risk exposure

**For Closed Trades:**
- Fill in all fields above PLUS Exit Price
- Set Status to **Closed**
- P&L and R:R are calculated automatically

#### 4. Track Your Performance

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

### TradingView Indicators

The Pine Script indicators are designed for TradingView. To use them:

1. Open TradingView
2. Open Pine Editor (bottom of screen)
3. Copy the indicator code from the `indicators/` folder
4. Paste into Pine Editor
5. Click "Add to Chart"

### Trading Journal

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

- TradingView for the excellent charting platform
- Pine Script for custom indicator capabilities
- Scalable Capital for trade execution

---

**Happy Trading! 📈**
