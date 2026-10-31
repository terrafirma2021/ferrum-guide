# Ferrum 2.0.5 — driver reference

[Website](https://terrafirma2021.github.io/ferrum-guide/) · [Protocol reference](https://terrafirma2021.github.io/ferrum-guide/reference.html) · [Test installer](downloads/ferrum-2.0.5.msi)

Independent documentation of the Ferrum 2.0.5 host protocol: CP2102N / MCU integration, discovery, status, acknowledgements and command formats.

## Findings

- USB filter target: `USB\VID_10C4&PID_EA60`.
- Recorded hardware: CP2102N. USB OUT transfers were observed; no MCU was connected during that test.
- Six discovery cases and eight role/status cases passed recorded offline emulation with mocked transport and Windows services. Forty serializer examples matched isolated original-code execution.
- A generic cable matching VID/PID has **not** been shown to replace the complete Ferrum board. The adapter supplies transport; an MCU must implement the protocol and downstream behavior. A complete custom-board test remains outstanding.
- The examined app HTTP paths handle updates. Online board authentication was not identified in those paths; full offline operation is unverified.

The reference contains 44 KM serial names, eight related names, 24 DHZ names, 16 KMNet IDs, 35 wire serializer forms and 52 receive-table entries. Unknown semantics remain marked.

## Test files

`downloads/ferrum-2.0.5.msi` is the original Ferrum software package containing its app and drivers. Its SHA-256 matches both the archived installer and a fresh download from [Ferrum's update server](https://update.xferrum.dev/versions/2.0.5.msi), checked on 31 October 2026.

SHA-256: `bb233b4bc0d7a404ac3803bf386fa22156343068bd8162418634d06f8935fd10`

Verify in PowerShell:

```powershell
Get-FileHash .\downloads\ferrum-2.0.5.msi -Algorithm SHA256
```

Install on a Windows x64 test machine, connect a compatible CP2102N adapter, and check driver attachment. For board-level tests, connect an MCU implementing the documented discovery, status and action messages. Installation changes system drivers and services. No replacement MCU firmware is supplied.

Vendor software and logo remain the property of their respective owners. This is an independent reference, not an official Ferrum project. No raw captures, private logs, decompiled source, project databases or research archive are included.

## Website files

- `index.html`, `style.css`, `logo.png`: website and supplied logo.
- `reference.html`, `reference.txt`: full protocol reference.
- `online-checks.txt`: scoped app network review.
- `downloads/`: original installer and checksum.
- `.nojekyll`: direct GitHub Pages serving.

No build dependencies, analytics or external assets. To preview locally:

```sh
python -m http.server 8765 --bind 127.0.0.1
```

GitHub Pages serves the root of `main`.
