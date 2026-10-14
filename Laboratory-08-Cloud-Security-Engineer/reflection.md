<div align="center">

# Mission Reflection
### Laboratory 08: The Cloud Security Engineer

**CCM101 – Cloud Computing** 

</div>

---

| | |
|---|---|
| **Name** | *Blessie C. De Guzman* |
| **Mission** | Securing a server with UFW |
| **Tools Used** | KillerCoda · Docker · Nginx · UFW |

---

## ✍️ 

> *"Security is not a product you buy; it is a continuous process you maintain."*

Before this mission, I thought securing a server was complicated. After finishing it, I learned that good security starts with a few simple commands and a careful way of thinking.

A host-based firewall protects the server itself, not just the network around it. Even if an attacker gets past the network perimeter, the firewall on the server still checks every connection and blocks anything that is not allowed. It is like putting a lock on every room in a building, not only on the front gate.

Managing open ports is important because every open port is a possible door into the server. Each port runs a service, and a service can have bugs or weak passwords. By keeping only SSH and port 8080 open, I made the attack surface smaller. This is also why leaving a database port like 3306 open to the public internet is dangerous in a real company. Bots scan the internet all day looking for open databases and try to guess passwords. If they get in, they can steal, change, or delete customer data, which can lead to data breaches, legal trouble, and loss of trust. A database should only be reachable by the app server or through a private network.

This mission also changed how I see server security. I used to think a server was safe if nobody knew about it. Now I know that a new server with no firewall is exposed right away, and automated attacks can find it within minutes. One forgotten setting is enough to leave it wide open.

My GitHub portfolio now has eight laboratory missions, and each one has its own README, documents, and screenshots. Together they show my growth from learning basic cloud ideas to deploying, monitoring, and securing a live server. It looks organized, and I am proud to show it. In the end, I learned that security is not something I do once, but something I keep doing.

---

<div align="center">

🔒 *Default Deny · Least Privilege · Smaller Attack Surface* 🔒

</div>
