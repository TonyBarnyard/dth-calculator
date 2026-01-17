# DTH Drill String Calculator

A comprehensive web-based tool for evaluating Down-The-Hole (DTH) drill string configurations with a multi-supplier consumables database.

![DTH Calculator](https://img.shields.io/badge/Version-1.0-orange) ![License](https://img.shields.io/badge/License-MIT-blue)

## Features

- **Multi-Supplier Database** - Pre-loaded with products from Sandvik, Epiroc, Mincon, and Robit
- **Real-Time Calculations** - Efficiency rating, bailing velocity, cost per metre
- **Custom Item Entry** - Add your own products to the database
- **Print Output** - Technical drawing style reports
- **Offline Capable** - Works without internet once downloaded
- **No Installation Required** - Just open in browser

## Suppliers Included

| Supplier | Products | Website |
|----------|----------|---------|
| Sandvik | RH460, RH510, RH560, RH570 hammers; QL bits | [mining.sandvik](https://www.mining.sandvik) |
| Epiroc | COP M4, M5, M6, M7, M8 series | [epiroc.com](https://www.epiroc.com) |
| Mincon | MP40, MP60, MP80 series | [mincon.com](https://mincon.com) |
| Robit | H4, H6, H8 modular hammers | [robitgroup.com](https://www.robitgroup.com) |

## Quick Start

### Option 1: Use Online (GitHub Pages)
Visit: `https://[your-username].github.io/dth-calculator/`

### Option 2: Download & Run Locally
1. Download or clone this repository
2. Open `index.html` in your browser
3. Start configuring your drill string

## Usage

1. **Select Rig** - Choose SmartROC D65 or Cat MD6250
2. **Browse Database** - Click to open product browser
3. **Select Components** - Choose hammer, bit, and pipe
4. **Review Results** - Check efficiency, bailing velocity, cost/metre
5. **Print Report** - Generate PDF or print configuration

## File Structure

```
dth-calculator/
├── index.html      # Main application
├── database.js     # Product database
├── README.md       # This file
└── LICENSE         # MIT License
```

## Adding Custom Products

### Via Application
1. Click **📦 Database** button
2. Go to **➕ Add New** tab
3. Fill in product details
4. Click **💾 Save Item**

Custom items are saved in your browser's localStorage.

### Via Database File
Edit `database.js` and add entries to the appropriate array:

```javascript
// Example: Add new hammer
{
    id: 'CUSTOM-001',
    supplier: 'custom',
    partNumber: 'YOUR-PART-NUMBER',
    name: 'Your Hammer Name',
    series: 'Series Name',
    size: 6,
    shank: 'QL60',
    airConsumption: 700,
    maxPressure: 30,
    efficiency: 0.90,
    cost: 5000.00,
    lifeMetres: 10000,
    notes: 'Your notes here',
    imageUrl: '',
    productUrl: '',
    rigCompatibility: ['D65', 'MD6250']
}
```

## Calculations

### Bailing Velocity
```
BV (fpm) = CFM Available / Annular Area
Where:
- CFM Available = Rig CFM - Hammer Air Consumption
- Annular Area = π × (Hole Dia² - Pipe OD²) / 4
```

**Target Range:** 7,000 - 9,000 fpm for optimal cuttings removal

### Cost Per Metre
```
CPM = Component Cost / Expected Life (metres)
Total CPM = Hammer CPM + Bit CPM + Pipe CPM + Shock Sub CPM
```

### Efficiency Rating
Weighted calculation based on:
- Pressure efficiency (30%)
- Air efficiency (30%)
- Component matching (40%)

## Supported Rigs

| Rig | Compressor | Max Pressure | Hole Sizes |
|-----|------------|--------------|------------|
| Epiroc SmartROC D65 | 995 CFM | 30 bar | 105-190mm |
| Cat MD6250 | 1350 CFM | 34.4 bar | 200-270mm |

## Browser Compatibility

- ✅ Google Chrome (recommended)
- ✅ Microsoft Edge
- ✅ Mozilla Firefox
- ✅ Safari

## Contributing

Contributions welcome! To add new suppliers or products:

1. Fork this repository
2. Edit `database.js` with new entries
3. Submit a pull request

## License

MIT License - See [LICENSE](LICENSE) file

## Disclaimer

This tool is for evaluation purposes only. Always verify specifications with your supplier before ordering. Actual component performance may vary based on ground conditions, operator technique, and equipment maintenance.

## Contact

For questions or suggestions, open an issue on GitHub.

---

**Built for Australian Mining Operations** 🇦🇺
