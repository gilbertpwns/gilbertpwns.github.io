# Introduction to Brute Forcing

## What is Brute-Forcing?

A trial-and-error method used to crack passwords, login credentials, or encryption keys by systematically trying every possible combination of characters.

## Factors Influencing Brute Force Attacks

* complexity of the password or key
* computational power available to the attacker
* security measures

## How Brute Forcing Works

1. Start: The attacker initiates the brute force process.
2. Generate Possible Combination: software generates a potential password or key combination.
3. Apply Combination: The generated combination is attempted against the target system
4. Check if Successful: system evaluates the attempted combination
5. Access Granted (if successful): The attacker gains unauthorized
6. End (if unsuccessful): The process repeats until the correct combination is found or the attacker gives up.

## Types of Brute-Forcing

| Attack Type | Description |  Best Used When |
|:-:|:-:|:-:|
| Simple Brute Force | Tries every possible character combination in a set (e.g.: lowercase, uppercase, numbers, symbols) | When there is no prior information about the password | 
| Dictionary Attack | Uses a pre-compiled list of common passwords. | When the password is likely weak or follows common patterns |
| Hybrid Attack | Combine brute and dictionary attacks, adding number or symbols to dictionary words | When the target uses slightly modified versions of common passwords. |
| Credential Stuffing | Uses leaked credentials from other breaches to access different services where users may have reused passwords | When you have a set of leaked credentials, and the target may reuse passwords |
| Password Spraying | Attempts common passwords across many accounts to avoid detection | When account lockout policies are in place |
| Rainbow Table Attack | Users precomputed tables of password hashes to reverse them into plaintext passwords | When a large number of password hashes need cracking, and storage for tables is available |
| Reverse Brute Attack | Targets a known password against multiple usernames | Whens there's a suspicion  of password reuse across multiple accounts. |
| Distributed Brute Force | Distributes brute force attempts across multiple machines to speed up the process | When the password is slightly complex, and a single machine isn't powerful enough|

## Default Credentials

| Device | Username | Password |
|:-:|:-:|:-:|
| Linksys Router | admin | admin |
| Netgear Router | admin | password |
| TP-Link Router | admin | admin |
| Cisco Router | cisco | cisco |
| Ubiquiti Router | ubnt | ubnt |

## Brute-Forcing Tools

### hydra

* fast network login cracker
* supports numerous protocols
* uses parallel connections for speed
* flexible and adaptable
* relatively easy to use

> hydra [-l LOGIN|-L FILE] [-p PASS|-P FILE] [-C FILE] -m MODULE [service://server[:PORT][/OPT]]

| Hydra Service | Service/Protocol | Description | Example Command |
|:-:|:-:|:-:|:-:| 
| ftp | file transfer protocol (FTP) | used to brute-force login credentials for FTP services,commonly used to transfer files over a network | hydra -l admin -P /path/to/password_list.txt ftp://192.168.1.100 |
| ssh |  secure shell (SSH) | targets SSH services to brute-force credentials, commonly used for secure remote login to systems | hydra -l root -P /path/to/password_list.txt ssh://192.168.1.100 |
| http-get/post | HTTP web services | used to brute-force login credentials for HTTP web login forms using either GET or POST request | hydra -l admin -P /path/to/password_list.txt 127.0.0.1 http-post-form "/login.php:user=^USER^&pass=^PASS^:F=incorrect" | 

### medusa

* fast, massively parallel, modular login brute-forcer
* supports a wide array of services

> medusa [-h host|-H file] [-u username|-U file] [-p password|-P file] [-C file] -M module [OPT]

## custom wordlists

---

↩️ [BACK](../../README.md)

