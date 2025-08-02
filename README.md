# Cross-Command-App

A simple cross-platform HTTP service in Go that executes basic system commands and returns the results as JSON.

## ✨ Features

- 🌐 **Ping** any host and get success & latency.
- 💻 **Get system info**: hostname and IP address.
- 🧩 Built with Go’s standard HTTP server.
- 🪟 Supports Windows, macOS (Linux compatible).
- 📦 Basic macOS `.pkg` installer script included.

---

## 📁 Project Structure

```
cross-command-app/
├── cmd/              # Entry point (main.go)
├── commander/        # Ping and system info logic
├── server/           # HTTP handler
├── test/             # Test cases
├── installer/        # macOS installer script
└── README.md
```
---

## ⚙️ Build & Run

> 🪟 On **Windows**:

```bash
go build -o app.exe .\cmd\main.go
.\app.exe
```

> 🍎 On **macOS/Linux**:

```bash
go build -o app ./cmd/main.go
./app
```
App runs on `http://localhost:8080`

---

## 🔌 API Documentation

### 🔹 `POST /execute`

#### Command: `sysinfo`

```json
{
  "type": "sysinfo"
}
```

#### Command: `ping`

```json
{
  "type": "ping",
  "payload": "google.com"
}
```
### Response Format

- `ping` returns:
  ```json
  {
    "success": true,
    "data": {
        "successful": true,
        "time": 110195200
    }
  }
  ```
- `sysinfo` returns:
  ```json
  {
    "success": true,
    "data": {
        "successful": true,
        "time": 84116700
    }
  }
  ```
## 🧪 Testing

Run unit tests:

```bash
go test ./test
```

Example test output:

```
PASS: TestGetSystemInfo
```

---
## 🔬 Postman Example

1. Open Postman
2. Create a new `POST` request to:

```
http://localhost:8080/execute
```

3. In the body, choose:
   - `raw`
   - `JSON`

Example body:

```json
{
  "type": "ping",
  "payload": "google.com"
}
```

---

## 📦 macOS Installer (optional)

To generate a `.pkg` installer (macOS only):

```bash
chmod +x ./installer/macos_installer.sh
./installer/macos_installer.sh
```

Installs binary to `/usr/local/bin`.

---
## 🎬 Demo Video

A short walkthrough Video:  

https://github.com/user-attachments/assets/ec399915-ed8b-42cb-a15d-a137c6616c1d

---

## 📌 Notes

- Windows uses `-n` for ping; macOS/Linux uses `-c`.
- Requires outbound network access for ping.
- IPv6 is not supported in this version.

---





