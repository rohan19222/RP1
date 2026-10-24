# Simulated Corporate Network Reconnaissance

A beginner-to-intermediate ethical hacking portfolio project focused on passive intelligence gathering, host discovery, service enumeration, and professional reporting in an **authorized, isolated lab**.

> **Safety and authorization:** Use only the fictional target and lab subnet assigned to you. Do not scan public IP addresses, real organizations, or systems without explicit written authorization. Keep all testing inside your isolated VirtualBox/VMware lab.

## Project goals

- Distinguish passive reconnaissance from active scanning.
- Collect and document DNS and domain intelligence for an approved lab target.
- Discover hosts and services inside an assigned lab subnet.
- Correlate evidence into a concise attack-surface summary.
- Produce reproducible notes and a professional final report.

## Suggested lab setup

- Kali Linux attacker VM
- One or more intentionally configured target VMs
- Host-only or otherwise isolated virtual network
- A fictional lab domain such as `internship-corp.local`
- A lab subnet explicitly assigned to you, for example `192.168.56.0/24` (verify your own lab configuration before use)

Do not use the example subnet unless it is actually your isolated lab subnet.

## Tools

- Passive/DNS research: `whois`, `dig`, `dnsrecon`, theHarvester
- Host and service discovery: `Nmap`, `Netdiscover`
- Optional SMB enumeration: `enum4linux` against an authorized lab Windows target only
- Documentation: Markdown, spreadsheet software, screenshots, and PDF export

External search services such as Shodan/Censys should be used only for permitted search-based research; do not treat them as permission to probe discovered systems.

## Repository structure

```text
.
├── docs/
│   └── original-project-brief.pdf
├── reports/
│   └── templates/
│       └── reconnaissance-report-template.md
├── evidence/
│   ├── passive-osint/
│   ├── nmap/
│   └── screenshots/
├── data/
├── scripts/
├── .gitignore
├── LICENSE
└── README.md
```

## Workflow

1. **Confirm scope:** Record the approved target domain, subnet, testing window, and written authorization.
2. **Passive reconnaissance:** Gather permitted DNS/domain information and save source notes in `evidence/passive-osint/`.
3. **Host discovery:** Discover live hosts only within the approved isolated subnet.
4. **Service enumeration:** Run scoped scans against approved lab hosts; save raw output in `evidence/nmap/`.
5. **Analyze:** Identify exposed services, versions, and items that require validation. A version banner alone does not prove a vulnerability.
6. **Report:** Complete the report template, attach relevant evidence, and provide prioritized recommendations.

## Example commands (replace placeholders only with your approved lab values)

DNS lookups:
```bash
dig <authorized-lab-domain> A
dig <authorized-lab-domain> MX
dig <authorized-lab-domain> NS
```

Host discovery:
```bash
nmap -sn <approved-lab-subnet>
```

Service/version scan of one authorized lab host:
```bash
nmap -sV -oA evidence/nmap/host-scan <approved-lab-host>
```

Use `-p-`, OS detection, or NSE scripts only when they are within the scope and rules of your lab. Do not copy commands blindly; confirm the target and subnet first.

## Evidence and reporting

- Save command output, timestamps, and the exact scope used.
- Redact credentials, personal information, tokens, and any sensitive data before committing.
- Never commit private keys, passwords, VPN profiles, `.env` files, or unredacted client data.
- Keep the final report factual: separate observed evidence from hypotheses and recommendations.

Start with `reports/templates/reconnaissance-report-template.md`.

## Project status

This repository is a documentation and evidence scaffold. Add your own lab results and completed report; do not invent scan results or findings.
