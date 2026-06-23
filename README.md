# TryHackMe-Alert-Triage-SOC-L1-Lab-mini-write-up.
TryHackMe Alert Triage SOC L1 mini write up.

## Objective
Investigate & identify SOC L1 Alerts Triage.

## Tools Used
* TryHackMe 
* Browser 
* TryHackMe SIEM

## Indicators Found: 
* False Positive and True Positive
* Suspicious attachment double extension file mp4.exe.
* SIEM and SOC Work-Book (play/runbook) rules Broken.
*	Downloaded files & Data sent.
---

### Suspicious Attachment (Double Extension)
* **Rule:** This rule detects a creation of a double-extension file like `*.pdf.exe` or `*.gif.lnk`, used by hackers in phishing attacks to trick users into opening the malicious executable. As we can see the extension is `mp4.exe` - a double-extension. 
* **File:** `C:\Users\S.Conway\Downloads\cats2025.mp4.exe`
* **File MotW:** `https://freecatvideoshd.monster/cats2025.mp4.exe`
<img width="672" height="484" alt="image" src="https://github.com/user-attachments/assets/c953ffea-df72-4c64-8c23-895c6e1c8aef" />


### GitHub Download
* **Rule:** This rule detects any download from GitHub. While GitHub stores lots of great projects that our IT team uses, it also stores malicious scripts and exploits that must not be downloaded by the users.
* **Accessed URL:** `https://github.com/facebook/react`
* **Observation:** User Source `User:G.Chandler` tried to download item from GitHub, now this doesn’t mean that item downloaded was a threat, the risk was a download but this does not equate to a threat this instance.
<img width="715" height="428" alt="image" src="https://github.com/user-attachments/assets/7fb4cb09-badd-46ff-8128-cdfe6a3bfac4" />


### Data Exfiltration (Volume Threshold)
* **Rule:** The Rule dictates that if there is over 5GB of data it will get alert in SIEM.
* **Observation:** As we can deduce we can see both destinations and both are known and legitimate destination and source the destination `*.zoom.us` and Source of the network: `UK04/MEETINGROOM`. From this even though 5.8GB was sent out it was from the `UK04/MEETINGROOM` to `*.zoom.us`. This clearly shows zoom meeting(s) were going on, throughout the entire day & within the organisation.
<img width="695" height="479" alt="image" src="https://github.com/user-attachments/assets/fff1ca9b-cfe9-4203-938a-823182819221" />


---

## Lessons Learnt
* Triaged Alerts from the SIEM TryHackMe Dashboard. 
* Alert Prioritised, who, what and how they are prioritised severity levels from Critical to low & from Old to new. 
* Only triage Alerts other Analyst have not and assigned myself to those alerts. 
* Familiarised myself with the alert details like its name, description and key indicators.  
* Learnt about workbooks(play/runbook) that SOC Teams may have, to discern & investigate specific categories of alerts. 
* Decided on whether or not, the alert is a False Positive or True Positive. 
* Analysed Numerous types of Alerts/ threats and risks involved with day to day threats SOC Analyst have to go through.

## Conclusion
The Alert Triage Lab, has given me insights into the type of Alerts/Threats a SOC analyst will have to triage & a look at the layout of a SIEM dashboard. How Threats/Alerts are triaged from the time of alert & to the severity. The indicators of compromise. To add, the concept of False Positive and True Positive, in this regards to this I found it very enlightening, not every alert is a threat, even if the alert is brought up because of rules of the SOC Workbook or defined Rules of the SIEM.
