# Pigeon 🕊️

**The Aesthetic API Client** — A beautiful, powerful, and privacy-first API client that lives in your browser. Supports HTTP, GraphQL, WebSocket, SSE, TCP, UDP, MQTT, Socket.IO, and more.

![Pigeon Preview](assets/brand/pigeon-wordmark.svg)

---

## At a Glance

| Metric | Count |
|--------|-------|
| **Protocols** | 8 (HTTP, GraphQL, WebSocket, SSE, TCP, UDP, MQTT, Socket.IO) |
| **Help Center Pages** | 22+ |
| **Tools & Features** | 25+ |
| **Build Targets** | Chrome Extension (Manifest V3) |

---

## Features Overview

### 🎨 Design
- Linear-inspired dark UI with glassmorphism effects
- Inter & JetBrains Mono fonts for typography
- Smooth animations and micro-interactions
- Status-coded responses with color coding

### 🪄 Tab Siphon (Magic Wand)
One click to pull the URL, cookies, and headers from your current browser tab into the request editor. Perfect for authenticated API testing.

### 📝 Request Lab
- **All HTTP Methods**: GET, POST, PUT, PATCH, DELETE, HEAD, OPTIONS
- **Smart Headers**: Autocomplete for common headers (Content-Type, Authorization, etc.)
- **Body Types**: JSON, Text, URL-encoded, Form-data
- **Authentication**: Bearer Token, Basic Auth, API Key

### 🎯 Smart Formatting
- Auto-detects JSON, HTML, XML responses
- One-click pretty printing
- Collapsible JSON tree view
- Click-to-copy for any JSON path or header value

### 📚 Local History
- Saves last 50 requests locally
- Search and filter through history
- One-click restore any previous request
- 100% private — zero data leaves your machine

### 🔒 Privacy First
- All data stored in `chrome.storage.local`
- No cloud sync, no accounts, no tracking
- CORS bypass via background service worker

---

## Installation & Build

### From Source (Development)

1. **Clone the repository**
   ```bash
   git clone https://github.com/your-username/pigeon-extension.git
   cd pigeon-extension
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Build the extension**
   ```bash
   npm run build
   ```

4. **Load in Chrome**
   - Open Chrome → `chrome://extensions/`
   - Enable "Developer mode" (toggle in top right)
   - Click "Load unpacked"
   - Select the `dist` folder

### Build Commands

| Command | Description |
|---------|-------------|
| `npm run build` | TypeScript compile + Vite build → outputs to `dist/` |
| `npm run dev` | Vite dev server with hot reload |
| `npm run relay` | Start the TCP/UDP relay (WebSocket bridge on `ws://127.0.0.1:17890`) |
| `npm run relay:test` | Run relay end-to-end tests |
| `npm run preview` | Preview the built app |

### Supported Environments

- **Chrome** (Manifest V3)
- **Chromium-based browsers** (Edge, Brave, etc.) — load unpacked from `dist/`

---

## Help Center (End-to-End Guide)

The following is a dump of the in-extension Help Center. Use it as a reference for every major feature.

---

### 1. Get Moving in 30 Seconds

- **Quick Guide**: Interactive tour through collections → runner → history → GraphQL → WebSocket → SSE → TCP → UDP
- **Import Petstore**: One-click Swagger Petstore import with ready-to-run collection + environment
- **Jump to live protocols**: GraphQL demo, Binance WebSocket, Wikipedia SSE, TCP echo, UDP echo / DNS lookup

**Pro tip**: Everything is linkable. Use the left navigation for full docs; each page has a table-of-contents and "Try it now" buttons.

---

### 2. Quickstart: Send Your First Request

1. **Enter a URL and hit Send**
   - Paste URL into the URL bar
   - Select HTTP method (GET, POST, …)
   - Press **Send** (or ⌘/Ctrl + Enter)

2. **Inspect the response**
   - Status, time, size for quick regression checks
   - Headers for caching, auth challenges, content-type
   - Body viewer with JSON pretty-printing and search

3. **Save to a Collection**
   - Use **Collections** tab in sidebar
   - Click the **Save** icon to add the current request

**Shortcut**: ⌘/Ctrl + Enter sends a request from anywhere. Use `?` or F1 to open the Help Center.

---

### 3. Import Swagger / OpenAPI

**Fastest path: Petstore (demo)**
- Pigeon fetches the Swagger Petstore spec and generates a collection with endpoints and sample payloads
- Creates: (1) collection with folders + requests, (2) environment with variables like `baseUrl`

**Step-by-step (any OpenAPI URL)**
1. Open **Import / Export** (sidebar bottom)
2. Select **Swagger / OpenAPI**
3. Paste the JSON/YAML URL (swagger.json / openapi.json)
4. Click **Fetch**

**Troubleshooting**: If fetch fails, verify the URL is reachable and returns valid JSON/YAML. Pigeon uses a background fetch to reduce CORS friction.

---

### 4. Collections

**Create & structure**
1. Sidebar → **Collections**
2. Type a name in "New collection name…" and hit **+**
3. Use folders to group endpoints (Auth, Users, Orders…)

**Save the current request**
- When you've tuned headers/body/auth, save into a collection for reuse and sharing

**Run a collection**
- Each collection has a **Run** button
- Executes requests sequentially and records a structured result set

**Export docs**
- **Markdown** for wikis and READMEs
- **OpenAPI** for tooling pipelines
- **Runner** generates an **HTML Report** with timings, statuses, assertions, per-request details

---

### 5. Collections Runner

**How it works**
- Requests run **in order** (top → bottom)
- Each request can read environment variables and output new ones
- Assertions validate status codes, JSON paths, headers, timing rules

**Export reports (JSON + HTML)**
- **JSON Report** for automation pipelines and CI artifacts
- **HTML Report** for humans — open the downloaded file in any browser

**Best practices**
- Put login/token refresh first; write tokens to env vars
- Keep "create" requests separate from "cleanup" (or use folders)
- Use a dedicated environment for runner flows (e.g. `staging`)

---

### 6. History & Replay

**What gets stored**
- Request URL, method, headers, body
- Response status, headers, body (where applicable)
- Timing and size metrics

**Load from history**
1. Sidebar → **History**
2. Expand an entry (click the row)
3. Click **Load Request** to restore into the editor

**cURL on demand**: Use "Copy cURL" to share a reproduction snippet without exporting files.

---

### 7. GraphQL Mode

**Switch to GraphQL**
- In the Request Type selector, pick **GraphQL**
- Editor becomes query-focused with Variables and Headers tabs

**Built-in Guide**
- Click **📚 Guide** for interactive tutorials
- Each loads a working query + variables + endpoint
- Load one, hit Send, then tweak variables to explore

**Sample**: `https://countries.trevorblades.com/`

---

### 8. WebSocket Mode

**Try Binance BTC/USDT (sample)**
- Ready-to-use Binance trade stream
- Switch to WebSocket and connect to `wss://stream.binance.com:9443/ws/btcusdt@trade`

**The WebSocket workspace**
- **Get Started** shows sample endpoints and handshake flow
- **Message list** separates sent vs received; supports filtering + search
- **Copy** any message payload for bug reports or replay

**Note**: Some networks block `wss://`. If connect fails, try a different endpoint or network.

---

### 9. SSE Mode (Server-Sent Events)

**Try Wikipedia Recent Changes (sample)**
- High-volume real-time feed of edits
- URL: `https://stream.wikimedia.org/v2/stream/recentchange`

**Filter by event type**
- Pigeon detects event types and lets you filter (e.g. only `message` or specific named events)

**SSE vs WebSocket**: SSE is one-way (server → client) and auto-reconnects. WebSocket is bidirectional.

---

### 10. TCP Mode

**How TCP works in Pigeon**
- Browsers can't open raw TCP sockets directly
- Pigeon uses a **local WebSocket relay** that bridges TCP ↔ WebSocket

**Run the TCP/UDP relay**
1. Download the relay script (from Help Center or `relay/pigeon-relay.cjs`)
2. Run: `node pigeon-relay.cjs`
3. Relay starts on `ws://127.0.0.1:17890`
4. In Pigeon → TCP panel → Advanced, keep Relay URL as `ws://127.0.0.1:17890` (unless changed)

**Quickstart: built-in echo server**
- After starting the relay, connect to `127.0.0.1:9000`
- Click **Connect**, then send `hello`
- You should see `echo: hello` in the live stream

**Encoding & framing**
- **utf8**: sends text as-is
- **hex** and **base64**: for binary payloads
- **Append newline**: for line-delimited servers

---

### 11. UDP Mode

**How UDP works in Pigeon**
- UDP is connectionless
- Pigeon uses the relay to send/receive datagrams and keeps a live event log

**Quickstart: built-in UDP echo**
- After starting the relay, connect to `127.0.0.1:9999`
- Click **Connect**, then send `hello`
- You should see `echo: hello` in the live stream

**DNS Lookup (A record)**
- Pigeon includes a built-in **DNS Lookup** demo in the UDP panel
- Enter a domain (e.g. `google.com`), click **Connect**, then **Resolve**
- Sends a proper DNS A-record query to Google DNS (8.8.8.8:53) and parses the response to show resolved IPs
- **Why DNS?** DNS uses UDP on port 53. This demo shows how to send binary protocols over UDP — the query is built from the domain name and sent as base64-encoded bytes

**Tip**: Many UDP protocols expect binary payloads — use **hex** or **base64** when needed.

---

### 12. Environments & Variables

**What variables solve**
- Switch `baseUrl` between environments without editing each request
- Store tokens and reuse across requests and runner flows
- Share a collection while keeping secrets local in env variables

**How to use**
1. Sidebar → **Env**
2. Create an environment and add variables (e.g. `baseUrl`)
3. Reference variables in requests using the variable syntax shown in the UI

**Imported specs**: Swagger/OpenAPI import creates an environment automatically.

---

### 13. Keyboard Shortcuts & Command Palette

- Press **?** or **F1** for Help Center
- Open Keyboard Shortcuts from the Tools menu
- Use the Command Palette for instant navigation

---

### 14. Templates

- Tools → **Templates** for reusable request blueprints
- Reduces repetitive setup (auth headers, pagination, etc.)

---

### 15. Request Inspector

- Tools → **Request Inspector**
- Deep-dive debugging for headers, timing, and payloads
- Inspect what was actually sent and received in a structured view

---

### 16. Export / Import (Request Exchange)

- Tools → **Export/Import**
- Export requests and collections; import from Postman, cURL, etc.
- **cURL workflow**: Copy cURL from History (or exporter) to share a request without files

---

### 17. Benchmark

- More → Testing → **Benchmark**
- Load-test an endpoint with repeatable runs
- Measures latency distribution, success rate, throughput

**Tips**
- Benchmark a stable environment (staging)
- Use same env vars across runs for clean comparisons
- Track P95/P99, not just average latency

---

### 18. Mock Server

- More → Protocols → **Mock Server**
- Spin up predictable responses for frontend development
- Mock APIs locally to unblock UI work and reproduce edge cases

---

### 19. MQTT Client

- More → Protocols → **MQTT Client**
- Publish/subscribe to IoT topics
- Test MQTT topics and payloads with built-in client UI

---

### 20. Socket.IO

- More → Protocols → **Socket.IO**
- Dedicated client UI for Socket.IO connections
- Supports namespaces, rooms, auth patterns
- **Troubleshooting**: Force WebSocket via `transports: ["websocket"]`; enable CORS on server; Socket.IO URL is HTTP(S), not WS(S)

---

### 21. Network Capture

- More → Protocols → **Network Capture**
- Inspect and capture network traffic signals
- Debug requests, headers, payloads at the network layer

---

### 22. Cookie Manager

- More → Data → **Cookie Manager**
- View and manage cookies relevant to API auth flows
- Debug cookie-based sessions, CSRF flows, domain-scoped auth

---

### 23. Storage Inspector

- More → Data → **Storage Inspector**
- Inspect local/session storage and related state
- Debug auth tokens stored in web storage and app state persistence

---

## Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `⌘/Ctrl + Enter` | Send Request |
| `?` or `F1` | Open Help Center |

---

## Tech Stack

| Layer | Technology |
|-------|------------|
| **Frontend** | React 18 + TypeScript |
| **Styling** | Tailwind CSS |
| **State** | Zustand |
| **Build** | Vite |
| **Syntax Highlighting** | prism-react-renderer |

---

## Design Tokens

| Token | Value | Usage |
|-------|-------|-------|
| Background | `#0a0a0a` | Main background |
| Surface | `#111111` | Cards, panels |
| Border | `#262626` | Borders, dividers |
| Pigeon Blue | `#5DA9E9` | Primary accent |
| Success | `#10B981` | 2xx responses |
| Warning | `#F59E0B` | 5xx responses |
| Error | `#F43F5E` | 4xx responses |

---

## Project Structure

```
pigeon-extension/
├── src/
│   ├── components/
│   │   ├── ui/           # Reusable UI components
│   │   ├── Header.tsx
│   │   ├── RequestEditor.tsx
│   │   ├── ResponseViewer.tsx
│   │   ├── HistorySidebar.tsx
│   │   ├── TcpUdpPanel.tsx
│   │   └── ...
│   ├── store.ts          # Zustand state management
│   ├── types.ts          # TypeScript definitions
│   ├── lib/              # curl, codegen, dns, swaggerImporter, etc.
│   ├── App.tsx
│   └── main.tsx
├── public/
│   ├── manifest.json     # Chrome extension manifest (V3)
│   ├── background.js     # Service worker (CORS bypass, relay bridge)
│   ├── relay/
│   │   └── pigeon-relay.cjs  # TCP/UDP WebSocket bridge
│   └── icons/
├── relay/
│   └── pigeon-relay.cjs  # Source relay script
└── dist/                 # Built extension (load this in Chrome)
```

---

## License

MIT License — feel free to use, modify, and distribute.

---

Made with ☕ and TypeScript
