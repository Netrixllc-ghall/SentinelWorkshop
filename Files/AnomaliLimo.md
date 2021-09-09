# Connect Anomali Limo to Azure Sentinel TAXII2 Connector

- Open https://portal.azure.com and find the Sentinel workspace
- Click on Connectors
- in the search bar type threat
- Click on the one named Threat Intelligence - TAXII (Preview)
- In the right blade click on Open Connector page

| Collection | IDs |
|------------|-----|
|Phish Tank | 107 |
|Abuse.ch Ransomware IPs | 135 |
|Abuse.ch Ransomware Domains | 136 |
|DShield Scanning IPs | 150 |
|Malware Domain List - Hotlist | 200 |
|Blutmagie TOR Nodes | 209 |
|Emerging Threats C&C Servers | 31 |
|DT Covid 19 | 313 |
|Lehigh MalwareDomains | 33 |
|CyberCrime | 41 |
|Emerging Threats - Compromised | 68 |

Run the following command to get the current collections being offered.
```Ps
curl.exe -u guest:guest https://limo.anomali.com/api/v1/taxii2/feeds/collections/ | Out-File .\AnomaliCollections.json
```