# Lab 6 : Configuration of dynamic routing protocols: RIP, EIGRP, OSPF, BGP

## Objective
- To understand the concepts of dynamic routing protocols.
- To learn how to configure dynamic routing protocols (RIP, EIGRP, OSPF, BGP) on network devices using CLI.

## Theory
- **Dynamic Routing Protocols:** Dynamic routing protocols automatically determine the best path for data packets based on current network conditions. They allow routers to exchange information about the network topology and adapt to changes in real time.

- **RIP (Routing Information Protocol):** RIP is a distance-vector routing protocol that uses hop count as its metric. It is easy to configure but limited to smaller networks because it has a maximum hop count of 15.

- **EIGRP (Enhanced Interior Gateway Routing Protocol):** EIGRP is an advanced distance-vector protocol that considers multiple metrics, such as bandwidth, delay, load, and reliability. It is more efficient than RIP and can handle larger networks.

- **OSPF (Open Shortest Path First):** OSPF is a link-state routing protocol that uses Dijkstra's algorithm to calculate the shortest path to each network. It is highly scalable and ideal for large enterprise networks.

- **BGP (Border Gateway Protocol):** BGP is a path-vector protocol used for routing between autonomous systems on the Internet. It enables the exchange of routing information across different networks and is the backbone protocol of the Internet.

## Procedure
1. In Cisco Packet Tracer, create a network topology with multiple routers and networks.
2. Assign IP addresses to all devices and configure basic settings such as IP addresses, subnet masks, and gateways.
3. Configure RIP on the routers using the following commands in CLI mode:
   ```
   Router(config)# router rip
   Router(config-router)# version 2
   Router(config-router)# network [network_address]
   ```

   **Router 1:**
   ```
   Router> enable
   Router# configure terminal
   Router(config)# router rip
   Router(config-router)# version 2
   Router(config-router)# network 192.168.1.0
   Router(config-router)# network 10.0.0.0
   Router(config-router)# no auto-summary
   ```

   **Router 2:**
   ```
   Router> enable
   Router# configure terminal
   Router(config)# router rip
   Router(config-router)# version 2
   Router(config-router)# network 192.168.2.0
   Router(config-router)# network 10.0.0.0
   Router(config-router)# no auto-summary
   ```
4. Configure EIGRP on the routers using the following commands in CLI mode:
   ```
   Router(config)# router eigrp [AS_number]
   Router(config-router)# network [network_address] [wildcard_mask]
   ```

   **Router 1:**
   ```
   Router> enable
   Router# configure terminal
   Router(config)# router eigrp 100
   Router(config-router)# network 192.168.1.0 0.0.0.255
   Router(config-router)# network 10.0.0.0 0.0.0.255
   Router(config-router)# no auto-summary
   ```

   **Router 2:**
   ```
   Router> enable
   Router# configure terminal
   Router(config)# router eigrp 100
   Router(config-router)# network 192.168.2.0 0.0.0.255
   Router(config-router)# network 10.0.0.0 0.0.0.255
   Router(config-router)# no auto-summary
   ```

5. Configure OSPF on the routers using the following commands in CLI mode:
   ```
   Router(config)# router ospf [process_id]
   Router(config-router)# network [network_address] [wildcard_mask] area [area_id]
   ```

   **Router 1:**
   ```
   Router> enable
   Router# configure terminal
   Router(config)# router ospf 1
   Router(config-router)# network 192.168.1.0 0.0.0.255 area 0
   Router(config-router)# network 10.0.0.0 0.0.0.255 area 0
   ```

   **Router 2:**
   ```
   Router> enable
   Router# configure terminal
   Router(config)# router ospf 1
   Router(config-router)# network 192.168.2.0 0.0.0.255 area 0
   Router(config-router)# network 10.0.0.0 0.0.0.255 area 0
   ```

6. Configure BGP on the routers using the following commands in CLI mode:
   ```
   Router(config)# router bgp [AS_number]
   Router(config-router)# neighbor [neighbor_IP_address] remote-as [neighbor_AS_number]
   Router(config-router)# network [network_address] mask [subnet_mask]
   ```

   **Router 1:**
   ```
   Router> enable
   Router# configure terminal
   Router(config)# router bgp 65001
   Router(config-router)# neighbor 10.0.0.2 remote-as 65002
   Router(config-router)# network 192.169.1.0 mask 255.255.255.0
   ```

   **Router 2:**
   ```
   Router> enable
   Router# configure terminal
   Router(config)# router bgp 65002
   Router(config-router)# neighbor 10.0.0.1 remote-as 65001
   Router(config-router)# network 192.168.2.0 mask 255.255.255.0
   ```

7. Verify the routing configuration by using ping requests between devices on different networks. Use the following command in CMD mode:
   ```
   ping [destination_IP_address]
   ```

## Observations
- Successful ping responses indicate that the dynamic routing protocols are correctly configured, allowing communication between different networks.

## Output

<table>
   <tr>
      <td align="center">
         <img src="RIP-ping.png" alt="RIP Configuration CLI" width="800" />
         <br />Fig: Ping result using RIP
      </td>
      <td align="center">
         <img src="EIGRP-ping.png" alt="EIGRP Configuration CLI" width="800" />
         <br />Fig: Ping result using EIGRP
      </td>
   </tr>
   <tr>
      <td align="center">
         <img src="ospf-ping.png" alt="OSPF Configuration CLI" width="800" />
         <br />Fig: Ping result using OSPF
      </td>
      <td align="center">
         <img src="BGP-ping.png" alt="BGP Configuration CLI" width="800" />
         <br />Fig: Ping result using BGP 
      </td>
   </tr>
</table>

## Conclusion
- This lab helped us understand and configure dynamic routing protocols—RIP, EIGRP, OSPF, and BGP—on network devices using the CLI.  
- We learned how dynamic routing allows networks to adapt automatically to changes, ensuring efficient and reliable communication.  
- Proper setup of these protocols is crucial for maintaining optimal routing paths and seamless connectivity in complex networks.

