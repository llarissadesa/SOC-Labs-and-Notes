# 🔍 Investigation Report: Find server details
Date: 08/18/2026  |  Platform: TryHackMe  | Room: Search Skills |  Difficulty: Beginner  |  Tools Used: Shodan, TryScanMe, Apache 


**Shodan** is a special search engine that looks for devices connected to the internet, like security cameras and smart machines. It shows where these devices are and what software they use. Security experts use Shodan to quickly find weak systems that need to be fixed, using easy search filters to narrow down the results.

**Apache** is a highly popular web server, making it a frequent target for attackers searching for vulnerabilities.

## :rotating_light: Scenario description
Check the web server's IP address using TryScanMe.

## :detective: Investigation step-by-step
### Step 1
Search for Apache on TryScanMe. Click on the first row and check which domain uses the IP.

### Step 2
The domain found was trychackme.thm.


## :shield: Conclusion 
Apache is a very popular server, and Shodan monitors the internet to map the servers running it and check if they are vulnerable. If the server is vulnerable, Shodan publishes a security alert.

## Recommended actions
To prevent Shodan from exposing your Apache server details, you must:
- Change the banner to hide the exact version and the operating system.
- Remove server information from error pages.
