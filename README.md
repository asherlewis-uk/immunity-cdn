# Immunity CDN

Static threat-intelligence files served via GitHub raw content delivery.

These files are consumed by the **Pulse Check Engine** (`src/lib/pulse.ts`) in the Immunity app. The app fetches them daily to append new certificates and blocklist domains into the local Dexie.js database (append-only, never overwrite).

## Files

| File | Schema | Purpose |
|---|---|---|
| `status.json` | `BulletinStatus` | Security bulletin displayed on the dashboard |
| `certs.json` | `CdnCertificate[]` | Trusted vendor SHA-256 certificate fingerprints |
| `blocklist.json` | `CdnBlocklistEntry[]` | Stalkerware C2 domains for DNS sinkhole |

## Deployment

1. Push this `cdn/` directory to a new GitHub repo: `asherlewis-uk/immunity-cdn`
2. Files are served at: `https://raw.githubusercontent.com/asherlewis-uk/immunity-cdn/main/<file>`
3. The Immunity app's `CDN_BASE_URL` points to this base path.

## Schema Contracts

### `status.json`
```json
{
  "minVersion": "0.1.0",
  "criticalUpdate": false,
  "bulletinTitle": "...",
  "bulletinMessage": "...",
  "severity": "info | warning | critical"
}
```

### `certs.json`
```json
[
  { "packageName": "com.example.app", "signature": "SHA256_HEX" }
]
```

### `blocklist.json`
```json
[
  { "domain": "malicious-domain.com" }
]
```
