# Computer Networks

> Core networking concepts every software engineer must know — from OSI layers to how the web actually works.

---

## 1. What is a Computer Network?

A collection of interconnected devices that can communicate and share resources (data, files, internet access).

### Types of Networks
| Type | Range |
|---|---|
| **PAN** (Personal Area Network) | A few meters (Bluetooth) |
| **LAN** (Local Area Network) | A building/campus |
| **MAN** (Metropolitan Area Network) | A city |
| **WAN** (Wide Area Network) | Country/globe (e.g., the Internet) |

---

## 2. OSI Model (7 Layers)

A conceptual framework describing how data travels across a network.

```
7. Application   → HTTP, FTP, DNS, SMTP
6. Presentation  → Encryption, compression, data formatting
5. Session       → Session establishment, maintenance
4. Transport     → TCP, UDP (segments)
3. Network       → IP, routing (packets)
2. Data Link     → MAC addresses, switches (frames)
1. Physical      → Cables, signals, hardware (bits)
```

**Mnemonic:** *"All People Seem To Need Data Processing"*

---

## 3. TCP/IP Model (Practical, 4 Layers)

```
4. Application  → HTTP, FTP, DNS
3. Transport    → TCP, UDP
2. Internet     → IP, ICMP
1. Network Access → Ethernet, Wi-Fi
```

This is the model actually used on the Internet today.

---

## 4. TCP vs UDP

| TCP | UDP |
|---|---|
| Connection-oriented | Connectionless |
| Reliable (guarantees delivery) | Unreliable (best-effort) |
| Ordered delivery | No ordering guarantee |
| Slower (due to overhead) | Faster |
| Used for: web browsing, email, file transfer | Used for: video streaming, gaming, DNS, VoIP |

### TCP 3-Way Handshake
```
Client → SYN → Server
Client ← SYN-ACK ← Server
Client → ACK → Server
   (Connection Established)
```

---

## 5. IP Addressing

- **IPv4** – 32-bit address (e.g., `192.168.1.1`) → ~4.3 billion addresses
- **IPv6** – 128-bit address (e.g., `2001:0db8::1`) → solves IPv4 exhaustion

### Types of IP Addresses
- **Public IP** – globally unique, routable on the internet
- **Private IP** – used within local networks (e.g., `192.168.x.x`, `10.x.x.x`)

### Subnetting
Divides a network into smaller sub-networks using a **subnet mask** (e.g., `255.255.255.0`) to manage IP allocation efficiently.

---

## 6. DNS (Domain Name System)

Translates human-readable domain names (e.g., `google.com`) into IP addresses.

### DNS Resolution Flow
```
Browser → Local DNS Cache → ISP Resolver → Root Server →
TLD Server (.com) → Authoritative Server → Returns IP → Browser connects
```

---

## 7. HTTP / HTTPS

- **HTTP** – Application layer protocol for transferring web content (stateless)
- **HTTPS** – HTTP over TLS/SSL (encrypted, secure)

### Common HTTP Methods
| Method | Purpose |
|---|---|
| GET | Retrieve data |
| POST | Submit/create data |
| PUT | Update/replace data |
| PATCH | Partially update data |
| DELETE | Remove data |

### Common HTTP Status Codes
| Code | Meaning |
|---|---|
| 200 | OK |
| 201 | Created |
| 301 | Moved Permanently |
| 400 | Bad Request |
| 401 | Unauthorized |
| 403 | Forbidden |
| 404 | Not Found |
| 500 | Internal Server Error |
| 503 | Service Unavailable |

---

## 8. What Happens When You Type a URL and Hit Enter?

1. Browser checks cache for DNS record
2. DNS resolution → gets the IP address of the server
3. Browser establishes a **TCP connection** (3-way handshake) with the server
4. If HTTPS, **TLS handshake** happens (certificate exchange, encryption keys)
5. Browser sends an **HTTP GET request**
6. Server processes the request and sends back an **HTTP response**
7. Browser renders the HTML, fetches additional resources (CSS, JS, images)
8. Page is displayed

*(This is one of the most commonly asked SWE interview questions — know it thoroughly.)*

---

## 9. Client-Server vs Peer-to-Peer

| Client-Server | Peer-to-Peer (P2P) |
|---|---|
| Centralized server handles requests | No central authority; peers share directly |
| Easier to manage & secure | Harder to manage, more resilient |
| e.g., Web apps, APIs | e.g., BitTorrent, blockchain networks |

---

## 10. Load Balancing (Preview)

Distributes incoming network traffic across multiple servers to ensure reliability and performance.

- **Round Robin** – requests distributed sequentially
- **Least Connections** – sent to server with fewest active connections
- **IP Hash** – based on client IP for session persistence

*(Covered in more depth in `system-design-basics.md`)*

---

## 11. Common Networking Concepts

- **Firewall** – filters incoming/outgoing traffic based on security rules
- **Proxy Server** – intermediary between client and server (can cache, anonymize)
- **CDN (Content Delivery Network)** – distributes content across servers globally for faster access
- **VPN** – creates a secure, encrypted tunnel over a public network
- **NAT (Network Address Translation)** – maps private IPs to a public IP for internet access

---

## 12. Quick Revision Summary

- OSI has 7 layers; TCP/IP (practical model) has 4
- TCP = reliable, connection-oriented; UDP = fast, connectionless
- DNS converts domain names → IP addresses
- HTTPS = HTTP + encryption (TLS/SSL)
- Know the full flow: "What happens when you type a URL and press Enter"

---

## 13. Interview-Style Questions

1. Explain what happens when you type a URL into a browser and press Enter.
2. Difference between TCP and UDP — when would you use each?
3. What is the OSI model, and why is it useful?
4. Explain the TCP 3-way handshake.
5. What's the difference between HTTP and HTTPS?
6. What is DNS, and how does DNS resolution work?
7. What is a CDN, and why does it improve performance?
8. Explain the difference between a forward proxy and a reverse proxy.

---

**Previous file ←** `operating-systems.md`
**Next file →** `dbms-basics.md`
