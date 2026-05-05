# Browser & OS Detection Tool Pro

A modern, single-file browser diagnostics dashboard that detects the visitor’s browser, operating system, device profile, feature support, privacy exposure, security context, storage, network, battery, and more.

The tool runs entirely in the browser. It does **not** require a backend, build step, database, login system, or external API.

---

## Preview

Open `browser_os_detection_tool_pro.html` in any modern browser.

The app automatically scans the current environment and displays:

- Browser name, version, icon, and rendering engine
- Operating system and platform details
- Device type, touch support, language, timezone, CPU threads, and memory
- Screen size, viewport, pixel ratio, and orientation
- Network connection type, online/offline state, round-trip time, and data saver status
- Battery status where the browser allows it
- Storage estimate and persistent-storage support
- Permissions status for supported browser permissions
- Web platform feature support
- Security score, capability score, and privacy exposure score
- AI-style local insights and recommendations
- Exportable full JSON diagnostics report
- Local scan history using `localStorage`

---

## Features

### Browser and OS Detection

Detects common browsers and engines, including:

- Chrome
- Microsoft Edge
- Brave
- Firefox
- Safari
- Opera
- Vivaldi
- Samsung Internet
- Internet Explorer fallback
- Blink, WebKit, Gecko, and Trident engine detection

Detects common platforms, including:

- Windows
- macOS
- Linux
- Android
- iOS
- iPadOS
- ChromeOS
- Windows Phone fallback

---

### Feature Support Dashboard

The app checks a wide set of browser APIs and groups them into useful sections.

#### Graphics and Compute

- Canvas
- WebGL
- WebGL 2
- WebGPU
- WebAssembly
- OffscreenCanvas
- WebCodecs

#### App and Offline

- Service Workers
- Cache Storage
- IndexedDB
- LocalStorage
- Notifications
- Push API
- Background Sync

#### Media and Input

- WebRTC
- Camera and microphone access
- Screen capture
- Speech recognition
- Speech synthesis
- Vibration
- Pointer Events

#### Security and Platform

- Secure context
- Web Crypto API
- Permissions API
- Credential Management
- Payment Request
- Clipboard API
- File System Access

#### Sharing and UX

- Web Share
- Fullscreen
- View Transitions
- Popover API
- Dialog element
- IntersectionObserver
- ResizeObserver

---

## Scoring System

The dashboard includes three quick-read scores.

### Capability Score

Shows how many tested modern browser features are supported.

### Security Score

Checks whether the page is running in a secure browser context and whether important security-related APIs are available.

### Privacy Exposure Score

Estimates how many browser and device signals are exposed to the page.

A higher privacy exposure score does **not** always mean something is wrong. Modern browsers expose many capability signals by design. The score is meant to help users understand how fingerprintable their environment may be.

---

## Smart Insights

The app generates local recommendations based on detected support.

Examples:

- Warns if the page is not running in a secure context
- Warns if Service Workers are unavailable
- Warns if WebGL is unavailable
- Notes if WebGPU is available
- Notes if Data Saver is enabled
- Warns if camera or microphone permission is already granted
- Explains high or low privacy exposure

These insights are generated locally in JavaScript.

---

## Export and Sharing Tools

The dashboard includes:

- Copy user-agent string
- Copy full diagnostics report
- Export report as JSON
- Share report using the native Web Share API where available
- Fallback copy-to-clipboard support

---

## Local Scan History

Recent scans are stored in the browser using `localStorage`.

Stored history includes:

- Browser name
- Browser version
- OS name
- Device type
- Capability score
- Privacy exposure score
- Scan timestamp

No scan history is uploaded anywhere.

Users can clear local history from inside the app.

---

## Privacy

This project is privacy-friendly by design.

- No backend is required
- No analytics are included
- No diagnostics are uploaded
- No cookies are created by the app
- Data stays in the user’s browser
- Scan history is stored only in `localStorage`
- Clipboard and share actions only happen when the user clicks a button

Some browser APIs may expose device or environment details, such as GPU renderer, language list, screen size, CPU thread count, and memory estimate. The app displays these values so users can understand what a website may be able to detect.

---

## How to Use

### Option 1: Open Locally

Download the file and open it directly:

```text
browser_os_detection_tool_pro.html
```

Double-click the file or drag it into a browser window.

Some APIs may be limited when opened with `file://`.

---

### Option 2: Run with a Local Server

For best results, serve it from localhost.

Using Python:

```bash
python -m http.server 8080
```

Then open:

```text
http://localhost:8080/browser_os_detection_tool_pro.html
```

---

### Option 3: Deploy to GitHub Pages

1. Create a GitHub repository.
2. Add `browser_os_detection_tool_pro.html`.
3. Rename it to `index.html` if you want it to load as the homepage.
4. Go to repository settings.
5. Enable GitHub Pages.
6. Visit the generated GitHub Pages URL.

---

## File Structure

This project is intentionally simple.

```text
browser-os-detection-tool-pro/
├── index.html
└── README.md
```

The HTML file contains:

- HTML markup
- CSS styling
- JavaScript detection logic
- UI rendering
- Export tools
- Local history system

No build tools are required.

---

## Customization

### Change the App Title

Edit the `<title>` tag:

```html
<title>Browser & OS Detection Tool Pro</title>
```

You can also update the visible title in the topbar inside the JavaScript render function.

---

### Change Theme Colors

Edit the CSS variables in `:root`:

```css
:root {
  --primary: #6d5dfc;
  --primary-2: #22c1c3;
}
```

---

### Change Local History Limit

Edit this JavaScript constant:

```js
const MAX_HISTORY = 8;
```

---

### Add a New Feature Check

Add a new item inside `getFeatureMatrix()`:

```js
["Example API", "exampleAPI" in window, "Description of what this API does."]
```

---

### Add a New Insight

Edit the `makeInsights(report)` function:

```js
if (!someCondition) {
  add("warn", "⚠️", "Insight title", "Insight explanation.");
}
```

Supported tones include:

- `ok`
- `warn`
- `bad`
- `info`

---

## Browser Compatibility

The dashboard works best in modern browsers.

Recommended:

- Chrome
- Edge
- Firefox
- Safari
- Brave
- Opera

Some APIs are browser-specific. If an API is missing, the app marks it as unsupported rather than crashing.

---

## Known Limitations

Browser detection is not perfect because user-agent strings can be frozen, reduced, spoofed, or changed by browser vendors.

Some APIs require:

- HTTPS
- localhost
- specific browser versions
- user permission
- desktop or mobile hardware support

The app uses feature detection where possible because feature detection is usually more reliable than user-agent detection.

---

## Accessibility

The interface includes:

- Semantic sections
- Button labels
- Keyboard-friendly controls
- Responsive layout
- Reduced-motion support
- Print-friendly styles
- High-contrast dark and light themes

---

## Security Notes

The project avoids unsafe inline click handlers for dynamic data.

Clipboard operations are handled through JavaScript event listeners. If the modern Clipboard API is unavailable, the app falls back to a temporary textarea copy method.

Dynamic values are escaped before rendering to reduce injection risk.

---

## Development

No dependencies are required.

You can edit the file directly in any code editor.

Recommended workflow:

1. Open the HTML file in a browser.
2. Make edits.
3. Refresh the browser.
4. Test in multiple browsers.
5. Deploy the single HTML file.

---

## Suggested Future Ideas

Possible future upgrades:

- Add a downloadable PDF report
- Add a compact embed widget mode
- Add benchmark tests for canvas and JavaScript performance
- Add PWA install support
- Add browser comparison mode
- Add QR code export for sharing diagnostics
- Add configurable privacy mode that hides sensitive fields
- Add Lighthouse-style grading sections
- Add accessibility feature checks
- Add extension detection where safe and ethical

---

## License

You can use, modify, and share this project freely.

Suggested license:

```text
MIT License
```

---

## Credits

Created as a standalone browser diagnostics and environment detection dashboard using HTML, CSS, and vanilla JavaScript.
