---
title: "HTB Apocalypse 2023 - Packet Cyclone"
date: 2023-03-23T23:22:12+01:00
author: "goozy"
draft: false
tags : 
- "HTB Apocalypse 2023"
- "Forensic"
---
[download file](../forensics_packet_cyclone.zip)

Pandora's friend and partner, Wade, is the one that leads the investigation into the relic's location. Recently, he noticed some weird traffic coming from his host. That led him to believe that his host was compromised. After a quick investigation, his fear was confirmed. Pandora tries now to see if the attacker caused the suspicious traffic during the exfiltration phase. Pandora believes that the malicious actor used rclone to exfiltrate Wade's research to the cloud. Using the tool called "chainsaw" and the sigma rules provided, can you detect the usage of rclone from the event logs produced by Sysmon? To get the flag, you need to start and connect to the docker service and answer all the questions correctly.
Questions in container

# binary static analysis

1. File analysis
    ```
    $ file bin
    ```
2. Test
    * test
    * test
