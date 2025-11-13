# External-Network-Enumeration
Enumerate external company domains, subdomains, webpages and open ports.

# Workflow
subfinder + chaos
        ↓
       dnsx
      ↙    ↘
 katana     naabu
   ↓         ↓
  httpx ----→ nuclei
   ↓
 katana (deep)
   ↓
 nuclei (final)

| Tool              | Input         | Output          | Main Job                         |
| ----------------- | ------------- | --------------- | -------------------------------- |
| subfinder / chaos | domain        | hostnames       | Find subdomains                  |
| dnsx              | hostnames     | IPs (hosts.txt) | Resolve DNS                      |
| katana (early)    | hosts/domains | URLs            | Find paths pre-httpx             |
| httpx             | URLs/hosts    | live URLs       | Verify & fingerprint web servers |
| naabu             | hosts         | open ports      | Port scan non-HTTP               |
| katana (late)     | live URLs     | deeper URLs     | Find hidden routes               |
| nuclei            | all URLs      | vulnerabilities | Scan for vulns                   |


