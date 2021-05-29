# HomDroid: Detecting Android Covert Malware by Social-Network Homophily Analysis
Android has become the most popular mobile operating system.
Correspondingly, an increasing number of Android malware has
been developed and spread to steal users’ private information. There
exists one type of malware whose benign behaviors are developed
to camouflage malicious behaviors. The malicious component occupies
a small part of the entire code of the application (app for
short), and the malicious part is strongly coupled with the benign
part. In this case, the malware may cause false negatives when
malware detectors extract features from the entire apps to conduct
classification because the malicious features of these apps may be
hidden among benign features. Moreover, some previous work aims
to divide the entire app into several parts to discover the malicious
part. However, the premise of these methods to commence app
partition is that the connections between the normal part and the
malicious part are weak (e.g., repackaged malware).

In this paper, we call this type of malware as Android covert
malware and generate the first dataset of covert malware. To detect
these malware samples,we first conduct static analysis to extract the
function call graphs. Through the deep analysis from these graphs,
we observe that although the correlations between the normal part
and the malicious part in these graphs are high, the degree of these
correlations has a unique range of distribution. By this, we design a
novel system (i.e., HomDroid) to detect covert malware by analyzing
the homophily of call graphs.

1) Static Analysis: Given an app, we first conduct static analysis
to obtain the function call graph where each node is a
function that can be an API call or a user-defined function.
2) Graph Partition: After generating the call graph, we then
divide it into certain subgraphs by community detection and
discover the most suspicious part by homophily analysis.
The output of this phase is the most suspicious subgraph.
3) Feature Extraction: Next, two types of feature sets are collected
from the suspicious subgraph, including the appearance
of sensitive API calls and the ratio of the number of
sensitive triads to the total number of triads within the subgraph.
4) Classification: In our final phase, given a feature vector,
we can accurately flag it as either benign or malicious by
using a trained machine learning classifier.

# Dataset
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

# Publication
Yueming Wu, Deqing Zou, Wei Yang, Xiang Li, and Hai Jin. 2021. HomDroid:
Detecting Android Covert Malware by Social-Network Homophily Analysis.
In Proceedings of the 30th ACM SIGSOFT International Symposium on Software
Testing and Analysis (ISSTA’21), July 11–17, 2021, Virtual, Denmark. ACM,
New York, NY, USA, 13 pages. https://doi.org/10.1145/3460319.3464833
