# Social Engineering

## Types of Social Engineering

| Technique | Description |
|:-:|:-:|
| Phishing | Deceptive emails, messages, or websites desiged to trick recipients into revealing confidentials information, such as passwords, account credentials, or financial data 
| Spear Phishing | Targeted phishing attacks that are customized for specific individuals or groups within an organization, often used personalized information or context to increase credibility |
| Vishing (Voice Phishing) | Phishing attacks conducted over phone calls or voice messages, where attackers impersonate legitimate entities (e.g., IT support, bank reps) to extract sensitive informationg or manipulate victims into taking specific actions. | 
| Smishing (SMS) | Phishing attacks conducted via SMS or text messages, where recipients are tricked into clicking on malicious links or providing sensitive information by impersonating trusted entities |
| Pretexting | Creating a false pretext or scenario to gain the trust of targets and extract sensitive information. This may involve impersonating authority figures, colleagues, or service providers to manipulate victims into divulging confidential data.
| Baiting | Luring targets into performing a specific action (e.g. clicking URL, opening malicious file) by offering enticing incentives or rewards. Such as free software, prizes, or job opportunities | 
| Tailgating | Physically following authorized individuals into restricted areas or faciliites without proper authentication. Attackers exploit social norms or courtesy to gain unauthorized access to secure locations |

## Pretext Example

I'm not going to get into overly specific details on accomplishing many of these tasks. However, for the lesser known or utilized tactic (pretexting), here's a short examples of e-mail metadata/body:

```
<!-- PRETEXT OVERVIEW:
Credential capture.
$organization: Target organization.
$evilurl: URL to cloned Office 365 portal.
$evildomain: Spoofed domain.
Can be sent as helpdesk@domain.com.
Don't forget to setup the mailbox for user replies!
-->
<b>Subject: New Webmail - Office 365 Rollout</b>
<br>
<br>
Dear colleagues,
<br>
<br>
In an effort to continue to bring you the best available technology, $organization has implemented the newest version of Microsoft's Office 365 Webmail.
Your existing emails, contacts, and calendar events will be seamlessly transferred to your new account.
<br>
<br>
Visit the [new webmail website]($evilurl) and login with your current username and password to confirm your upgraded account.
<br>
<br>
If you have additional questions or need clarification, please contact the Help Desk at helpdesk@$evildomain.
<br>
<br>
Thank you,
```

A library of pretexts to use on offensive phishing engagements:

[Phishing Pretext Library](https://github.com/L4bF0x/PhishingPretexts/tree/master)

---

🔗 [Client Side Information Gathering](./client-side-info-gathering.md)

🔙 [Homepage](https://gilbertpwns.github.io)