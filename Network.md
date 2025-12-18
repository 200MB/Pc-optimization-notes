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

---

# Wireless vs Wired  
**Which one is better and which one to choose**

---

## Wired Connection

The **most stable** and **fastest** option available.

- Completely unaffected by radio interference  
- Lowest possible latency  
- Ideal for gaming, competitive play, and any latency-sensitive workload  

If you can run a cable, this is always the best choice.

---

## Wireless Connection

Much easier to set up and offers wider coverage, but comes with trade-offs.

- Sensitive to environmental changes  
- Less stable than wired  
- Higher and more inconsistent latency  

The two main problems are **congestion** and **interference**.

---

### Congestion vs Interference

- **Congestion**  
  Too much data flowing through the same network path  
  - Example: family members streaming, downloading, or uploading heavily  

- **Interference**  
  Disruptive radio signals from other devices and networks  
  - Often unavoidable  
  - Extremely noticeable during gaming  

---

## Wireless Frequencies

Most Wi-Fi networks operate on one of these frequency bands.

---

## 2.4 GHz (Avoid if possible)

The most common frequency and often the default on many routers.

- Extremely sensitive to environmental interference  
- Very limited channel availability  
- Poor choice for gaming  

> There is **nothing you can do on your PC** to fully stabilize a bad 2.4 GHz connection.

To gamers still stuck on this band: your pain is real.

---

### Why 2.4 GHz is so bad

- Operates on **only 12 channels**
- **Only 3 non-overlapping channels**: **1, 6, and 11**
- If a neighbor uses overlapping channels → **packet loss**
- You have no control over this

---

### Common 2.4 GHz Interference Sources

- **Other Wi-Fi networks**
- **Bluetooth devices** (Bluetooth also uses 2.4 GHz)  
  - Bluetooth headphones + Wi-Fi = local interference  
- **Microwaves**  
  - Routers near microwaves will suffer severe disruption  

Standing near or placing a router close to these devices will noticeably degrade performance.

---

## 5 GHz (Strongly Recommended)

If your router and device support it, upgrade immediately.

- Far more stable than 2.4 GHz  
- Significantly higher throughput  
- Much lower interference  
- Gaming becomes almost lag-free  

### Why it’s better

- **165+ channels** available  
- Much lower chance of sharing channels with neighbors  
- Less crowded spectrum overall  

The difference between 2.4 GHz and 5 GHz is massive.

---





