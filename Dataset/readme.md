As API calls are used by the Android apps to access operating system functionality and system resources, 
they can be used as representations of the behaviors of Android apps. 
Moreover, Android malware usually invokes some sensitive API calls to perform malicious activities. 
Therefore, we assume these sensitive API calls and their correlated parent nodes as the malicious part and the rest as the normal part. 
Particularly, we focus on the largest collection of sensitive API calls (i.e., 21,986 API calls).
After dividing the graph into the normal part and malicious part, we build the covert malware dataset according to the following steps: 
1) We first conduct statistical analysis to obtain the proportion of malicious nodes in all nodes; 
2) We then perform homophily analysis to collect the correlation between the normal part and the malicious part; 
3) Next, malware samples with low correlation between the normal part and the malicious part are be omitted; 
4) As for the remaining malware, we divide them into six categories according to the proportion: [0-1%), [1%-2%), [2%-3%), [3%-4%), [4%- 5%), and greater than 5%;
5) To find which category may be more covert, we randomly select 100 samples from each category and upload them to VirusTotal; 
6) After analyzing the scanning results, we find that malware with a proportion of less than 2\% is less likely to be detected as malware. Therefore, we pay more attention to these malware with a proportion of less than 2% (i.e., 4,321 samples);
7) To further verify whether these samples contain disguised behaviors or not, we conduct dynamic analysis to obtain accurate behaviors. Specifically, we use some state-of-the-art security tools (e.g., AppCritique) to generate detailed behavior reports, and then manually analyze these reports to check whether sensitive API calls invoked by malicious behaviors are used by normal behaviors at the same time. If there are many such cases, then we consider the malware to be covert. After in-depth manual analysis, we finally obtain 3,358 covert malware samples.
