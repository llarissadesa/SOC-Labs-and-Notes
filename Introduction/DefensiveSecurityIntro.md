# 🔍 Investigation Report: 
Date: 08/15/2026  |  Platform: TryHackMe  |  Room: Defensive Security Intro |  Difficulty: Beginner  |  Tools Used: Monitoring Dashboard


**Defensive security** is the process of defending and securing devices and systems.

## :rotating_light: Scenario description
The goal of this room was to help an apprentice SOC analyst identify and investigate suspicious network activity.

## :detective: Investigation step-by-step
### Step 1
Open the monitoring dashboard and review the recent alerts to spot the suspicious activity on the network.
### Step 2
Identify the attacker's source IP address (32.122.195.63) from the alert logs.
### Step 3
Access the "URL Discovery Attempts" list to analyze the attacker's history and see which hidden pages they are rapidly trying to access.
### Step 4
Examine the latest entry in the "URL Discovery Attempts" list to identify the specific type of attack taking place.
### Step 5
Navigate to the practical security actions panel where firewall and access control rules are managed.
### Step 6
Enter the IP 32.122.195.63 into the "Add Firewall Rule" field, "Block" from the dropdown menu, and click "Apply" to contain the threat.


## :shield: Conclusion 
The investigation showed that the application lacks proper monitoring and access controls. Using the monitoring dashboard, I identified an attacker rapdily probing hidden URLs from the IP and successfully contained the threat by applying a firewall block rule.


## Recommended actions
- **IP Blocking:** Add the attacker's IP to the firewall rules with a "Block" action to halt ongoing malicious traffic immediately.
- **Rate Limiting:** Implement request rate limits to restrict rapid, automated URL discovery and directory brute-force attempts.
- **Update Security Rules:** Enforce strict access control policies to secure sensitive endpoints and prevent unauthorized access to hidden pages.
- **Vulnerability Patching:** Audit the application to remediate the underlying flaw that allowed the attacker to discover and attempt access to restricted endpoints.
