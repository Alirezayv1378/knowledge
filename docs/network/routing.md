# Routing Fundamentals

### What is a Router?
A **router** is a network device that forwards packets between networks. It examines the destination IP address in a packet's header and decides the next hop (where to send it next).
- Each host (device) is attached directly to one router, called its **default router** or **first-hop router**.
- Routers connect multiple networks and maintain **routing tables** to know paths to destinations.

### Routing vs. Forwarding
- **Forwarding**: The action of a router looking up its routing table and sending a packet to the next hop. This is per-packet and happens in the **data plane**.
- **Routing**: The process of building and updating routing tables across the network. This is network-wide and happens in the **control plane**.

### The Internet as a Graph
The internet can be modeled as a **graph** where:
- **Nodes**: Routers (or sometimes hosts/subnets).
- **Edges**: Physical links (e.g., fiber optic cables) between nodes.
- Each edge has a **cost** (metric), such as distance, bandwidth, delay, or monetary cost. For simplicity, beginners can think of cost as the "length" or "hop count" (number of routers traversed).

Routing answers: "If I have a packet for IP address X, where do I send it next?" The goal is often the **least-cost path** (shortest path based on metrics).

#### Example: Simple Network Graph
Consider a small network with routers A, B, C, D:
```
A --(cost 1)-- B --(cost 2)-- C
|              |
(cost 3)       (cost 1)
|              |
D -------------(cost 4)
```
- From A to C: Possible paths: A-B-C (cost 1+2=3) or A-D-B-C? Wait, no direct A-D-B. Actual paths: A-B-C (3) or A-D-(via cost 4 to B? No, assume D connects to C too? Let's clarify.
Better simple example:
```
A --1-- B --2-- D
 \     /
  3   1
   \ /
    C
```
- Shortest path A to D: A-B-D (cost 3) or A-C-B-D (longer). No, A-C-D? Assume C--2--D.
Use text: Paths from A:
- To B: A-B (1)
- To C: A-C (3) or A-B-C? If B-C is 1, then A-B-C=2 (shorter!).

Routing algorithms find these shortest paths.

### Static vs. Dynamic Routing
- **Static Routing**: Manually configured routes (e.g., by admin). Simple for small networks but doesn't adapt to changes (e.g., link failure).
- **Dynamic Routing**: Routers automatically learn and update routes using algorithms. Adapts to failures but more complex.

## Routing Algorithms

Routing algorithms compute paths. They are classified as:
- **Intra-domain (Interior Gateway Protocols - IGP)**: Within one organization (AS), e.g., RIP, OSPF.
- **Inter-domain (Exterior Gateway Protocols - EGP)**: Between organizations, e.g., BGP.

Main types: Distance Vector (DV) and Link State (LS). A third is Path Vector (used in BGP).

### Distance Vector (DV) Algorithms
DV is a **decentralized routing algorithm**. Each router knows only about its neighbors and iteratively learns about the whole network.
- Based on the **Bellman-Ford algorithm**.
- Each router maintains a **routing table**: | Destination | Cost | Next Hop |
- Routers exchange tables with **directly connected neighbors** periodically (e.g., every 30 seconds) or on changes.
- Update rule: If neighbor Y says it can reach Z with cost C, and my link to Y is D, then my cost to Z via Y is D + C. Choose the minimum over all neighbors.
- Routers share least-cost estimates to all known destinations but **do not know the full topology**—they trust neighbors.

#### Pros and Cons
- Pros: Simple, low overhead for small networks.
- Cons: Slow convergence (time to stabilize after changes), **count-to-infinity problem** (loops form if link fails, costs increase forever until max hop limit, e.g., 15 in RIP).

#### Count-to-Infinity Example
Network: A--1--B--1--C
- Initially, A to C: via B, cost 2.
- If B-C fails, B thinks cost to C is infinity, but if A still advertises old cost 2, B updates to 3 (via A), A then to 4 (via B), and so on—infinitely increasing.

Solutions: **Split horizon** (don't advertise back to source), **poison reverse** (advertise infinity back), hold-down timers.

#### Example Protocol: RIP (Routing Information Protocol)
- Uses hop count as cost (max 15 hops).
- UDP-based, simple for small networks.

### Link State (LS) Algorithms
LS is a **centralized/global routing algorithm**. Each router learns the entire network topology.
- Based on **Dijkstra's shortest path algorithm**.
- Steps:
  1. **Discover neighbors**: Send "hello" packets.
  2. **Measure link costs**: To neighbors.
  3. **Flood link state packets (LSPs)**: Broadcast costs of directly connected links to all routers (using sequence numbers to avoid duplicates).
  4. **Build topology graph**: Each router assembles the full map.
  5. **Compute shortest paths**: Run Dijkstra from itself to all others.

- Each router knows the **full topology** and computes independently.

#### Dijkstra's Algorithm Example
Graph:
```
A --2-- B --3-- D
 \1    /4
  C --5-- E
```
From A:
- Initialize: Dist to A=0, others infinity.
- Visit closest: A, update B=2, C=1.
- Visit C (closer than B): Update from C? C to E=5, so E=1+5=6; C to B? No link.
- Visit B: B to D=3, so D=2+3=5.
- And so on.

#### Pros and Cons
- Pros: Fast convergence, no looping issues, supports multiple metrics.
- Cons: Higher overhead (flooding), more CPU/memory for large networks.

#### Example Protocols
- **OSPF (Open Shortest Path First)**: Common IGP, supports areas for scalability.
- **IS-IS (Intermediate System to Intermediate System)**: Similar to OSPF, used in large ISPs.

### Comparison of DV vs. LS
| Aspect        | Distance Vector          | Link State                        |
| ------------- | ------------------------ | --------------------------------- |
| Knowledge     | Local (neighbors only)   | Global (full topology)            |
| Communication | With neighbors only      | Broadcast to all                  |
| Computation   | Iterative, distributed   | Centralized (Dijkstra per router) |
| Convergence   | Slower, prone to loops   | Faster, loop-free                 |
| Examples      | RIP, EIGRP (enhanced DV) | OSPF, IS-IS                       |

### Path Vector Algorithms
Similar to DV but includes the full path (sequence of nodes/ASes) to avoid loops. Used in inter-domain routing (see BGP below).

## Autonomous Systems (ASs)

The internet is divided into **Autonomous Systems (ASs)**: Groups of routers under single administrative control (e.g., an ISP, company, university).
- Each AS has an **AS Number (ASN)** (16-bit or 32-bit unique ID).
- **Intra-AS routing**: Within an AS, using IGP like OSPF/RIP. All routers run the same protocol and share info.
- **Inter-AS routing**: Between ASs, using EGP like BGP.
- **Gateway routers** (border routers): In an AS, handle traffic to/from outside ASs.
- Why ASs? Scalability—internet has millions of routers; grouping reduces complexity.

#### Example
- AS 100: Your home ISP.
- AS 200: Google.
- Traffic from your PC to Google goes intra-AS in 100, then inter-AS via BGP, then intra-AS in 200.

## Border Gateway Protocol (BGP)

BGP is the **de facto inter-domain routing protocol** for the internet. It's a **path vector protocol** (extension of DV).
- Allows ASs to advertise **IP prefixes** (blocks of IP addresses, e.g., 198.51.100.0/24 means 256 addresses starting at 198.51.100.0).
- Advertisements include **AS_PATH**: Sequence of ASNs traversed (e.g., AS_PATH: 100 200 300) to detect loops.
- BGP sessions: **eBGP** (external, between ASs) vs **iBGP** (internal, within AS).

#### How BGP Works
- ASs "scream" their prefixes: "I own 198.51.100.0/24, reach me via this path."
- Routers build **BGP tables** with prefixes, paths, attributes.
- Without BGP, ASs would be isolated.

#### BGP Attributes and Path Selection
When multiple paths to a prefix:
1. **Highest LOCAL_PREF**: Local preference (admin-set, e.g., prefer customer links).
2. **Shortest AS_PATH**: Fewer AS hops.
3. **Lowest origin type**: IGP < EGP < Incomplete.
4. **Lowest MED** (Multi-Exit Discriminator): Hint for entry point.
5. **eBGP over iBGP**.
6. **Lowest IGP cost** to next hop (using intra-AS metric).
7. **Oldest path**.
8. **Router ID** tie-breaker (lowest IP).

#### Additional Definitions
- **IP Prefix**: CIDR notation, e.g., /24 means first 24 bits fixed, last 8 variable.
- **Route Aggregation**: Combining prefixes to reduce table size (e.g., 10.0.0.0/16 covers many /24s).
- **Hot Potato Routing**: Send traffic out of AS as quickly as possible (low IGP cost).

#### End-to-End Example (Expanded)
**Scenario: Sending from Host in AS100 to Server in AS200**
```
AS100 (OSPF intra)          AS200 (OSPF intra)
  R1 (host attached) -- R2 -- R3 (gateway) --eBGP-- R4 (gateway) -- R5 -- Server
          |IGP links|               |IGP links|
```
1. **BGP Advertisement**:
   - AS200 advertises prefix 198.51.100.0/24 (server's subnet) via eBGP to R3.
   - R3 receives: Prefix: 198.51.100.0/24, AS_PATH: 200.
   - R3 shares via iBGP inside AS100.
   - All in AS100 install route.

2. **Intra-AS Routing**:
   - OSPF in AS100: R1 learns shortest path to R3 (e.g., R1-R2-R3, cost 2).

3. **Packet Forwarding (Data Plane)**:
   - Host sends packet to R1 (default router).
   - R1: Looks up table, next hop R2.
   - R2: Next hop R3.
   - R3: BGP says next AS 200, so forward to R4.
   - In AS200: OSPF routes R4 to R5 to server.

#### Another Example: Multi-Homed AS
AS300 connected to AS100 and AS200.
- AS300 advertises prefix to both.
- Traffic to AS300 might go via shorter AS_PATH or policy (e.g., LOCAL_PREF).

## Route Hijacking and Security

**Route hijacking** (BGP hijacking): When an AS falsely advertises a prefix it doesn't own, diverting traffic.
- Impacts: Traffic interception, blackholing, or MITM attacks.

### Types
1. **Origin Hijack**: Attacker AS claims to own the prefix (e.g., fake AS_PATH starting with attacker's ASN).
   - Example: In 2008, Pakistan Telecom hijacked YouTube prefixes, causing global outage.

2. **Subprefix Hijack**: Announce a more specific prefix.
   - Real: 10.0.0.0/16 (65k addresses).
   - Attacker: 10.0.5.0/24 (256 addresses, subset).
   - BGP prefers **longest prefix match** (more specific), so traffic to 10.0.5.x goes to attacker, even if AS_PATH longer.

3. **Path Hijack**: Fake shorter AS_PATH to attract traffic.

### Prevention
- **RPKI (Resource Public Key Infrastructure)**: Cryptographic validation of prefix ownership using ROAs (Route Origin Authorizations).
- **BGPSEC**: Signs AS_PATH for path validation (not widely deployed).
- **MANRS (Mutually Agreed Norms for Routing Security)**: Best practices for ISPs.
- Monitoring tools: BGPmon, Route Views.

#### Example: 2023 Incident
In recent years, misconfigurations (not always malicious) have caused hijacks, like AWS routes being leaked.
