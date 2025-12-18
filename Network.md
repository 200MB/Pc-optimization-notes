# TCP Optimizer

**TCP Optimizer** is a utility provided by **SpeedGuide** that exposes a large set of Windows registry and networking tweaks through a single UI.

Because most of these tweaks affect **TCP**, you should not expect noticeable improvements in **UDP-based traffic**.  
Most online games primarily use UDP, so gains for gaming are usually limited.

---

## Settings Explained

### TCP Window Auto-Tuning  
**Disabled**  
- Forces the smallest possible TCP receive window  
- Minimizes latency at the cost of reduced throughput

---

### Windows Scaling Heuristics  
**Disabled**  
- Dynamically overrides TCP auto-tuning based on connection statistics  
- Often counterproductive and can lead to inconsistent behavior

---

### Congestion Control Provider  
**CTCP / CUBIC / NewReno**  
- Controls how TCP reacts to congestion and packet loss  
- **NewReno**: Lowest latency in my experience  
- **CUBIC**: Optimized for throughput and high-bandwidth links  
- **CTCP**: Alternative approach, sometimes better on lossy connections

---

### Receive Side Scaling (RSS)  
**Disabled**  
- Distributes network processing across CPU cores  
- Can introduce stuttering if the CPU or scheduler struggles

---

### Receive Segment Coalescing (RSC)  
**Disabled**  
- Reduces CPU interrupts by merging packets  
- Increases latency, which is undesirable for real-time workloads

---

### Explicit Congestion Notification (ECN)  
**Disabled**  
- Designed to reduce packet loss without dropping packets  
- Poor router support in practice  
- Added noticeable latency during gaming in my case

---

# Group policy DSCP marking 
**Basically it adds a priority mark on each packet sent.**

Naturally this means that your packets will be delivered first and processed faster.

**Requirements**
- Must have a QOS compliant router which respects your markings.

I tried it but couldn't feel any difference in latency.
To enable marking, go to group policy -> User Configuration -> Windows Settings -> Policy-Based Qos 

Right Click and select **create new policy**, give it any name and input 46 as DSCP value which is a decimal representation of EF (expedited forwarding) which is the highest priority.

Rest of the settings are intuitive to setup. 


