# Testing Guide for Flippr

This guide will help you test the Flippr plugin locally or after deployment.

## Prerequisites

1. **Install Alt1 Toolkit**
   - Download from [runeapps.org/alt1](https://runeapps.org/alt1)
   - Install and open Alt1 Toolkit

2. **Have RuneScape 3 Client Running**
   - Make sure RS3 is running (doesn't need to be logged in for some tests)

## Testing Methods

### Method 1: Local Testing (Development)

1. **Start a Local Server**
   ```bash
   # If you have Python installed:
   python -m http.server 8000
   
   # Or use Node.js:
   npx http-server -p 8000
   
   # Or use VS Code Live Server extension
   ```

2. **Load Plugin in Alt1**
   - Open Alt1 Toolkit
   - Click the Apps button
   - Click "Open App Browser"
   - Navigate to: `http://localhost:8000/plugins/ge-flipper/index.html`
   - Click "Add App" to install

3. **Grant Permissions**
   - When prompted, grant: `capture`, `ocr`, `overlay`, and `chatbox` permissions
   - Make sure Alt1 can detect the RS window

### Method 2: GitHub Pages Testing

1. **Push to GitHub**
   ```bash
   git add .
   git commit -m "Initial Flippr plugin"
   git push origin main
   ```

2. **Enable GitHub Pages**
   - Go to repository Settings → Pages
   - Select source branch (usually `main` or `gh-pages`)
   - Save

3. **Access Plugin**
   - URL will be: `https://yourusername.github.io/alt1plugins/plugins/ge-flipper/index.html`
   - Open in Alt1 app browser and click "Add App"

## Feature Testing Checklist

### ✅ Basic Functionality

- [ ] **Plugin Loads**
  - Open the plugin in Alt1
  - Should show "Alt1 connected" status
  - All tabs should be visible

- [ ] **Manual Order Entry**
  - Go to "Buy Orders" tab
  - Enter item name, price, quantity
  - Click "Add Buy Order"
  - Verify order appears in list
  
  - Go to "Sell Orders" tab
  - Enter item name, price, quantity
  - Click "Add Sell Order"
  - Verify order appears in list

- [ ] **Order Linking**
  - Select a buy order (click on it)
  - Select a sell order (click on it)
  - Click "Link Buy → Sell"
  - Verify both orders show "🔗 Linked"

- [ ] **Statistics Display**
  - Go to "Statistics" tab
  - Verify all stats show (should be 0 initially)
  - Check that stat cards are visible

### ✅ GE Price Check Auto-Detection

- [ ] **Enable Auto-Detection**
  - Go to "Item Tracking" or "Settings" tab
  - Make sure "Auto-detect GE price checks" is checked

- [ ] **Test Price Check Detection**
  1. Log into RuneScape 3
  2. Go to Grand Exchange
  3. Right-click an item → "Check" or "Price Check"
  4. Make sure GE interface is visible on screen
  5. Wait 2-3 seconds
  6. Check "Item Tracking" tab
  7. Item should appear with buy/sell prices and profit calculation

- [ ] **Test Debug Mode**
  - Go to "Settings" tab
  - Enable "Debug Mode"
  - Do a price check in GE
  - Check debug output area - should show OCR text
  - Verify detection regions are correct

### ✅ Chatbox Monitoring

- [ ] **Test Buy Order Completion**
  1. Add a buy order manually (e.g., "Shark", 500 gp, 100 qty)
  2. Actually place the order in GE (or wait for existing order)
  3. Watch chat for: "Your offer to buy X of [item] has finished buying"
  4. Plugin should automatically update the order
  5. Verify "Bought" quantity updates in real-time

- [ ] **Test Sell Order Completion**
  1. Add a sell order manually
  2. Actually place the order in GE
  3. Watch chat for: "Your offer to sell X of [item] has finished selling"
  4. Plugin should automatically update
  5. Verify "Sold" quantity updates

- [ ] **Test Partial Completion**
  1. Place an order in GE
  2. Wait for partial completion message in chat
  3. Verify plugin shows "X/Y" progress
  4. Check overlay notifications appear

- [ ] **Test Auto-Profit Calculation**
  1. Create a buy order and link it to a sell order
  2. Wait for both to complete (or manually mark complete)
  3. Verify profit is automatically calculated
  4. Check "Completed" tab for the flip entry
  5. Verify statistics updated

### ✅ GE Limit Detection

- [ ] **Test Wiki API Fetching**
  1. Add an item manually or via price check
  2. Check "Item Tracking" tab
  3. Verify "GE Limit" shows a number
  4. Verify "Total at Limit" shows total profit calculation

- [ ] **Test OCR Limit Detection**
  1. Price check an item in GE
  2. If buy limit is visible in GE interface
  3. Verify it's detected and shown

- [ ] **Test Common Items**
  - Test with: "Shark", "Rune", "Coal", etc.
  - Verify correct limits are fetched/assigned

### ✅ Data Persistence

- [ ] **Refresh Test**
  1. Add some orders and tracked items
  2. Close Alt1 or refresh the plugin
  3. Reopen plugin
  4. Verify all data is still there

- [ ] **Export/Import Test**
  1. Create some test data (orders, tracked items, completed flips)
  2. Click "Export All Data"
  3. Verify JSON file downloads
  4. Clear data using "Reset Everything"
  5. Click "Import Data"
  6. Select the exported file
  7. Verify all data is restored

## Common Issues & Solutions

### ❌ Alt1 Status Shows "Alt1 library not found"
- **Solution**: Make sure you're opening the plugin through Alt1's app browser, not regular browser

### ❌ "Alt1 connected" but features don't work
- **Solution**: Check permissions - make sure `capture`, `ocr`, `overlay`, and `chatbox` are granted
- Try clicking "Test Detection" in Settings tab

### ❌ Auto-detection not working
- **Solution**: 
  1. Enable Debug Mode in Settings
  2. Check debug output to see what OCR is reading
  3. Adjust detection regions if needed
  4. Make sure GE interface is visible on screen
  5. Try manual entry as fallback

### ❌ Chat monitoring not detecting messages
- **Solution**:
  1. Make sure chatbox permission is granted
  2. Check that ChatboxReader initialized (check browser console)
  3. Verify chat messages are in the visible chat area
  4. Try typing in chat to ensure it's being read

### ❌ GE Limits not showing
- **Solution**:
  1. Check browser console for API errors
  2. May need CORS setup if testing locally
  3. Fallback local database should still work
  4. Manual entry still works without limits

## Quick Test Script

Run through this quick checklist:

```
1. Open plugin in Alt1 → Should see "Alt1 connected"
2. Add manual buy order → Should appear in list
3. Add manual sell order → Should appear in list
4. Link them → Should show linked indicator
5. Go to Statistics tab → Should see active order count = 2
6. Price check an item in GE → Should appear in Item Tracking
7. Check Item Tracking → Should show GE Limit and Total at Limit
8. Export data → Should download JSON file
9. Reset everything → Should clear all data
10. Import data → Should restore previous data
```

## Testing with Real GE Orders

For full testing with actual GE orders:

1. **Small Test Flip**
   - Buy a cheap item (e.g., 100 logs)
   - Link buy and sell order
   - Wait for both to complete
   - Verify auto-profit calculation works

2. **Partial Completion Test**
   - Place a buy order for a high-volume item
   - Watch for partial completion messages
   - Verify progress updates in real-time

3. **Multiple Orders**
   - Track several different items
   - Verify each updates independently
   - Check statistics reflect all activity

## Browser Console Debugging

Open browser console (F12) to see:
- Plugin initialization messages
- OCR detection logs
- Chat message detection
- API fetch results
- Any errors

Look for:
- `"Alt1 connected"`
- `"GE limits database loaded: X items"`
- `"Tracked: [item] ..."`
- `"Buy/Sell update: ..."`

## Next Steps After Testing

1. Fix any bugs found
2. Adjust detection regions if OCR isn't accurate
3. Update GE limits database if common items missing
4. Test with different screen resolutions
5. Verify all edge cases work properly

