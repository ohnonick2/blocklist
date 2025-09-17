# Central Blocklist Repository

A centralized DNS blocklist repository that automatically merges multiple blocklist categories into a single file optimized for DNS-based ad and tracking blockers like Technitium DNS Server.

## 🎯 Purpose

This repository serves as a central source for DNS blocklists, automatically combining multiple categories of unwanted domains into a single, easy-to-use blocklist file. The merged list is perfect for DNS servers, Pi-hole, AdGuard Home, Technitium DNS Server, and other DNS-based blocking solutions.

## 📁 Repository Structure

```
blocklists/
├── ads.txt         # Advertisement domains
├── tracking.txt    # Analytics and tracking domains
└── custom.txt      # Custom blocked domains

merged/
└── all.txt         # Auto-generated merged blocklist

.github/workflows/
└── merge-blocklists.yml  # GitHub Action for auto-merging
```

### Blocklist Categories

| File | Purpose | Examples |
|------|---------|----------|
| `ads.txt` | Advertisement networks and banner ads | doubleclick.net, googlesyndication.com |
| `tracking.txt` | Analytics, tracking, and fingerprinting | google-analytics.com, facebook.com |
| `custom.txt` | Custom domains (malware, unwanted sites) | Add your own domains here |

## 🚀 Usage

### For Technitium DNS Server

Use this raw GitHub URL directly in Technitium DNS Server:

```
https://raw.githubusercontent.com/ohnonick2/blocklist/main/merged/all.txt
```

### For Other DNS Blockers

The same URL works with:
- **Pi-hole**: Add as an adlist in the admin panel
- **AdGuard Home**: Add as a DNS blocklist
- **pfBlockerNG**: Add as a DNSBL feed
- **NextDNS**: Add as a custom blocklist
- **Any DNS blocker**: Supporting standard domain-per-line format

### Manual Download

```bash
# Download the latest merged blocklist
curl -o blocklist.txt https://raw.githubusercontent.com/ohnonick2/blocklist/main/merged/all.txt

# Or with wget
wget https://raw.githubusercontent.com/ohnonick2/blocklist/main/merged/all.txt
```

## 🔧 How It Works

1. **Individual Lists**: Domains are organized in separate files by category in the `blocklists/` directory
2. **GitHub Action**: Automatically triggered on:
   - Push to main/master branch (when blocklist files change)
   - Daily schedule (02:00 UTC)
   - Manual dispatch
3. **Merging Process**: 
   - Combines all blocklist files
   - Removes duplicates
   - Adds headers and metadata
   - Generates statistics
4. **Output**: Creates `merged/all.txt` with all domains in a single file

## 📝 File Format

The merged blocklist follows standard DNS blocklist format:
- One domain per line
- Comments start with `#`
- No protocol prefixes (no `http://` or `https://`)
- Domains are sorted and deduplicated

Example:
```
# Merged Blocklist
# Last updated: 2024-01-15 02:00 UTC

# === Advertisement Domains ===
doubleclick.net
googleadservices.com

# === Tracking and Analytics Domains ===
google-analytics.com
facebook.com
```

## 🤝 Contributing

### Adding Domains

1. **Fork** this repository
2. **Edit** the appropriate blocklist file:
   - `blocklists/ads.txt` for advertisement domains
   - `blocklists/tracking.txt` for tracking/analytics domains  
   - `blocklists/custom.txt` for other unwanted domains
3. **Add domains** one per line (no protocol prefix)
4. **Submit** a pull request

### Guidelines

- Only add domains you're confident should be blocked
- Include comments explaining why a domain should be blocked
- Test domains before adding to ensure they don't break legitimate services
- Keep domains relevant to their category

### Example Addition

```diff
# Custom Blocklist
+ # Known malware distribution
+ malicious-site.example
+ phishing-domain.com
```

## 🔄 Automatic Updates

The merged blocklist is automatically updated:
- **When changes are made** to any blocklist file
- **Daily at 02:00 UTC** to ensure freshness
- **On manual trigger** via GitHub Actions

This ensures downstream DNS blockers always have the latest protection.

## 📊 Statistics

Current blocklist stats (updated automatically):
- View the latest statistics in the merged file header
- Check the [GitHub Actions](../../actions) page for update history

## ⚠️ Disclaimer

This blocklist is provided as-is for educational and security purposes. Users should:
- Test the blocklist in their environment before deploying
- Monitor for false positives that might block legitimate services
- Adjust or customize as needed for their specific use case

## 📄 License

This project is open source. Feel free to use, modify, and distribute the blocklists according to your needs.

## 🔗 Quick Links

- **Raw Blocklist URL**: https://raw.githubusercontent.com/ohnonick2/blocklist/main/merged/all.txt
- **Repository**: https://github.com/ohnonick2/blocklist
- **Issues**: Report problems or suggest domains [here](../../issues)
- **Pull Requests**: Contribute improvements [here](../../pulls)