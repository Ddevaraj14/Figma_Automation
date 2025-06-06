# Figma_Automation# UI Automation: Live Figma Design Preview

This project enables **live preview of Figma designs** in your browser, with automatic updates whenever you change your Figma file. It consists of a Node.js/Express backend, a React frontend, and scripts to fetch Figma JSON and generate CSS.

---

## Features

- **Auto-fetches Figma JSON** from your Figma file at regular intervals
- **Auto-generates CSS** from Figma design tokens and properties
- **Express server** serves the latest Figma JSON and a static HTML preview
- **React app** renders the Figma design structure and styles in real time
- **Industrial-standard code structure** for scalability and maintainability

---

## Folder Structure

```
UI_Automation/
├── data/
│   └── figma.json                # Latest Figma JSON (auto-fetched)
├── public/
│   ├── preview.html              # HTML preview (static)
│   └── style.css                 # Auto-generated CSS from Figma JSON
├── scripts/
│   ├── autoFetchFigma.js         # Script: fetches Figma JSON on interval
│   ├── fetchFigma.js             # Script: fetches Figma JSON once
│   ├── generateCssFromFigma.js   # Script: generates CSS from Figma JSON
│   └── parser.js                 # Script: generates HTML from Figma JSON (if needed)
├── figma-live-preview/           # React frontend app
│   ├── public/
│   └── src/
│       ├── api/
│       │   └── figma.js
│       ├── components/
│       │   └── FigmaRenderer/
│       │       ├── FigmaRenderer.js
│       │       └── index.js
│       ├── hooks/
│       │   └── useFigmaData.js
│       ├── utils/
│       │   └── figmaStyles.js
│       ├── App.js
│       ├── App.css
│       └── index.js
├── .env                          # Figma API keys (for backend/scripts)
├── package.json                  # Backend/scripts dependencies & scripts
├── server.js                     # Express server
└── README.md
```

---

## Prerequisites

- Node.js (v18+ recommended)
- npm
- A [Figma Personal Access Token](https://www.figma.com/developers/api#access-tokens)
- Your Figma File Key (from the Figma file URL)

---

## Setup & Usage

### 1. **Clone the repository**

```sh
git clone <your-repo-url>
cd UI_Automation
```

### 2. **Install dependencies**

```sh
npm install
cd figma-live-preview
npm install
cd ..
```

### 3. **Configure environment variables**

Create a `.env` file in the project root:

```
FIGMA_TOKEN=your_figma_token
FIGMA_FILE_KEY=your_figma_file_key
```

For the React app, create `figma-live-preview/.env`:

```
PORT=3001
```

### 4. **Run everything with one command**

From the project root:

```sh
npm run dev
```

This will:

- Start the Express server on port 3000
- Start the React app on port 3001
- Start the auto-fetch script to keep `figma.json` and `style.css` up to date

### 5. **View your Figma design**

- **Static HTML preview:**  
  [http://localhost:3000/preview.html](http://localhost:3000/preview.html)
- **React live preview:**  
  [http://localhost:3001/](http://localhost:3001/)

---

## How It Works

1. **Auto-fetch script** (`scripts/autoFetchFigma.js`) pulls the latest Figma JSON every 10 seconds.
2. **CSS generator** (`scripts/generateCssFromFigma.js`) creates `public/style.css` from the Figma JSON.
3. **Express server** serves `/design` (raw JSON), `/preview.html` (static preview), and static assets.
4. **React app** fetches `/design` and renders the design structure and styles using reusable components and hooks.

---

## Customization

- **To support more Figma node types or styles:**  
  Extend `figmaStyles.js` and `FigmaRenderer.js` in the React app, and/or the CSS generator script.
- **To change polling interval:**  
  Edit the interval in `autoFetchFigma.js` and `useFigmaData.js`.

---

## Troubleshooting

- **Port conflicts:**  
  Make sure Express (3000) and React (3001) are not used by other apps.
- **Figma JSON not updating:**  
  Check your `.env` values and ensure your Figma token and file key are correct.
- **Styles not applied:**  
  Ensure `public/style.css` is being generated and linked in your HTML.

---

## License

MIT

---

## Author

Dinesh Devaraj

---

**Enjoy live Figma design previews in your browser!**
