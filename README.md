# Central Blocklist Repository

A centralized repository for managing domain blocklists that can be used with DNS filtering tools like Technitium DNS Server, Pi-hole, and other DNS-based ad blockers.

## 🚀 Quick Start

Use this raw link directly in your DNS filtering tool:
```
https://raw.githubusercontent.com/ohnonick2/blocklist/main/merged/all.txt
```

## 📁 Repository Structure

```
blocklists/
├── ads.txt         # Ad-serving domains
├── tracking.txt    # Analytics and tracking domains
└── custom.txt      # Custom blocked domains

merged/
└── all.txt         # Auto-generated merged blocklist (use this!)
```

## 🔄 How It Works

1. **Source Lists**: Individual blocklists are maintained in the `blocklists/` directory
2. **Automatic Merging**: GitHub Actions automatically merges all `.txt` files when changes are pushed
3. **Deduplication**: Duplicate entries are removed and domains are sorted alphabetically
4. **Raw Access**: The merged list is available via GitHub's raw content URL

## 📋 Usage Instructions

### For Technitium DNS Server
1. Go to Settings > Block Lists
2. Add this URL: `https://raw.githubusercontent.com/ohnonick2/blocklist/main/merged/all.txt`
3. Click "Update" to download and apply the blocklist

### For Pi-hole
1. Go to Group Management > Adlists
2. Add the raw URL in the "Address" field
3. Click "Add" and update gravity

### For Other DNS Tools
Most DNS filtering tools accept blocklist URLs. Use the raw GitHub URL provided above.

## ✏️ Adding New Domains

### Method 1: Edit Files Directly
1. Navigate to the appropriate file in `blocklists/`:
   - `ads.txt` - for advertising domains
   - `tracking.txt` - for analytics/tracking domains  
   - `custom.txt` - for other blocked domains
2. Add one domain per line (without protocols or paths)
3. Commit your changes

### Method 2: Create Pull Request
1. Fork this repository
2. Edit the appropriate blocklist file
3. Submit a pull request with your changes

### Domain Format
- Use bare domains: `example.com` (not `https://example.com`)
- One domain per line
- Comments start with `#`
- Subdomains are supported: `ads.example.com`

## 🤖 Automation

The repository uses GitHub Actions to automatically:
- Merge all blocklist files when changes are pushed to main
- Remove duplicate entries
- Sort domains alphabetically
- Update the merged blocklist at `merged/all.txt`

## 📊 Current Statistics

The merged blocklist currently contains **18** unique domains across all categories.

## 🛠️ Maintenance

The blocklist is automatically updated whenever:
- New domains are added to any source list
- Existing domains are modified or removed
- Pull requests are merged

No manual intervention is required for the merging process.

## 📝 License

This project is public domain. Feel free to use, modify, and distribute as needed.