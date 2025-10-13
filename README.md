# 🛡️ SecuScan — Security & Compliance Scanner

![Python](https://img.shields.io/badge/Python-3.10+-blue.svg?logo=python&logoColor=white)
![Security](https://img.shields.io/badge/Security-Scanner-FF5252?logo=shield)
![Compliance](https://img.shields.io/badge/Compliance-Licenses-4CAF50?logo=open-source-initiative)
![Reports](https://img.shields.io/badge/Reports-JSON-2196F3?logo=json)
![CI/CD](https://img.shields.io/badge/CI/CD-Ready-2088FF?logo=githubactions)
![Dependencies](https://img.shields.io/badge/Dependencies-None-green?logo=python)

**SecuScan** is a **Python 3** tool that scans codebases and dependency files for **hardcoded secrets**, **vulnerable packages**, and **license violations** — all with **zero external dependencies**.

It’s built for **DevSecOps** teams who want a fast, lightweight, and CI/CD-friendly security scanner for Python projects.

---

## 🛠 Tech & Languages

| Layer | Tech / Format | Purpose |
|------|------|------|
| Language | **Python 3.10+** | Pure standard library |
| Scanner | **Regex / Static Rules** | Detect secrets and unsafe code |
| Dependencies | **requirements.txt** | Check vulnerable package versions |
| License | **README.md** | License validation |
| Reports | **JSON** | Machine-readable summary |
| Logging | **Python Logging** | Lightweight audit tracking |

---

## 🌐 Architecture

<p align="center">
  <img src="https://raw.githubusercontent.com/codecrafters-io/build-your-own-x/main/media/devops-architecture-diagram.png" alt="SecuScan Architecture" width="650" />
</p>

Flow:
1. Scans files for **hardcoded secrets** (API keys, passwords, tokens)  
2. Checks **requirements.txt** for vulnerable versions  
3. Validates **project license** against a whitelist  
4. Produces a **JSON security report**  
5. Exits cleanly for use in **CI/CD gates**

---


---

## ▶️ Run the Scanner

Run from terminal:
```bash
python scanner/secuscan.py --path ./project --output reports/report.json

---------

🧪 Example Output
{
  "summary": {
    "files_scanned": 42,
    "secrets_found": 1,
    "vulnerabilities": 2,
    "licenses_invalid": 1
  },
  "details": {
    "secrets": [
      {"file": "config.py", "line": 14, "issue": "AWS Access Key"}
    ],
    "vulnerabilities": [
      {"package": "requests", "version": "2.19.0", "severity": "critical"}
    ],
    "licenses": ["Unknown"]
  }
}

📊 Use Cases

🔐 Enforce DevSecOps gates in pipelines

🧩 Detect AWS keys and secrets before commits

⚙️ Validate dependency versions and licenses

🧾 Generate JSON reports for dashboards

Design Philosophy

Lightweight: Pure Python standard library

Transparent: Human-readable JSON output

Portable: Works on any OS, no dependencies

Practical: CI/CD-friendly exit codes

Extensible: Add new regex patterns easily

🐳 Docker (Optional)

Build:

docker build -t secuscan:latest .


Run:

docker run --rm -v $(pwd):/src secuscan:latest \
  python scanner/secuscan.py --path /src
