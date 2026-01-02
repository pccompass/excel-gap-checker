# Excel Gap Checker

A Vue.js web application to detect missing sequential numbers in Excel files. Upload your Excel file, select a column, and instantly see which numbers are missing from the sequence.

## Features

- 📑 **Excel File Support**: Upload `.xlsx` files directly from your browser
- 🔍 **Gap Detection**: Automatically identify missing sequential numbers in any column
- 📄 **Client-Side Processing**: All processing happens in your browser - no server required
- 📈 **Real-Time Results**: Instant feedback with visual highlighting of gaps
- 🌟 **Built with Vue.js 3**: Modern, reactive user interface
- 🌐 **GitHub Pages Ready**: Deploy directly to GitHub Pages without a backend server

## Tech Stack

- **Frontend Framework**: Vue.js 3
- **Build Tool**: Vite
- **Excel Processing**: SheetJS (xlsx)
- **Styling**: CSS3
- **Deployment**: GitHub Pages

## Getting Started

### Prerequisites

- Node.js (v14 or higher)
- npm or yarn

### Installation

```bash
# Clone the repository
git clone https://github.com/pccompass/excel-gap-checker.git
cd excel-gap-checker

# Install dependencies
npm install
```

### Development

```bash
# Start the development server
npm run dev

# The application will be available at http://localhost:5173
```

### Build

```bash
# Build for production
npm run build

# Preview the production build
npm run preview
```

## Usage

1. **Upload Excel File**: Click the file input to select your Excel file
2. **Select Column**: Choose which column contains the sequential numbers
3. **Review Results**: View missing numbers and download the gap report
4. **Export**: Download the list of missing numbers as a file

## How It Works

The application uses SheetJS to read Excel files in the browser and implements the following logic:

1. Parses the Excel file to extract data from selected column
2. Converts values to numbers and removes invalid entries
3. Sorts the numbers and identifies gaps in the sequence
4. Displays results with detailed information about missing numbers

## Deployment to GitHub Pages

To deploy this application to GitHub Pages:

```bash
# Install gh-pages
npm install -D gh-pages

# Add to package.json scripts
"deploy": "npm run build && gh-pages -d dist"

# Run deployment
npm run deploy
```

Your application will be live at: `https://pccompass.github.io/excel-gap-checker/`

## Project Structure

```
excel-gap-checker/
├── public/
├── src/
│   ├── components/
│   ├── App.vue
│   ├── main.js
│   └── style.css
├── index.html
├── vite.config.js
├── package.json
└── README.md
```

## API Reference

### Gap Detection Logic

```javascript
const findGaps = (dataArray) => {
  const gaps = [];
  const sorted = dataArray
    .map(Number)
    .filter(n => !isNaN(n))
    .sort((a, b) => a - b);

  for (let i = 0; i < sorted.length - 1; i++) {
    const current = sorted[i];
    const next = sorted[i + 1];
    if (next - current > 1) {
      for (let missing = current + 1; missing < next; missing++) {
        gaps.push(missing);
      }
    }
  }
  return gaps;
};
```

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

MIT License - feel free to use this project for personal or commercial purposes.

## Support

If you encounter any issues, please create an issue on GitHub.

## Roadmap

- [ ] Support for multiple sheet selection
- [ ] Advanced filtering options
- [ ] Data export in multiple formats (CSV, JSON)
- [ ] Batch processing for multiple columns
- [ ] Dark mode support
- [ ] Internationalization (i18n)

---

Made with ❤️ by [pccompass](https://github.com/pccompass)
