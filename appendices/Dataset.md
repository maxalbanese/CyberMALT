# Dataset Description: CIC-IDS2017

To evaluate the proposed approach, we used the **CIC-IDS2017 (Canadian Institute for Cybersecurity Intrusion Detection Systems 2017)** dataset, a comprehensive collection of network traffic data designed for cybersecurity research, specifically focusing on intrusion detection systems (IDS). The dataset was created by the Canadian Institute for Cybersecurity at the University of New Brunswick and contains network traffic data captured in a controlled environment to simulate various types of cyber-attacks and normal network activities.

CIC-IDS2017 contains both benign and malicious traffic generated from modern attack tools. This traffic was captured and saved as PCAP files. From these files, the **CIC-Flow tool** [1] extracts features from network flows based on Source and Destination IPs, Source and Destination Ports, and Protocols. A flow is defined as the collection of packets exchanged during a TCP session between two entities. The dataset includes nearly 80 features (metadata) such as duration, number of packets, number of bytes, and packet length. Data capture occurred over five days, starting at 9 a.m. on Monday, July 3, 2017, and ending at 5 p.m. on Friday, July 7, 2017 [2]. The implemented attacks, including Brute Force FTP, Brute Force SSH, DoS, Heartbleed, Web Attack, Infiltration, Botnet, and DDoS, were executed in both morning and afternoon sessions on Tuesday, Wednesday, Thursday, and Friday [3].

Monday’s data consists only of benign flows. Tuesday’s data includes two attacks: FTP-Patator and SSH-Patator. **Patator** is a multi-purpose brute-force attack with a modular design and flexible usage [4]. It was executed by a machine running Kali Linux, targeting a server with IP `192.168.10.50`, which would be the victim of many other attacks.

Wednesday’s data features several DoS attacks, including **DoS Slow Loris**, **DoS Slowhttptest**, **DoS Hulk**, and **DoS GoldenEye**, all targeting the server with IP `192.168.10.50`, along with the implementation of the Heartbleed attack on a server with IP `192.168.10.51`.

- The **DoS Slow Loris** attack works by sending HTTP requests and maintaining them with partial request headers, preventing the server from releasing resources [5].
- **Slowhttptest** implements the most common low-bandwidth application layer DoS [6].
- The **Hulk DoS** creates multiple client processes that attack the target by sending asynchronous HTTP requests, similar to GoldenEye [7].
- The **Heartbleed attack** allows a user to read sensitive information due to a vulnerability in the server’s implementation of the Heartbeat extension.

The OpenSSL cryptography library’s Heartbleed vulnerability was exploited in this dataset, with the authors using port 444 instead of the usual port 443 [8].

On Thursday morning, web attacks such as **brute force**, **XSS**, and **SQL injection** were implemented on the server with IP `192.168.10.50` using the Damn Vulnerable Web App (DVWA), a deliberately insecure PHP/MySQL web application [2]. An infiltration attack was attempted on Thursday afternoon, but due to mislabeling, it is not considered in this dataset [9].

On Friday morning, the **Botnet Ares** attack was executed. Ares, a Python Remote Access Tool, compromised various machines in the local network, extracting data and sending it to the attacker’s command and control server at IP `205.174.165.73` [2]. In the afternoon, a **DDoS LOIC attack** targeted the server, sending numerous TCP, UDP, or HTTP requests. The attack involved three LOIC bot instances in the attacker’s network, which used the attacker’s public IP, masking the individual IPs of the bots from the local network perspective [10]. Finally, on Friday afternoon, **port scan attacks** were conducted to discover active ports on the server `192.168.10.50`. These attacks were executed only after disabling the firewall rules [2].

---

## References

1. CICFlowMeter. Available at: [https://www.unb.ca/cic/research/applications.htmlquicivasteriscoCICFlowMeter](https://www.unb.ca/cic/research/applications.htmlquicivasteriscoCICFlowMeter). Accessed: 2024-06-26.

2. Iman Sharafaldin, Arash Habibi Lashkari, and Ali A. Ghorbani. "Toward Generating a New Intrusion Detection Dataset and Intrusion Traffic Characterization." *International Conference on Information Systems Security and Privacy*, 2018. Available at: [https://api.semanticscholar.org/CorpusID:4707749](https://api.semanticscholar.org/CorpusID:4707749).

3. Intrusion detection evaluation dataset (CIC-IDS2017). Available at: [https://www.unb.ca/cic/datasets/ids-2017.html](https://www.unb.ca/cic/datasets/ids-2017.html). Accessed: 2024-06-26.

4. Patator. Available at: [https://www.kali.org/tools/patator/](https://www.kali.org/tools/patator/). Accessed: 2024-06-26.

5. What is a Slowloris DDoS attack. Available at: [https://www.cloudflare.com/learning/ddos/ddos-attack-tools/slowloris/](https://www.cloudflare.com/learning/ddos/ddos-attack-tools/slowloris/). Accessed: 2024-06-26.

6. Slowhttptest Documentation. Available at: [https://www.kali.org/tools/slowhttptest/](https://www.kali.org/tools/slowhttptest/). Accessed: 2024-06-26.

7. Hulk DoS tool analyzed and mitigated. Available at: [https://www.infosecurity-magazine.com/news/hulk-dos-tool-analyzed-and-mitigated/](https://www.infosecurity-magazine.com/news/hulk-dos-tool-analyzed-and-mitigated/). Accessed: 2024-06-26.

8. SSL Port 443 – The Heartbleed Attack. Available at: [https://www.infosecurity-magazine.com/news/hulk-dos-tool-analyzed-and-mitigated/](https://www.infosecurity-magazine.com/news/hulk-dos-tool-analyzed-and-mitigated/). Accessed: 2024-06-26.

9. Arnaud Rosay, Florent Carlier, Eloïse Cheval, Pascal Leroux. "From CIC-IDS2017 to LYCOS-IDS2017: A corrected dataset for better performance." *2021 IEEE International Conference*. DOI: [10.1145/3486622.3493973](https://doi.org/10.1145/3486622.3493973).

10. Low Orbit Ion Cannon (LOIC). Available at: [https://www.imperva.com/learn/ddos/low-orbit-ion-cannon/](https://www.imperva.com/learn/ddos/low-orbit-ion-cannon/). Accessed: 2024-06-26.
