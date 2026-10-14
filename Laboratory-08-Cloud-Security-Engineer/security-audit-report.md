# Security Audit Report

## The Principle of Least Privilege (PoLP)
PoLP means a user or account only gets the minimum access needed to do its job, nothing more. It is important for cloud user accounts because if an account gets hacked, the attacker can only do a little damage. It also protects against honest mistakes by users.

## Attack Surface
The attack surface of a virtual machine is all the places an attacker can try to get in. This includes open ports, running services, installed software, and user accounts. The fewer of these there are, the harder it is to attack the VM.

## Default Deny Policy
Default deny means all traffic is blocked unless I specifically allow it. It is safer because there are millions of possible attackers and I can never list them all. It is much easier to list the few things I trust than to chase every bad IP address.
