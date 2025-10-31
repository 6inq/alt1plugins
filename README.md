# Alt1 Plugins Collection

A collection of helpful Alt1 plugins for RuneScape 3, designed to enhance gameplay with automation, tracking, and quality-of-life improvements.

## 📦 Available Plugins

### 🪓 Elder Tree Timer
**Version:** 0.5.0  
**Status:** ✅ Active

Tracks Elder Tree chop timers (5 minutes) and cooldowns (10 minutes) across all three locations (Edgeville, Varrock, Yanille). Features automatic detection via OCR, per-location tracking, overlay HUD, sound alerts, and comprehensive statistics.

#### Features:
- 🎯 **Automatic Detection**: Uses chat OCR and screen popup detection to automatically start timers
- 📍 **Location Detection**: Auto-detects your current location via banner and minimap OCR
- ⏱️ **Per-Location Tracking**: Tracks timers, logs, and XP separately for each Elder Tree location
- 📊 **Statistics**: Tracks total logs, XP, and chop count across all sessions
- 🔊 **Sound Alerts**: Customizable pre-alert sound before timer completion
- 🖥️ **Overlay HUD**: Optional in-game overlay showing current location timers
- 💾 **Data Export/Import**: Backup and restore your progress
- 📈 **Session Tracking**: Runtime and cumulative statistics

#### Usage:
1. Install via Alt1 app browser
2. Open the plugin in Alt1
3. Select your current location or let auto-detection handle it
4. The plugin will automatically detect when you start chopping via chat messages
5. Use the overlay HUD toggle for in-game timer display
6. Configure pre-alert timing for notifications before timer completion

#### Detection Methods:
- Chat message detection: "you begin to swipe at the tree"
- Center popup OCR: Detects "no branches... regrow shortly" message
- Banner OCR: Detects location name from area banner
- Minimap OCR: Fallback location detection from minimap

---

### 💰 Flippr
**Version:** 1.1.0  
**Status:** ✅ Active

Comprehensive Grand Exchange flipping tracker with profit margins, tax calculations, historical data, and detailed statistics. Automatically detects GE price checks and tracks items with profit calculations - similar to Runelite's Flipping plugin for OSRS.

#### Features:
- 🎯 **Auto-Detection**: Automatically detects GE price checks and tracks items with profit calculations
- 📊 **Order Tracking**: Track buy and sell orders separately with full details
- 🔗 **Order Linking**: Link buy orders to sell orders for automatic profit calculation
- 💵 **Profit Calculation**: Automatic profit/loss calculation with 1% GE tax included (per item and total)
- 📈 **Real-time Statistics**: Running totals for profit, ROI, success rate, and more
- 📜 **Historical Data**: Complete history of all completed flips with dates and details
- 📋 **Item Tracking**: Per-item profit tracking with price history and check counts
- 📋 **Watchlist**: Track items you're monitoring for potential flips
- 💾 **Export/Import**: Backup and restore all your flipping data
- 🎯 **Key Metrics**: Total profit, average profit per flip, best flip, ROI percentage, success rate
- ⚡ **Runelite-Style**: Similar functionality to OSRS Runelite Flipping plugin

#### Usage:
1. Install via Alt1 app browser
2. Open Flippr in Alt1
3. **Auto-detection**: Simply price check items in GE - they'll be automatically tracked with profit per item shown
4. View tracked items in the "Item Tracking" tab to see profit margins for each item
5. Add buy orders when you place offers in GE (or use "Create Order" from tracked items)
6. Add sell orders when you list items for sale
7. Link buy and sell orders together (select both, click "Link Buy → Sell")
8. Mark sell orders as complete to automatically calculate profit and update statistics
9. View your completed flips in the "Completed" tab
10. Export your data regularly to backup your trading history

#### Statistics Tracked:
- **Total Profit**: Cumulative profit/loss from all completed flips
- **Total Flips**: Number of completed flip transactions
- **Active Orders**: Current number of pending buy/sell orders
- **Total Invested**: Total amount spent on buy orders
- **Avg Profit/Flip**: Average profit per completed flip
- **Success Rate**: Percentage of profitable flips
- **Best Flip**: Highest profit from a single flip
- **ROI %**: Return on investment percentage

---

## 🛠️ Installation

### For Users:
1. Install [Alt1 Toolkit](https://runeapps.org/alt1) if you haven't already
2. Open Alt1 app browser
3. Navigate to the plugin's URL (e.g., `https://6ing.github.io/alt1plugins/plugins/elder-timer/index.html`)
4. Click "Add App" to install the plugin
5. Grant necessary permissions (capture, OCR, overlay) when prompted

### For Developers:
```bash
# Clone the repository
git clone https://github.com/yourusername/alt1plugins.git
cd alt1plugins

# Plugins are standalone HTML/CSS/JS files
# Edit files directly or serve locally for testing
```

---

## 📝 Plugin Structure

Each plugin follows this structure:
```
plugins/
  └── plugin-name/
      ├── index.html          # Main HTML interface
      ├── main.js            # Plugin logic
      ├── style.css          # Styling
      ├── appconfig.json     # Alt1 app configuration
      └── icon.png           # Plugin icon (optional)
```

---

## 🤝 Contributing

Contributions are welcome! Please follow these guidelines:

1. **New Plugins**: Create a new folder in `plugins/` following the structure above
2. **Updates**: Update version numbers and document changes in the plugin's section
3. **Code Style**: Follow existing code patterns and Alt1 best practices
4. **Testing**: Test thoroughly before submitting changes

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 🙏 Credits

**Author:** Gingie  
**Alt1 Toolkit:** [RuneApps](https://runeapps.org/)

---

## 📞 Support

For issues, suggestions, or questions:
- Open an issue on GitHub
- Contact via Alt1 app or Discord

---

## 🔄 Changelog

### Elder Tree Timer
- **v0.5.0** - Added statistics tracking, export/import functionality, improved completion alerts
- **v0.4.0** - Per-location live panels, overlay HUD, banner + minimap OCR, audio pre-alert

### Flippr
- **v1.1.0** - Added auto-detection of GE price checks, per-item profit tracking with price history, Runelite-style features
- **v1.0.0** - Initial release with comprehensive profit tracking, margins, taxes, historical data, and statistics

---

## 💡 Tips

- **Elder Tree Timer**: Enable overlay HUD for hands-free timer monitoring while playing
- **Flippr**: Enable auto-detection to automatically track items when you price check them in GE. The plugin will show profit per item, margin, and track price history. Link buy and sell orders immediately when both are placed to track complete transactions. Export your data regularly to maintain a backup of your trading history.
- Keep plugins updated for the latest features and bug fixes
- Export your data regularly to prevent data loss
- Use sound alerts to avoid missing timer completions when multitasking
