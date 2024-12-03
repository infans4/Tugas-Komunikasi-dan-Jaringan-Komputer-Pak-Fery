# **UAS Semseter Gasal TA 2024/2025**
# **S2 TIK A**

1224800010
Muhammad Infan Tri Andhika

Question and answer below are based on the trace file tcp-ethereal-trace-1 in in http://gaia.cs.umass.edu/wireshark-labs/wireshark-traces.zip
---
Answer the following questions for the TCP segments:
## **1. What is the IP address and TCP port number used by your client computer (source) to transfer the file to gaia.cs.umass.edu? (10%)**
![Figure 1](https://github.com/infans4/1224800010_Muhammad-Infan-Tri-Andhika_UAS-Komunikasi-dan-Jaringan-Komputer-2024/blob/main/assets/Picture%201.png)
Answer:
Based on the figure above, the first client computer initiation IP Address mean client itself. So the IP address is 192.168.1.102 and the port of the TCP is 1161.

## **2. What does gaia.cs.umass.edu use the IP address and port number to receive the file. (Attach the screenshot of your Wireshark's display) (10%)**
![Figure 2](https://github.com/infans4/1224800010_Muhammad-Infan-Tri-Andhika_UAS-Komunikasi-dan-Jaringan-Komputer-2024/blob/main/assets/Picture%202.png)
Answer:
Based on the figure above, the response from client computer initiation IP Address is the server that mean gaia.cs.umass.edu. So the IP address is 128.119.245.12 and the port of the TCP is 80.

## **3. 	What is the sequence number of the TCP SYN segment that is used to initiate the TCP connection between the client computer and gaia.cs.umass.edu? What is it in the segment that identifies the segment as a SYN segment? (Attach the screenshot of your Wireshark's display) (10%)**
![Figure 3](https://github.com/infans4/1224800010_Muhammad-Infan-Tri-Andhika_UAS-Komunikasi-dan-Jaringan-Komputer-2024/blob/main/assets/Picture%203.png)
Answer:
First, the sequence number that initiate the TCP SYN segment connection between client to server that we can see in “Seq : 0”. That mean the value is 0.
Second, the flags in TCP dropdown description. The value set to 1 indicating the SYN segment is active.

## **4. What is the sequence number of the SYNACK segment sent by gaia.cs.umass.edu to the client computer in reply to the SYN? What is the value of the ACKnowledgement field in the SYNACK segment? How did gaia.cs.umass.edu determine that value? What is it in the segment that identifies the segment as a SYNACK segment? (Attach the screenshot of your Wireshark's display) (10%)**
![Figure 4](https://github.com/infans4/1224800010_Muhammad-Infan-Tri-Andhika_UAS-Komunikasi-dan-Jaringan-Komputer-2024/blob/main/assets/Picture%204.png)
Answer:
First, the sequence number that response the connection from client to server that we can see in “Seq : 0”. That mean the value is 0.
Second, value of ACKnowledment in this segment is 1. This value mean server add 1 to the initial sequence number of SYN segment from the client.
Third, SYN and ACKnowledgment flag set to 1 that mean of this segment is SYNACK segement.

## **5. What is the sequence number of the TCP segment containing the HTTP POST command? Note that in order to find the POST command, you’ll need to dig into the packet content field at the bottom of the Wireshark window, looking for a segment with a “POST” within its DATA field.(Attach the screenshot of your Wireshark's display) (15%)**
![Figure 5](https://github.com/infans4/1224800010_Muhammad-Infan-Tri-Andhika_UAS-Komunikasi-dan-Jaringan-Komputer-2024/blob/main/assets/Picture%205.png)
Answer:
Based on the capture, the TCP segement contain HTTP POST command in line 4. The sequence number of this segment is 1.

## **6.     6. Consider the TCP segment containing the HTTP POST as the first segment in the TCP connection. What are the sequence numbers of the first six TCP connection segments (including the HTTP POST segment)? At what time was each segment sent? When was the ACK for each segment received? Given the difference between when each TCP segment was sent, and when its acknowledgement was received, what is the RTT value for each of the six segments? What is the EstimatedRTT value (see page 237 in textbook) after the receipt of each ACK? Assume that the value of the EstimatedRTT is equal to the measured RTT for the first segment, and then is computed using the EstimatedRTT equation on page 237 for all subsequent segments. (30%)
Note: Wireshark has a nice feature that allows you to plot the RTT for each of the TCP segments sent. Select a TCP segment in the “listing of captured packets” window that is being sent from the client to the gaia.cs.umass.edu server. Then select: Statistics->TCP Stream Graph-
>Round Trip Time Graph.**
![Figure 6](https://github.com/infans4/1224800010_Muhammad-Infan-Tri-Andhika_UAS-Komunikasi-dan-Jaringan-Komputer-2024/blob/main/assets/Picture%206.png)
Answer:
Based on the capture, the HTTP POST segment is from the first segement. The 1-6 segments are 4, 5, 7, 8, 10, and 11. The 1-6 ACK segments are 6, 9, 12, 14, 15, and 16.
Segment 1 seq number :1
Segment 2 seq number :566
Segment 3 seq number :2026
Segment 4 seq number :3486
Segment 5 seq number :4946
Segment 6 seq number :6406

Sent, ACK received, RTT, and Estimated RTT time are tabulated in the table below.
![Figure 7](https://github.com/infans4/1224800010_Muhammad-Infan-Tri-Andhika_UAS-Komunikasi-dan-Jaringan-Komputer-2024/blob/main/assets/Picture%207.png)

To get RTT we need a formula:
RTT (second) =ACK Received Time – Sent Time
For Estimated RTT  after receipt ACK of segment x:
Est. RTT = 0.875 * Estimated RTT (x before) + 0.125 * Sample RTT

![Figure 8](https://github.com/infans4/1224800010_Muhammad-Infan-Tri-Andhika_UAS-Komunikasi-dan-Jaringan-Komputer-2024/blob/main/assets/Picture%208.png)
Segment 1-6
![Figure 9](https://github.com/infans4/1224800010_Muhammad-Infan-Tri-Andhika_UAS-Komunikasi-dan-Jaringan-Komputer-2024/blob/main/assets/Picture%209.png)
ACK after segment 1-6
![Figure 10](https://github.com/infans4/1224800010_Muhammad-Infan-Tri-Andhika_UAS-Komunikasi-dan-Jaringan-Komputer-2024/blob/main/assets/Picture%2010.png)
RTT Graph by Sequence Number

## **7. What is the length of each of the first six TCP segments?(Attach the screenshot of your Wireshark's display)  (15%)**
![Figure 11](https://github.com/infans4/1224800010_Muhammad-Infan-Tri-Andhika_UAS-Komunikasi-dan-Jaringan-Komputer-2024/blob/main/assets/Picture%2011.png)
Answer:
Based on the capture, the HTTP POST segment is from the first segement. The 1-6 segments are 4, 5, 7, 8, 10, and 11. 
Length of the segment 1 is 565 bytes and the other are 1460 bytes.
