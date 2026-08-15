# 🔍 Investigation Report: Mobile banking vulnerability
Date: 08/14/2026  |  Platform: TryHackMe  |  Room: Offensive Security Intro  |  Difficulty: Beginner  |  Tools Used: Linux Terminal, Dirbuster


**Offensive Security** is about thinking like an attacker to find weaknesses before real hackers do.
**Dirbuster** is a security testing (pentest) tool that finds hidden files and directories on web servers using wordlist brute-force attacks.


## :rotating_light: Scenario description
The goal of this room was to identify security weaknesses in the **FakeBank** web application. A common security flaw in web applications is relying on obscurity by leaving hidden pages or administrative endpoints accessible without proper access controls or authentication checks.

## :detective: Investigation step-by-step
### Step 1
Open the terminal and run **dirb** with bank's URL to find hidden pages.
### Step 2
Pages found: http://fakebank.thm/images and http://fakebank.thm/bank-transfer
### Step 3
Go to the URL http://fakebank.thm/bank-transfer, enter the account number, and deposit money. After depositing, go back to the account page and check the amount.


## :shield: Conclusion
The investigation showed that the FakeBank application suffers from Broken Access Control and relies on Security through Obscurity. Using a directory brute-force tool made it possible to discover hidden sensitive endpoints (**/bank-transfer**) that lack proper authentication checks. As a result, an aunauthenticated user can access financial functions and perform unauthorized money transfers without logging in.


## Recommended actions
- **Implement Strong Access Control:** Restrict access to sensitive endpoints like /bank-transfer. Require user authentication and verify permissions before allowing access to financial functions.
- **Avoid Security through Obscurity:** Do not rely on hidden URLs to protect sensitive pages. Always secure pages with server-side authentication mechanisms.
- **Enforce Transaction Authorization:** Ensure that every transfer or deposit request checks the user's session and verifies account ownership on the server side before processing the transaction.
- **Disable Directory Listing & Audit Endpoints:** Configure the web server to prevent directory listing and regularly audit all public endpoints to remove exposed test or administrative pages.
