# Link_disruption_NS2

Below is the topology of the network we implemented

<img src="https://github.com/VaibhavDN/Link_disruption_NS2/blob/master/images/Picture1.png" width="80%">

There are total 14 nodes in the topology out of which 4 are source nodes and 2 are destination nodes.

    Node 0 UDP source

    Node 13 UDP source

    Node 1 TCP source

    Node 12 TCP source


    Node 10 UDP Sink (Loss Monitor)

    Node 11 TCP Sink


The bandwidth and propagation delay of each connection in between these nodes is given below:-

    Node 0 and 2 -> 4Mb 10ms 

    Node 1 and 2 -> 4Mb 10ms 

    Node 2 and 3 -> 3Mb 10ms 

    Node 3 and 4 -> 3Mb 10ms 

    Node 2 and 5 -> 2Mb 5ms 

    Node 5 and 6 -> 2Mb 5ms 

    Node 2 and 7 -> 4Mb 10ms 

    Node 7 and 8 -> 4Mb 10ms 

    Node 4 and 9 -> 4Mb 10ms

    Node 6 and 9 -> 4Mb 10ms

    Node 8 and 9 -> 4Mb 10ms 

    Node 9 and 10 -> 4Mb 10ms 

    Node 9 and 11 -> 4Mb 10ms 

    Node 3 and 12 -> 4Mb 5ms 

    Node 13 and 7 -> 4Mb 5ms 


Since the distance between Node 2 and Node 5 is minimum thus DV algorithm chooses path passing through node 2 - node 5. Despite the existence of node 2 - node 3 and node 2 - node 7 i.e. 2 paths of higher bandwidth. Since path with lower bandwidth is chosen we observe packet drops at node 3.


#### Network disruption analysis:

We implemented two nested for loops and try to disrupt link between every two nodes. If two nodes are not adjacent we catch the exception and pass the loop to the next node. 
Link is disrupted and restored at an interval of 0.5 sec. And we analyse the congestion window for TCP nodes and bandwidth received by UDP sink at an interval of 0.7 sec. That is we analyse at mean of disrupted or restored state.


Difference between New Reno, Reno, Vegas:

We implemented a pair of above mentioned algorithms on node 1 under same topology circumstances, and following graphs were observed:

Reno vs New Reno:

<img src="https://github.com/VaibhavDN/Link_disruption_NS2/blob/master/images/Picture2.png" width="80%">

Reno vs Vegas:

<img src="https://github.com/VaibhavDN/Link_disruption_NS2/blob/master/images/Picture3.png" width="80%">

New Reno vs Vegas:

<img src="https://github.com/VaibhavDN/Link_disruption_NS2/blob/master/images/Picture4.png" width="80%">

UDP Bandwidth analysis:

<img src="https://github.com/VaibhavDN/Link_disruption_NS2/blob/master/images/Picture5.png" width="80%">

Further we analyze two TCP nodes set at alternate position to observe the working of Distance Vector algorithm and plot the following graph:

#### RESULTS and CONCLUSION:

    -> We observed that TCP stops sending packets during congestion while UDP mindlessly keeps 
    sending packets into the network. This proves TCP implements congestion control.

    -> We found that New reno performs best for our topology out of other congestion control 
    algorithms. As observed from the graph.

    -> Same TCP congestion control algorithm when implemented by different TCP nodes perform 
    very differently as distance vector algorithm chooses different paths for different nodes.

    -> Weakest link in our topology was link from node 9 - node 10 and node 9 - node 11. As 
    observed from the graph. The minimum throughput is observed at 11.8 sec.

    -> Maximum throughput of the network is 2.2 Mbps achieved by CBR packets operating on UDP.



