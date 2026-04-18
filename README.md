# Bun-FCA (bun-fca)

[![Bun Version](https://img.shields.io/badge/Bun-%3E%3D1.0.0-blue?logo=bun)](https://bun.sh)
[![GitHub](https://img.shields.io/github/license/GrandpaAcademy/bun-fca)](https://github.com/GrandpaAcademy/bun-fca)

> **High-Performance Unofficial Facebook Chat API for Bun**
> 
> A complete, low-latency port of the ST-FCA library optimized specifically for the Bun runtime.

## ⚡ Why Bun-FCA?

This is a **native Bun port** that replaces the legacy Node.js networking stack with Bun's high-performance internals.

- 🚀 **Native Fetch**: Completely replaced the deprecated `request` library with Bun's native `fetch` for ultra-low latency.
- 🍪 **BunCookieJar**: Custom synchronous cookie management built for Bun, ensuring perfect session persistence without recursion overhead.
- 📦 **Zero-Config Bun Support**: No need for `node-fetch`, `bluebird` shims, or polyfills. Just `bun add` and run.
- 🛠️ **MQTT & WebSocket**: Fully compatible with Bun's native WebSocket and optimized `mqtt` client.

## 📦 Installation

```bash
bun add https://github.com/GrandpaAcademy/bun-fca.git
```

## 🚀 Basic Usage

```javascript
const login = require("bun-fca");

// use your appstate.json
const appState = JSON.parse(require("fs").readFileSync("appstate.json", "utf8"));

login({ appState }, (err, api) => {
    if (err) return console.error(err);

    console.log("Logged in as:", api.getCurrentUserID());

    api.listenMqtt((err, event) => {
        if (err) return console.error(err);

        // Echo back the received message
        api.sendMessage(event.body, event.threadID);
    });
});
```

## 📝 Key Optimizations

| Feature                | Optimization                                                                 |
| ---------------------- | ---------------------------------------------------------------------------- |
| **Networking**         | Uses Bun's `fetch` (C++ implementation) instead of JS-based `request`.       |
| **Form Handling**      | Uses Bun's native `FormData` for multipart and file uploads.                 |
| **Startup**            | Significantly faster module resolution and startup time under the Bun runtime. |
| **Memory**             | Reduced memory footprint by eliminating heavy Node.js legacy dependencies.   |

## 💾 Saving AppState

```javascript
const fs = require("fs");
const login = require("bun-fca");

login({ appState: [] }, (err, api) => {
    if (err) return console.error(err);

    const appState = JSON.stringify(api.getAppState(), null, 2);
    fs.writeFileSync("appstate.json", appState);
    console.log("✅ AppState saved successfully!");
});
```

## 🤝 Contributing

Contributions are welcome! Please:

1. Fork the repository
2. Create a new branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 License

MIT License - See [LICENSE](./LICENSE) for details.

## 👨‍💻 Author

**Grandpa Academy**
GitHub: [https://github.com/GrandpaAcademy](https://github.com/GrandpaAcademy)

---

**Disclaimer:** This is an unofficial API and is not officially supported by Facebook. Use responsibly and comply with [Facebook Terms of Service](https://www.facebook.com/terms.php).