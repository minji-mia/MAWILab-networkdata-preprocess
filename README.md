# Networkdata Preprocess from MAWILab

## About MAWILab
MAWILab is a database that assists researchers to evaluate their traffic anomaly detection methods. It consists of a set of labels locating traffic anomalies in the MAWI archive (samplepoints B and F). The labels are obtained using an advanced graph-based methodology that compares and combines different and independent anomaly detectors. The data set is daily updated to include new traffic from upcoming applications and anomalies.

## Anomaly taxonomy
[Mazel et al. (TRAC 2014)](http://www.necoma-project.eu/m/filer_public/0d/34/0d34ebf0-0e45-46ea-a40b-852bc6eb758f/johan_taxonomy.pdf) presented a taxonomy that reveals the nature of backbone traffic anomalies. MAWILab takes advantage of this taxonomy to provide more insights into the identified anomalies. The taxonomy consists of more than one hundred labels and corresponding signatures to classify events identified in backbone traffic. The details of labels and signatures are available at http://www.fukuda-lab.org/mawilab/classification/ .

Since MAWILab v1.1, the plots depicting the byte and packet breakdown in the data set webpages (e.g. http://www.fukuda-lab.org/mawilab/v1.1/index.html) are also based on this taxonomy. Each class in the plots corresponds to labels with a certain prefix:

- Unknown are labels starting with the prefixes "unk" and "empty"
- Other are labels starting with the prefixes "ttl_error","hostout","netout", and "icmp_error"
- HTTP are labels starting with the prefixes "alphflHTTP","ptmpHTTP","mptpHTTP","ptmplaHTTP" and "mptplaHTTP"
- Multi. points are labels starting with the prefixes "ptmp","mptp" and "mptmp"
- Alpha flow are labels starting with the prefixes "alphfl","malphfl","salphfl","point_to_point" and "heavy_hitter"
- IPv6 tunneling are labels starting with the prefixes "ipv4gretun" and "ipv46tun"
- Port scan are labels starting with the prefixes "posca" and "ptpposca"
- Network scan ICMP are labels starting with the prefixes "ntscIC" and "dntscIC"
- Network scan UDP are labels starting with the prefixes "ntscUDP" and "ptpposcaUDP"
- Network scan TCP are labels starting with the prefixes "ntscACK","ntscSYN","sntscSYN","ntscTCP","ntscnull","ntscXmas","ntscFIN" and "dntscSYN"
- DoS are labels starting with the prefixes "DoS","distributed_dos","ptpDoS","sptpDoS","DDoS" and "rflat"

## CSV format
Since MAWILab v1.1, anomalies are also reported in CSV format. Each line in the CSV files consists of a 4-tuple describing the traffic characteristics (similar to filters in the admd format) and additional information such as the heuristic and taxonomy classification results. The actual order of the fields is given by the CSV files header:

anomalyID, srcIP, srcPort, dstIP, dstPort, taxonomy, heuristic, distance, nbDetectors, label
- anomalyID is a unique anomaly identifier. Several lines in the CSV file can describe different sets of packets that belong to the same anomaly. The anomalyID field permits to identify lines that refer to the same anomaly.
- srcIP is the source IP address of the identified anomalous traffic (optional).
- srcPort is the source port of the identified anomalous traffic (optional).
- dstIP is the destination IP address of the identified anomalous traffic (optional).
- dstPort is the destination port of the identified anomalous traffic (optional).
- taxonomy is the category assigned to the anomaly using the taxonomy for backbone traffic anomalies.
- heuristic is the code assigned to the anomaly using simple heuristic based on port number, TCP flags and ICMP code.
- distance is the difference Dn-Da, see XML Schema (admd).
- nbDetectors is the number of configurations (detector and parameter tuning) that reported the anomaly.
- label is the MAWILab label assigned to the anomaly, it can be either: anomalous, suspicious, or notice.



## Built with

- [Python 3.7](https://www.python.org/)
- [Scapy](https://scapy.net/)

## Reference
http://www.fukuda-lab.org/mawilab/
