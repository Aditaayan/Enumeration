# Explore Google hacking and enumeration 

# AIM:

To use Google for gathering information and perform enumeration of targets

## STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various Google hacking keywords and enumeration tools as follows:


### Step 3:
Open terminal and try execute some kali linux commands

## Pen Test Tools Categories:  

| Operator    | Description                        | Example Usage           |
| ----------- | ---------------------------------- | ----------------------- |
| `site:`     | Search within a specific domain    | `site:example.com`      |
| `inurl:`    | Search in URL                      | `inurl:admin`           |
| `intitle:`  | Search in page title               | `intitle:"index of"`    |
| `filetype:` | Search by file type                | `filetype:pdf`          |
| `intext:`   | Search inside page text            | `intext:"confidential"` |
| `link:`     | Pages that link to a specific site | `link:example.com`      |
| `cache:`    | View cached version of a site      | `cache:example.com`     |
| `ext:`      | Same as filetype                   | `ext:xls`               |

 ## Architecture 
 ```
+----------------------+
|   Attacker / Hacker  |
|   (Browser & Google) |
+----------+-----------+
           |
           | Google Dork Queries
           v
+---------------------------+
|       Google Search       |
+---------------------------+
           |
           | Indexed Public Content
           v
+---------------------------+
|   Target Websites / Data  |
| - Leaked files            |
| - Open directories        |
| - Sensitive info          |
+---------------------------+

```

# Output:
# SITE:
=<img width="952" height="865" alt="Screenshot 2025-09-13 091909" src="https://github.com/user-attachments/assets/4c33a49d-700e-490a-96cf-28b0cce072a2" />

# INURL:
<img width="946" height="934" alt="Screenshot 2025-09-13 091930" src="https://github.com/user-attachments/assets/918efc28-a5b7-497c-bc49-3e59cc9f1a23" />

# INTITLE:
<img width="934" height="970" alt="Screenshot 2025-09-13 091949" src="https://github.com/user-attachments/assets/84074abc-16fc-49fb-aefa-e0f84441e24f" />

# FILETYPE:

# INTEXT:
<img width="951" height="966" alt="Screenshot 2025-09-13 092013" src="https://github.com/user-attachments/assets/5d721baa-45b2-4971-b0a9-a1a1022e5976" />

# LINK:
<img width="946" height="966" alt="Screenshot 2025-09-13 092033" src="https://github.com/user-attachments/assets/f4306e48-4acf-43c7-8357-71192e33706f" />

# DNS Enumeration
<img width="1919" height="977" alt="Screenshot 2025-09-04 104949" src="https://github.com/user-attachments/assets/a9e9d474-e587-4c7e-b6af-eb5dbf8a9d25" />

## DNS Recon
<img width="1919" height="696" alt="Screenshot 2025-09-04 105116" src="https://github.com/user-attachments/assets/eecaac38-8a30-4602-b053-683defc7ad19" />


| Record Type | Meaning                        | Example Output                   |
| ----------- | ------------------------------ | -------------------------------- |
| A           | Host to IPv4 address           | `example.com -> 93.184.216.34`   |
| AAAA        | Host to IPv6 address           | `example.com -> ::1`             |
| MX          | Mail server info               | `mail.example.com`               |
| NS          | Name servers                   | `ns1.example.com`                |
| TXT         | Misc data (SPF, verifications) | `v=spf1 include:_spf.google.com` |
| CNAME       | Canonical names (aliases)      | `www -> example.com`             |

## Common Tools Used (Kali Linux)

| Tool           | Description                                | Usage Example                           |
| -------------- | ------------------------------------------ | --------------------------------------- |
| `nslookup`     | DNS lookup tool (simple queries)           | `nslookup example.com`                  |
| `dig`          | DNS lookup utility (detailed)              | `dig example.com any`                   |
| `host`         | Simple DNS querying tool                   | `host example.com`                      |
| `dnsenum`      | Perl script to enumerate DNS info          | `dnsenum example.com`                   |
| `fierce`       | DNS scanner to locate non-contiguous IPs   | `fierce -dns example.com`               |
| `dnsrecon`     | Powerful DNS enumeration script            | `dnsrecon -d example.com -a`            |
| `theHarvester` | Subdomain enumeration using search engines | `theHarvester -d example.com -b google` |


## OUTPUT:
# NSLOOKUP:

# DIG:
<img width="1920" height="1080" alt="KALI  Running  - Oracle VirtualBox 13-09-2025 09_11_39" src="https://github.com/user-attachments/assets/134567bb-5669-4514-b528-9ab35fd65071" />

# HOST:

# FIERCE:
<img width="612" height="72" alt="KALI  Running  - Oracle VirtualBox 13-09-2025 09_12_52" src="https://github.com/user-attachments/assets/35245eca-aa9c-4b6e-8f52-3343c3bcde74" />

# HARVESTER:
<img width="1920" height="1080" alt="KALI  Running  - Oracle VirtualBox 13-09-2025 09_16_46" src="https://github.com/user-attachments/assets/9604aeac-5b5e-4ed9-9752-db5cbd35d668" />


## Architecture Diagram 
```
+-------------------+        +------------------+       +------------------+
|                   |        |                  |       |                  |
|   Attacker (You)  +------->|   Target Server   +<----->+    DNS Server    |
| Kali Linux / Parrot|       | (Mail / DNS Host) |       |  (Authoritative) |
+---------+---------+        +---------+--------+       +---------+--------+
          |                            ^                          ^
          |                            |                          |
          |                            |                          |
          |           +-----------------------------+            |
          |           |      Information Tools      |            |
          |           |-----------------------------|            |
          |           | smtp-user-enum              |            |
          |           | nmap --script smtp-enum-*   |            |
          |           | dnsenum                     |<-----------+
          |           +-----------------------------+
          |
          v
+-----------------------------+
|   Output/Report             |
|  - Usernames Found          |
|  - MX Records / Zones       |
|  - Subdomains / IPs         |
+-----------------------------+

```

## dnsenum
**Purpose:** A multithreaded Perl script to enumerate information from DNS servers.

**Use case:** Performs DNS zone transfers, brute force subdomains, and gather host IPs.

```
dnsenum example.com
```

## Output:

<img width="1920" height="1080" alt="KALI  Running  - Oracle VirtualBox 13-09-2025 08_59_23" src="https://github.com/user-attachments/assets/3c17c03f-dc26-48e0-ad8f-a6b2eb52497d" />


## smtp-user-enum
**Purpose:** Standalone tool used to enumerate valid users by using the VRFY, EXPN, or RCPT TO commands.

**Use case:** Brute-forces SMTP to find users.

```
smtp-user-enum -M VRFY -U users.txt -t <target-ip>
```
  
 ## Output
<img width="1920" height="1080" alt="KALI  Running  - Oracle VirtualBox 13-09-2025 09_01_55" src="https://github.com/user-attachments/assets/0a8b4314-86b9-4b78-a5d9-9339f7ebd940" />

## nmap –script smtp-enum-users.nse <hostname>

**Purpose:** Uses smtp-enum-users NSE script to enumerate valid users on an SMTP server.

**Use case:** Helps identify email accounts on mail servers.

```
nmap -p 25 --script smtp-enum-users.nse <target-ip>
```
## OUTPUT:

## RESULT:
The Google hacking keywords and enumeration tools were identified and executed successfully
