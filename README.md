# Domain-IP-Intelligence-CLI

A powerful command-line tool for domain and IP intelligence gathering, providing comprehensive information about domains and IP addresses through various lookup and scanning capabilities.

---

## ✨ Features

- WHOIS Lookup: Get domain registration details, creation date, expiration date, and registrar information
- DNS Records: Retrieve A, MX, NS, and TXT records for domains
- IP Information: Get geolocation, ASN, ISP, and organization details for IP addresses
- Abuse Detection: Check IP reputation using AbuseIPDB
- VPN/Proxy Detection: Identify VPN/proxy usage and anonymity level
- Subdomain Discovery: Find subdomains using public certificate logs (crt.sh)
- Bulk Domain Scanning: Process multiple domains from a text file
- CSV Reporting: Generate detailed reports with domain age calculations
- Failed Lookup Logging: Track failed lookups for troubleshooting
- Open Source & Free APIs: No paid services required

---

## 📁 Project Structure

```

domain-intel-cli/
├── domain_toolkit.py            # Main CLI controller
├── modules/
│   ├── whois_lookup.py          # WHOIS lookup with domain age
│   ├── dns_lookup.py            # DNS record fetcher
│   ├── ip_info.py               # IP geolocation and ASN
│   ├── risk_check.py            # AbuseIPDB risk analysis
│   ├── subdomain_enum.py        # Subdomain discovery
│   ├── bulk_whois.py            # Bulk domain scanning
│   └── export_csv.py            # CSV export functionality
├── data/                        # Output directory
│   └── output_*.csv            # CSV reports
│   └── failed_*.txt            # Failed lookups log
├── inputs/                      # Input directory
│   └── domains.txt             # List of domains to scan
└── requirements.txt            # Project dependencies

```

---

## 📂 Example Output Summary

```bash
✅ Bulk WHOIS Scan Complete!
--------------------------------------------------
📦 Total Domains Scanned    : 56
✅ Successful Lookups        : 52
❌ Failed Lookups            : 4

📁 CSV Report Saved To       : data/output_20250624_125057.csv
⚠️  Failed Domains Logged To : data/failed_20250624_125057.txt
🕒 Scan Timestamp            : 2025-06-24 12:50:57
```

---

## 🧾 Sample CSV Output (Columns)

| domain     | created    | expires    | domain_age                | registrar         | name_servers          | abuse_score | is_vpn_or_proxy | subdomains        |
| ---------- | ---------- | ---------- | -------------------------- | ----------------- | ---------------------- | ------------ | ------------------ | ----------------- |
| google.com | 1997-09-15 | 2028-09-14 | 31 years, 5 months, 7 days | MarkMonitor, Inc. | ns1.google.com, ns2... | 0            | False              | mail, drive, etc. |
| github.com | 2007-10-09 | 2026-10-09 | 19 years, 2 months, 5 days | MarkMonitor, Inc. | dns1.p08.nsone.net...  | 3            | True               | api, gist, docs   |

---

## 🛠 Setup & Usage

### 1️⃣ Install dependencies

```bash
pip install -r requirements.txt
```

### 2️⃣ Create `.env` file for API keys

```
ABUSEIPDB_API_KEY=your_api_key_here
```

### 3️⃣ Add domains to `inputs/domains.txt`

```txt
google.com
github.com
invalid.com
```

### 4️⃣ Run the CLI Tool

```bash
python domain_toolkit.py [command] [arguments]
```

---

## 📋 Available Commands

### WHOIS Lookup

```bash
python domain_toolkit.py whois [domain]
```

Example:
```bash
python domain_toolkit.py whois google.com
```

### DNS Lookup

```bash
python domain_toolkit.py dns [domain]
```

Example:
```bash
python domain_toolkit.py dns google.com
```

### IP Information

```bash
python domain_toolkit.py ipinfo [ip_address]
```

Example:
```bash
python domain_toolkit.py ipinfo 8.8.8.8
```

### Subdomain Enumeration

```bash
python domain_toolkit.py subdomains [domain]
```

Example:
```bash
python domain_toolkit.py subdomains google.com
```

### Bulk WHOIS Scan

```bash
python domain_toolkit.py bulk [file_path] [--export]
```

Example:
```bash
python domain_toolkit.py bulk inputs/domains.txt --export
```

---

## 🔐 API Keys

For full functionality, obtain an API key from AbuseIPDB:

1. Sign up at https://www.abuseipdb.com/
2. Create an API key in your account settings
3. Add it to your `.env` file

---

## 📝 Output Format

The tool generates two types of output:

1. CSV Report (data/output_*.csv):
   - Contains comprehensive domain information
   - Includes domain age calculation
   - Shows registrar, creation date, and expiration date
   - Lists name servers and DNS records
   - Shows abuse score and VPN/proxy status
   - Lists discovered subdomains

2. Failed Lookups Log (data/failed_*.txt):
   - Lists domains that failed to lookup
   - Helps track and troubleshoot issues

---

## 📝 License

Free for personal, academic, and commercial use — credit appreciated!

---

## 🌟 Future Roadmap

* [ ] Flask/Django REST API version
* [ ] Web UI in Next.js
* [ ] Historical WHOIS record lookup
* [ ] PDF/HTML export for reports
* [ ] Dashboard visualizer for reports

---

## 🙌 Contributing

Pull requests are welcome!

```bash
# GitHub Setup
git init
git remote add origin https://github.com/vaishnav4281/Domain-IP-Intelligence-CLI-Toolkit.git
git add .
git commit -m "Initial commit"
git push -u origin master
```
