# What is User and Entity Behavior Analytics (UEBA)?
Identifying threats inside your organization and their potential impact 
whether a compromised entity or a malicious insider - has always been a time-consuming and labor-intensive process. 
Sifting through alerts, connecting the dots, and active hunting all add up to massive amounts of time and effort expended with minimal returns, 
and the possibility of sophisticated threats simply evading discovery. Particularly elusive threats like zero-day, targeted, 
and advanced persistent threats can be the most dangerous to your organization, making their detection all the more critical.

The UEBA capability in Azure Sentinel eliminates the drudgery from your analysts’ workloads and the uncertainty from their efforts, 
and delivers high-fidelity, actionable intelligence, so they can focus on investigation and remediation.

As Azure Sentinel collects logs and alerts from all of its connected data sources, 
it analyzes them and builds baseline behavioral profiles of your organization’s entities (such as users, hosts, IP addresses, and applications) 
across time and peer group horizon. Using a variety of techniques and machine learning capabilities, 
Azure Sentinel can then identify anomalous activity and help you determine if an asset has been compromised. 
Not only that, but it can also figure out the relative sensitivity of particular assets, identify peer groups of assets, 
and evaluate the potential impact of any given compromised asset (its “blast radius”). Armed with this information, you can effectively prioritize your investigation and incident handling.

# Enable UEBA in Azure Sentinel


```KQL
BehaviorAnalytics
| where ActivityType == "FailedLogOn"
| where FirstTimeUserConnectedFromCountry == True
| where CountryUncommonlyConnectedFromAmongPeers == True
```