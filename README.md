# EasySigner

**EasySigner** is a free application for signing PDF documents with a qualified electronic signature (QES) — in just a few clicks:

1. Open a PDF document
2. Select the signature location with your mouse
3. Choose your certificate and enter the PIN
4. Sign

No complicated workflows, no unnecessary configuration, no platform-specific editions.

## Why EasySigner?

✅ **Free to use** — no feature limits, no subscriptions

✅ **One application for both Windows and macOS** — same look, same behavior

✅ **Modern and simple user interface**

✅ **Hardware tokens and smart cards (PKCS#11)** — the Czech national ID card (eObčanka) works out of the box, and any other PKCS#11-compatible token can be used by selecting its vendor's driver library in Settings

✅ **Certificate files (.pfx / .p12)**

✅ **Visible signature appearance** — custom text and an optional image of your handwritten signature

✅ **PAdES-compliant signatures** — profiles B-B, B-T, B-LT and archival B-LTA

✅ **Timestamping (RFC 3161)** — optional TSA integration for long-term validation

✅ **Three languages** — English, Czech, Ukrainian

🔒 **Local signing.** Your documents never leave your computer. Private keys never leave your token or certificate container. The PIN is never written to disk. The only network communication is the optional request to your timestamp (TSA) server.

---

## Download

Get the latest release from the [Releases page](https://github.com/mkozarik-praha/EasySigner/releases).

| Platform | File | Notes |
|---|---|---|
| Windows 10 or later (x64) | `EasySigner-win64-*.zip` | Portable — unzip and run `EasySigner.exe` |
| macOS 12 Monterey or later (Apple Silicon) | `EasySigner-osx-arm64.app.zip` | M1 or newer; an Intel (x64) build is in preparation |

Each release lists SHA-256 checksums. To verify your download on macOS or Linux:

```
shasum -a 256 EasySigner-osx-arm64.app.zip
```

---

## Installation

### Windows

1. Unzip the archive to any folder
2. Run `EasySigner.exe`
3. Windows SmartScreen may warn about an unrecognized app on first launch — choose **More info → Run anyway**

If you sign with eObčanka, the PKCS#11 driver path is pre-configured automatically (`C:\Windows\System32\eopproxyp11.dll`, installed with the official eObčanka software).

### macOS

1. Unzip the archive and move **EasySigner.app** to **/Applications** (do not run it from Downloads)
2. First launch: **right-click → Open** and confirm. On newer macOS versions, if that doesn't work: try to launch once, then go to **System Settings → Privacy & Security → Open Anyway**
3. Still blocked with a "damaged" message? Run in Terminal:
   ```
   xattr -cr "/Applications/EasySigner.app"
   ```
4. If none of the above helps, follow the full step-by-step guide (see below) — it includes a local ad-hoc signing procedure that resolves the remaining cases

The app is not yet notarized by Apple — these warnings are expected. Notarization is planned (see Roadmap).

For signing with eObčanka you also need the official **eObčanka – Správce karty** application installed; the PKCS#11 library path is then pre-configured automatically (`/usr/local/lib/eOPCZE/libeopproxyp11.dylib`).

📄 **Full step-by-step macOS guide (in Czech), including troubleshooting:** see `First_start_on_MacOS.pdf` attached to the release.

---

## Screenshots

<!-- Replace with real screenshots. Recommended: main window + signature placement. -->
*Coming soon.*

---

## How it works

- Certificates are read from your token via the standard **PKCS#11** interface (any vendor's token works — select its driver library in Settings), or from a **PKCS#12** file (`.pfx`/`.p12`)
- The signature is embedded as a **PAdES** (CAdES-in-PDF) signature; for B-LT/B-LTA profiles the app also embeds revocation evidence (OCSP/CRL) and a document timestamp, so signatures remain verifiable years later
- The signed file is saved next to the original with the `_signed` suffix

---

## Roadmap

- macOS build for Intel Macs (x64)
- Apple notarization and Windows code signing (removes the first-launch warnings)
- Signature validation — verify who signed a document and whether it was modified
- macOS Keychain integration for storing the TSA password
- Your suggestions — please [open an issue](https://github.com/mkozarik-praha/EasySigner/issues)!

---

## Source code

The source is currently not published because the application uses commercial third-party libraries. If there is community interest, the code can be published without the license keys (it would compile, but not be fully functional). The application itself is and will remain free.

---

## License

EasySigner is **freeware** — free of charge for personal and commercial use. All rights reserved.

---

## Support the Project

EasySigner is developed in spare time and distributed free of charge. If you find it useful, consider supporting its development:

☕ https://buymeacoffee.com/mkozarik

---

## Author

**Miroslav Kozárik**

Made with ❤️ for simple and secure electronic document signing.
