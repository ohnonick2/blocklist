# DNS Blocklist Repository

This repository serves as a centralized collection of DNS blocklists for use with Technitium DNS Server or other DNS filtering solutions.

## Repository Structure

- `blocklists/`: Contains individual blocklists by category
  - `ads.txt`: Domains related to advertisements
  - `tracking.txt`: Tracking and analytics domains
  - `custom.txt`: Custom domains you want to block
- `merged/`: Contains the automatically generated merged blocklist
  - `all.txt`: Combined list of all blocklists (updated via GitHub Actions)

## Usage

To use this blocklist with Technitium DNS Server:

1. Go to DNS Server > Block List
2. Click "Add"
3. Enter a name for your blocklist (e.g., "Combined Blocklist")
4. In the URL field, paste:
   ```
   https://raw.githubusercontent.com/ohnonick2/blocklist/main/merged/all.txt
   ```
5. Set update frequency as desired
6. Click "Save"

## Updating Lists

To add domains to block:
1. Edit the appropriate category file in the `blocklists/` directory
2. Add one domain per line
3. Commit and push your changes
4. GitHub Actions will automatically merge all lists into `merged/all.txt`

## Format

The blocklist files follow a simple format with one domain per line:
```
example-ad-domain.com
tracking-domain.net
```
