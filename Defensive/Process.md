## Alert Triage
The alert triage is the basis of the SOC team. The first response to any alert is to perform the triage. The triage is focused on analyzing the specific alert. This determines the severity of the alert and helps us prioritize it. The alert triage is all about answering the 5 Ws. What are these 5 Ws?
![[6645aa8c024f7893371eb7ac-1718872960352.png|235x199]]
Exemple : 

| 5 Ws   | Answers                                                                 |
|--------|------------------------------------------------------------------------|
| What?  | A malicious file was detected on one of the hosts inside the organization’s network. |
| When?  | The file was detected at 13:20 on June 5, 2024.                        |
| Where? | The file was detected in the directory of the host: "GEORGE PC".       |
| Who?   | The file was detected for the user George.                             |
| Why?   | After the investigation, it was found that the file was downloaded from a pirated software-selling website. The investigation with the user revealed that they downloaded the file as they wanted to use a software for free. |

## Reporting

The detected harmful alerts need to be escalated to higher-level analysts for a timely response and resolution. These alerts are escalated as tickets and assigned to the relevant people. The report should discuss all the 5 Ws along with a thorough analysis, and screenshots should be used as evidence of the activity.

## Incident Response and Forensics

Sometimes, the reported detections point to highly malicious activities that are critical. In these scenarios, high-level teams initiate an incident response. A few times, a detailed forensics activity also needs to be performed. This forensic activity aims to determine the incident’s root cause by analyzing the artifacts from a system or network.