# TCP
- Is more **reliable** than UDP
- It's segments have bigger header size
- Uses in HTTP, FTP, and ...
## TCP Sequence Number
- Sequence of bytes sender set's in segment header.
## TCP acknowledge Number
- The sequence number receiver expects from sender. 
---
- As an example think we have data with 100,000 bytes and MSS (maximum segment size) is 1000. so when TCP sends data it sets first segment sequence number to 0, second to 1000, third to 3000 and ... . But what if receiver machine get's sequence numbers 1000 and then 3000 instead of 2000? at this point the acknowledge number save us from loosing data. when receiver get's segment with sequence number 1000 it acknowledges the sender by setting acknowledge number 1000 and say to it hey I have first 1000 bytes and I want you to send me the next batch. on the other side the sender will acknowledge by this number and resend the 2000 sequence again.

# UDP
- It's less reliable than TCP because it doesn't grantee that it can fetch full response and it may have some data loss
- It has smaller header size
- Uses in Video streaming applications, DNS servers and ...