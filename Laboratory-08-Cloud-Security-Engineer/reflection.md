# Mission Reflection

**1. How does a host-based firewall protect a server if the network perimeter is breached?**
A host-based firewall protects the server itself. Even if someone gets inside the network, they still cannot reach the server's services unless a rule allows it. It is like having a lock on every room, not just on the front gate.

**2. Why is managing open ports important for the attack surface?**
Every open port is a possible door for attackers. Each open port runs a service, and a service can have bugs or weak passwords. When I only left ports 22 and 8080 open, there were fewer ways to attack the server. This is like the Principle of Least Privilege, but for the network.

**3. Why is it dangerous to leave a database port like 3306 open to the public?**
Bots scan the internet all the time looking for open database ports and try to guess passwords. If they get in, they can steal, change, or delete customer data. This can cause data breaches, legal trouble, and loss of trust. A database should only be reachable from the app server or through a private network or VPN.

**4. How did this mission change my view on how easily a server can be compromised?**
Before, I thought a server was safe if nobody knew about it. Now I understand that a new server with no firewall is exposed right away, and automated attacks can find it in minutes. One forgotten setting can leave it wide open. A firewall only takes a few commands, so there is no reason to skip it.

**5. How does my GitHub portfolio look with eight missions?**
My portfolio now has eight laboratory folders, from Laboratory 01 to Laboratory 08. Each one has its own README, documents, and screenshots. Together they show my progress from learning basic cloud ideas to deploying, monitoring, and securing a live server. It looks organized.
