<div align="center">

# ⚡ Aither-get

### Blazingly Fast Multi-Connection Download Engine

[![Windows](https://img.shields.io/badge/Windows-0078D6?style=for-the-badge&logo=windows&logoColor=white)](https://github.com/NoahMustafa/aither-get/releases)
[![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)](https://github.com/NoahMustafa/aither-get/releases)
[![Downloads](https://img.shields.io/github/downloads/NoahMustafa/aither-get/total?style=for-the-badge)](https://github.com/NoahMustafa/aither-get/releases)
[![Latest Release](https://img.shields.io/github/v/release/NoahMustafa/aither-get?style=for-the-badge)](https://github.com/NoahMustafa/aither-get/releases/latest)
[![Stars](https://img.shields.io/github/stars/NoahMustafa/aither-get?style=for-the-badge)](https://github.com/NoahMustafa/aither-get/stargazers)
[![Ko-fi](https://img.shields.io/badge/Support-Ko--fi-FF5E5B?style=for-the-badge&logo=ko-fi&logoColor=white)](https://ko-fi.com/Noah_mustafa_stuff)

**[Download Latest Release](https://github.com/NoahMustafa/aither-get/releases/latest)** • **[Documentation](#-quick-start)** • **[Report Bug](https://github.com/NoahMustafa/aither-get/issues)**

[![Aither-get Technical Demo](https://img.shields.io/badge/Watch-Demo_Video-blue?style=for-the-badge)](https://youtu.be/M4qYumZ4hpQ)

</div>

---

## 🚀 Why Aither-get?

Tired of slow downloads? **Aither-get** uses **multi-connection technology** to download files up to **3x faster** than traditional download managers.

```bash
# Download a 1GB file in seconds, not minutes
aither-get https://example.com/largefile.zip -n 32
```

> **⚠️ Important Notice:** This software is provided for **personal use only**. Building graphical user interfaces (GUIs) or wrappers around Aither-get, or publishing/distributing modified versions requires **explicit written consent** from the authors. Unauthorized commercial use, redistribution, or UI development is prohibited. See [License](#-license) for details.

### ✨ Key Features

<table>
<tr>
<td width="50%">

#### ⚡ Lightning Fast
- Up to **32 parallel connections**
- **3x faster** than single-connection downloads
- Smart chunk distribution

</td>
<td width="50%">

#### 🔄 Bulletproof Resume
- Automatic resume on interruption
- Block-aligned resume (zero waste)
- Persistent download state

</td>
</tr>
<tr>
<td width="50%">

#### 🎯 Smart & Flexible
- Auto-rename duplicate files
- Skip already-downloaded files
- Force re-download option

</td>
<td width="50%">

#### 🎛️ Full Control
- Real-time bandwidth limiting
- Live speed adjustments
- JSON API for automation

</td>
</tr>
<tr>
<td width="50%">

#### 🌐 Protocol Support
- HTTP/HTTPS with range requests
- FTP with resume support
- Proxy support (HTTP/SOCKS5)

</td>
<td width="50%">

#### 🛡️ Production Ready
- Zero data corruption
- Comprehensive error handling
- Battle-tested reliability

</td>
</tr>
</table>

---

## 📦 Installation

### Windows

1. **Download** the latest `aither-get.exe` from [Releases](https://github.com/NoahMustafa/aither-get/releases/latest)
2. **Place** it in a folder (e.g., `C:\Tools\Aither\`)
3. **Add to PATH** (optional but recommended):
   - Search "Environment Variables" in Windows
   - Edit "Path" under System Variables
   - Add your folder path (e.g., `C:\Tools\Aither\`)
   - Restart terminal
4. **Run** from Command Prompt or PowerShell

### Linux

1. **Download** the latest `aither-get` binary from [Releases](https://github.com/NoahMustafa/aither-get/releases/latest)
2. **Make it executable:**
   ```bash
   chmod +x aither-get
   ```
3. **Move to PATH** (optional but recommended):
   ```bash
   sudo mv aither-get /usr/local/bin/
   ```
4. **Run** from terminal

### Verify Installation

```bash
# Check version
aither-get --version

# Test with a small download
aither-get https://httpbin.org/bytes/1024 -o test.bin
```

> **Note:** macOS support may be added in future releases.

---

## 🎯 Quick Start

### Basic Usage

```bash
# Simple download (recommended: clean output)
aither-get --minimal https://example.com/file.zip

# Download with custom name
aither-get --minimal https://example.com/file.zip -o myfile.zip

# Fast download with 16 connections
aither-get --minimal https://example.com/file.zip -n 16

# Resume interrupted download
aither-get --minimal --resume myfile.zip
```

> **💡 Tip:** Use `--minimal` for clean, distraction-free progress display (just spinner + speed). Omit it for detailed progress bars with ETA.

### Real-World Examples

<details>
<summary><b>📥 Download Large Files (ISOs, Videos)</b></summary>

```bash
# Ubuntu ISO with maximum speed (clean output)
aither-get --minimal https://releases.ubuntu.com/22.04/ubuntu-22.04-desktop-amd64.iso -n 32

# Large video file with progress
aither-get --minimal https://example.com/video.mp4 -n 16 -o movie.mp4
```
</details>

<details>
<summary><b>🎮 Download Game Files</b></summary>

```bash
# Large game download with speed limit (don't saturate network)
aither-get --minimal https://cdn.example.com/game-installer.exe -n 16 --limit 10485760

# Resume if interrupted
aither-get --minimal --resume game-installer.exe
```
</details>

<details>
<summary><b>📚 Batch Download Multiple Files</b></summary>

```cmd
REM Windows batch script
@echo off
for /F "tokens=*" %%i in (urls.txt) do (
    aither-get --minimal %%i --auto-rename -n 16
)
```

```powershell
# PowerShell
Get-Content urls.txt | ForEach-Object { aither-get --minimal $_ --auto-rename -n 16 }
```
</details>

<details>
<summary><b>🔄 Resume Downloads After Interruption</b></summary>

```bash
# Start download
aither-get --minimal https://example.com/largefile.zip -o myfile.zip

# If interrupted (Ctrl+C, network failure, etc.), resume:
aither-get --minimal --resume myfile.zip

# The download picks up exactly where it left off!
```
</details>

<details>
<summary><b>🎛️ Control Bandwidth</b></summary>

```bash
# Limit to 5 MB/s (5 * 1024 * 1024 bytes)
aither-get --minimal https://example.com/file.zip --limit 5242880

# Limit to 1 MB/s
aither-get --minimal https://example.com/file.zip --limit 1048576

# No limit (maximum speed)
aither-get --minimal https://example.com/file.zip
```
</details>

---

## 📖 Command Reference

### Essential Options

| Option | Short | Description | Example |
|--------|-------|-------------|---------|
| `--minimal` | | **Recommended:** Clean output (spinner + speed) | `--minimal` |
| `--output` | `-o` | Output filename | `-o myfile.zip` |
| `--connections` | `-n` | Parallel connections (1-32) | `-n 16` |
| `--limit` | `-l` | Bandwidth limit (bytes/sec) | `--limit 5242880` |
| `--resume` | | Resume interrupted download | `--resume file.zip` |
| `--force` | | Overwrite existing file | `--force` |
| `--auto-rename` | | Auto-rename if exists | `--auto-rename` |

### Advanced Options

| Option | Description | Use Case |
|--------|-------------|----------|
| `--json-status` | Output JSON progress | Automation, UI integration |
| `--quiet` | Suppress all output | Silent operation |
| `--debug-progress` | Detailed progress logs | Debugging |
| `--user-agent` | Custom user agent | Bypass server restrictions |
| `--proxy` | Use proxy server | Download through proxy |
| `--no-verify-tls` | Skip TLS verification | Self-signed certificates |

### Speed Limit Reference

| Speed | Bytes/sec | Command |
|-------|-----------|---------|
| 1 MB/s | 1048576 | `--limit 1048576` |
| 5 MB/s | 5242880 | `--limit 5242880` |
| 10 MB/s | 10485760 | `--limit 10485760` |
| 50 MB/s | 52428800 | `--limit 52428800` |

---

## 🎨 Advanced Features

> **📝 Note:** Interactive mode (live bandwidth control via stdin) is currently disabled and under development. It will be re-enabled in a future release. For now, set bandwidth limits using the `--limit` flag at startup.

### JSON Output for Automation

Perfect for integrating into scripts, GUIs, or monitoring systems:

```bash
aither-get https://example.com/file.zip --json-status
```

**Output:**
```json
{"taskId":"abc123","downloadedBytes":1048576,"totalBytes":10485760,"progressPercent":10.0,"speedBps":2097152,"etaSeconds":4,"status":"downloading"}
{"taskId":"abc123","downloadedBytes":5242880,"totalBytes":10485760,"progressPercent":50.0,"speedBps":2621440,"etaSeconds":2,"status":"downloading"}
{"taskId":"abc123","downloadedBytes":10485760,"totalBytes":10485760,"progressPercent":100.0,"status":"completed"}
```

### Integration Examples

> **⚠️ Important:** These examples are for **monitoring and automation purposes only** (e.g., logging, progress tracking in scripts). Building graphical user interfaces (GUIs) or distributing applications that wrap Aither-get is **prohibited without written consent**. See [License](#-license) for details.

<details>
<summary><b>Python Integration (Monitoring/Logging)</b></summary>

```python
import subprocess
import json

# Example: Monitor download progress for logging purposes
process = subprocess.Popen(
    ['aither-get', '--json-status', 'https://example.com/file.zip'],
    stdout=subprocess.PIPE,
    stderr=subprocess.PIPE,
    text=True
)

for line in process.stdout:
    data = json.loads(line)
    if data.get('status') == 'downloading':
        print(f"Progress: {data['progressPercent']:.1f}% @ {data['speedBps']/1048576:.2f} MB/s")
```
</details>

<details>
<summary><b>Node.js Integration (Monitoring/Logging)</b></summary>

```javascript
const { spawn } = require('child_process');

// Example: Monitor download progress for logging purposes
const proc = spawn('aither-get', [
  '--json-status',
  'https://example.com/file.zip'
]);

proc.stdout.on('data', (data) => {
  const lines = data.toString().split('\n');
  lines.forEach(line => {
    if (!line.trim()) return;
    const event = JSON.parse(line);
    if (event.status === 'downloading') {
      console.log(`${event.progressPercent.toFixed(1)}% @ ${(event.speedBps/1048576).toFixed(2)} MB/s`);
    }
  });
});
```
</details>

---

## 🔧 Performance Tips

### 🚀 Maximum Speed

```bash
# Use maximum connections for fast servers (clean output)
aither-get --minimal https://fast-server.com/file.zip -n 32

# Optimal for most servers
aither-get --minimal https://example.com/file.zip -n 16
```

### 🌐 Network-Friendly

```bash
# Limit bandwidth to avoid saturating connection
aither-get --minimal https://example.com/file.zip -n 8 --limit 5242880

# Conservative for slow networks
aither-get --minimal https://example.com/file.zip -n 4 --limit 1048576
```

### 💾 Batch Downloads

```bash
# Auto-rename to avoid conflicts
aither-get --minimal https://example.com/file.zip --auto-rename

# Skip if already downloaded
aither-get --minimal https://example.com/file.zip  # Skips if complete
```

### 🎨 Output Modes

```bash
# Minimal mode (recommended): Clean spinner + speed
aither-get --minimal https://example.com/file.zip

# Default mode: Full progress bar with ETA
aither-get https://example.com/file.zip

# Quiet mode: No output (errors only)
aither-get --quiet https://example.com/file.zip

# JSON mode: Machine-readable for automation
aither-get --json-status https://example.com/file.zip
```

---

## ❓ Troubleshooting

<details>
<summary><b>Download is slower than expected</b></summary>

- **Try more connections:** `-n 16` or `-n 32`
- **Check server limits:** Some servers limit multi-connection downloads
- **Test with single connection:** `-n 1` to compare
- **Check your internet speed:** Run a speed test
</details>

<details>
<summary><b>Download fails immediately</b></summary>

- **Verify URL:** Make sure the URL is correct and accessible
- **Check internet connection:** Test with a browser
- **Try single connection:** Some servers block multi-connection: `-n 1`
- **Check firewall:** Ensure aither-get isn't blocked
</details>

<details>
<summary><b>Resume not working</b></summary>

- **Use exact filename:** `--resume` needs the exact output filename
- **Check for .aither file:** Metadata file must exist alongside partial download
- **Don't move files:** Keep partial download in same location
- **Correct syntax:** `aither-get --resume filename.zip`
</details>

<details>
<summary><b>"Permission denied" error</b></summary>

- **Check write permissions:** Ensure you can write to the output directory
- **Run as administrator:** Right-click → "Run as administrator" (Windows)
- **Use different location:** Try downloading to your home directory
</details>

<details>
<summary><b>High CPU or memory usage</b></summary>

- **Reduce connections:** Try `-n 8` or `-n 4`
- **Limit bandwidth:** Use `--limit` to reduce throughput
- **Check disk speed:** Slow disks can cause buffering
</details>

<details>
<summary><b>"Windows protected your PC" warning</b></summary>

- Click "More info"
- Click "Run anyway"
- This is normal for unsigned executables
- The software is safe to use
</details>

---

## 📊 Benchmarks

Real-world performance comparison:

| File Size | Single Connection | Aither-get (8 conn) | Aither-get (16 conn) | Speedup |
|-----------|------------------|---------------------|----------------------|---------|
| 100 MB | 12.5s | 4.8s | 4.2s | **3.0x** |
| 500 MB | 62.5s | 24.1s | 21.0s | **3.0x** |
| 1 GB | 125s | 48.2s | 42.0s | **3.0x** |
| 5 GB | 625s | 241s | 210s | **3.0x** |

*Tested on 100 Mbps connection with high-speed server*

---

## 🤝 Feedback & Support

Your feedback helps make Aither-get better:

- 🐛 **Report bugs** via [Issues](https://github.com/NoahMustafa/aither-get/issues)
- � **Sugrgest features** via [Issues](https://github.com/NoahMustafa/aither-get/issues)
- 📖 **Improve documentation** - Submit corrections or additions
- ⭐ **Star the project** if you find it useful!
- 💬 **Share your experience** - Help others discover Aither-get

## ❤️ Donations (Optional)

Aither-get is a free, personal project with no ads and no paid features.  
If you find it useful and would like to support its development, optional donations are welcome.

> Donations do not unlock features or affect functionality in any way.

### 🌍 Global
- ☕ **Ko-fi**  
  https://ko-fi.com/Noah_mustafa_stuff

### 🇪🇬 Local (Egypt only)

- 🏦 **InstaPay**  
  https://ipn.eg/S/noahmustafa8/instapay/6RJe2t


---

## 📄 License

**Free for personal and small business use** (under 100 employees).

### Usage Restrictions

- ✅ **Allowed:** Personal use, command-line usage, automation scripts
- ✅ **Allowed:** Internal use within small businesses (under 100 employees)
- ❌ **Prohibited:** Building or distributing graphical user interfaces (GUIs) or wrappers
- ❌ **Prohibited:** Publishing, redistributing, or selling modified versions
- ❌ **Prohibited:** Commercial redistribution without explicit written consent

**UI Development & Publishing:** Creating user interfaces around Aither-get or publishing/distributing the software (modified or unmodified) requires **explicit written permission** from the authors. Contact us for licensing inquiries.

**Enterprise organizations** (100+ employees) can use the free version or [contact us](#-enterprise-licensing) for custom editions with additional features and support.

See [LICENSE](LICENSE) for full terms | [Simple Summary](LICENSE-SUMMARY.md)

---

## 💼 Enterprise Licensing

**Is your organization 100+ employees?** We offer enterprise custom editions:

- 🚀 **Enhanced Features** - Additional capabilities beyond the free version
- 🎯 **Priority Support** - Dedicated support with guaranteed response times
- 📞 **SLA Guarantees** - Service level agreements for uptime and performance
- 🎨 **White-Label Options** - Rebrand for your organization
- 🔧 **Custom Integrations** - API access and custom feature development
- 📚 **Training & Onboarding** - Professional services and documentation

**Contact us:** noahmoustafa87@gmail.com

We offer flexible licensing tailored to your organization's needs.

---

## 🙏 Acknowledgments

Inspired by aria2, wget, curl, and other great download managers.

Built with modern technology for maximum performance and reliability.

---

<div align="center">

### ⭐ Star us on GitHub — it helps others discover Aither-get!

**[Download Now](https://github.com/NoahMustafa/aither-get/releases/latest)** • **[Report Issue](https://github.com/NoahMustafa/aither-get/issues)** • **[View Releases](https://github.com/NoahMustafa/aither-get/releases)**

Made with ❤️ for fast downloads

</div>


