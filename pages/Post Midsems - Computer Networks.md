# #[[Before Midsems - Computer Networks]]
- ## TCP [contd]
  id:: 662e405d-9b2e-4f8a-8675-08cb35d52022
	- ### TCP Header
		- #### Sequence No. (32 bits)
			- ID of first byte of segment
			- Sent from source sending the data
			- ##### Random Sequence No. at start
				- To avoid a packet to be misinterpreted as newer packet after process restart.
				- Like non-received packet(seq no=200) be misinterpreted as newer packet(seq no=200) after immediate process restart.
			- ##### Wrap around sequence no.
				- Wrapping(101 -> 1) sequence no. else max possible data is 2^32 - 1 = around 4 GB.
				- Wrap around time : Time to send 4GB of data in TCP (time after which seq no starts repeating)
					- Wrap around Time = Max Data(4 GB) / Bandwidth
				- Life time : Max time for which a packet is present in the network (generally 180s)
				- Wrap Around Time > Life time else issue in transmission (Older 0th seq no. get interpreted in newer wrapped context)
				- To fix this, we add option field as timestamp(8 bit) with sequence no., hence total data and hence wrap around time increases automatically
		- #### Acknowledgement No.
			- Which next seq no. packet to expect
			- It is _received_ Sequence no + "TCP" Data Size + 1
				- TCP Data Size = IP Packet Size - IP Header - TCP Header as TCP data length is not in headers
			- Sent from sink receiving the data
		- #### Header Length (Data Offset)
			- Header Length = 4 * Binary value of data offset (Min = 20B Max = 60B)
		- #### Checksum
			- Using CRC
			- TCP Header[Checksum all bits 0] + TCP Data + Pseudo Header
			- ![image.png](../assets/image_1714323901892_0.png)
		- ((662a439b-d867-4150-861e-f7952102946b))
		- ### Flags
			- #### PSH
				- Push data without filling maximum segment size
				- For realtime apps
			- #### URG and Urgent Pointer
				- Data forwarding out of order to send data urgently (Max Value = 7)
				- ![image.png](../assets/image_1714328155626_0.png){:height 235, :width 501}
			- #### RST
				- To reestablish the connection due to system reboot or unreliable sequence no.(seq no. is out of current window buffer range)
		- #### Options
			- If Window size > 2^16 (Window Field) then extra data is put in option field.
	- ### Flow control
		- Control transfer speed
			- Window Scaling
				- Common Window size in during connection establishment in TCP
			- Advertisement Window Size
				- During transmission of data, receiver will advertise its window size to sender continuously to prevent over transmission in case of full buffer.
			- Persistent Timer
				- After some persistant time, sender can send PROBE frame to receiver to check if its buffer is still full or has empty space, to restart transmitting data.
			- ![image.png](../assets/image_1714363872681_0.png){:height 386, :width 498}
	- ### Sliding Window Protocol
		- #### Hybrid Sliding Window Protocol
			- ##### Selective Repeat
				- Sender Window Size = Receiver Window Size
				- Accepts out of order segment (waiting for seq=101, but can accept 150th too if window size allows)
			- ##### Go Back N
				- Sending acummulative acknowledgements, of multiple packets at once.
	- ### Retransmission in TCP
		- #### Timeout based
			- Resend packet after timeout if ACK not received for it.
		- #### Dupack or Early retransmission
			- Before transmission, on receiving _three duplicate_ ACK for a segment
	- ### Congestion Control
		- Network Layer - ICMP (Router to Router)
		- Transport Layer - TCP (Entire end to end network)
		- By scaling window size (lower Window size lesser the data transferred)
		- Stages
			- Slow start phase
			  logseq.order-list-type:: number
				- _Congestion Window(Wc)_ = 1 or 2 initially and will grow by _x_ 2 till threshold
			- Congestion Avoidance phase
			  logseq.order-list-type:: number
				- Congestion Window increase by _+_ 1, if no congestion
			- Continuously Congestion Avoidance phase
			  logseq.order-list-type:: number
				- Timeouts (Severe congestion)
				  logseq.order-list-type:: number
					- _Wth(threshold value)_ = Wc/2 and slow start
				- 3 Duapack (Mild congestion)
				  logseq.order-list-type:: number
					- Wth = Wc/2 and congestion avoidance
			- ![image.png](../assets/image_1714380662623_0.png){:height 276, :width 528}
				- Wth = Wr / 2 = 64 / 2 = 32
				- Roundtrip time to reach Wr = log2 (Wth) + 1 + Wth
			- After SYN, Window Size(sender) = min (Receiver Window Size, Wc)
	- ### Timers
		- #### Time-wait timers
			- Delayed segments received by the receiver
		- #### Persistent Timer
			- Stop sending data for fixed time after receiver window is full
		- #### Keep Aliver Timer
			- Close Idle connection, server sent probe frames after keep alive time to check if client is idle or not
		- #### Acknowledgement Timer
			- Sends cummulative ACK of all packets after ACK timer times out!
		- #### Timeout Timer
			- For retransmission of data after timeout if its ACK is not received
			- Based dynamically on network params like traffic, bandwidth etc
			- ##### Basic Algortihm for Timeout timers
				- Assume Initial Round Trip Time (IRTT)
				  logseq.order-list-type:: number
				- Timeout Timer $$T_o$$ = 2 IRTT
				  logseq.order-list-type:: number
				- Observe Actual Round Trip Time (ARTT)
				  logseq.order-list-type:: number
					- New Round Trip Time (NRTT) = \alpha IRTT + (1- \alpha) ARTT
					  logseq.order-list-type:: number
					- \alpha is smoothing factor
					  logseq.order-list-type:: number
					- $T_o$ = 2 NRTT
					  logseq.order-list-type:: number
					- IRTT = NRTT of previous segment 
					  logseq.order-list-type:: number
	- ### Silly Window Syndrome
		- Due to ineffective utilization of resources (
			- Window size is full,
			- Slower Sender
			- SloweReceiver)
		-