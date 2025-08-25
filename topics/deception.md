# Deception

## Overview / What is it?
Cyber Deception: Beyond Defense
Traditional security builds walls. Cyber deception builds illusions — fake systems, data, and signals that confuse attackers, expose their tactics, and buy defenders time. It’s a cutting-edge research field at the intersection of cybersecurity, psychology, and AI. By studying deception, we learn not only how to defend better, but also how attackers think and adapt in the wild.


Or:
Hackers, Welcome to the Maze
 What if your server isn’t what it seems?
 Cyber deception plants decoys, traps, and digital illusions to lure attackers into chasing shadows. They think they’re winning — but we’re the ones collecting their secrets. By studying deception, we learn not only how to defend better, but also how attackers think and adapt in the wild.

## Real World Applications & Relevance

We look at cyber deception from the defensive side, so not at how the attacker uses deception, but how defenders can use deception. There are multiple different methods, such as honeypots, honeytokens, Moving Target Defense and tarpits, to name a few.
Deception methods can be used to enhance Intrusion Detection Systems or to collect Cyber Threat Intelligence. [Greynoise](https://www.greynoise.io/) is a service that deploys sensors on the web an logs interactions and categorized the type of attack. [Canarytokens](https://canarytokens.org/nest/) are a collection of different fake information that can be used to rack attackers behaviours. One example is a fake credit card, that can be used in fake shops to see how and when they abuse the credit card informations of their victims.

## Challenge

1. "Can you spot the trap in SSH?"

Attackers love weakly configured SSH. Imagine this:

An attacker tries 8 passwords and finally succeeds with root:root.

They change the SSH settings so anyone can log in as administrator.

Now the system is wide open.

👉 Task for you: Look at this (fake) SSH config snippet — what setting would you change to stop the attacker?

```
# /etc/ssh/sshd_config
PermitRootLogin yes
PasswordAuthentication yes
AllowUsers *
```

2. Fingerprint a Honeypot
- Pick a honeypot of your choice
- Deploy the honeypot and the real service locally on your machine
- Interact with both services and observe differences - can you detect the honeypot with as little interaction as possible?
- (It is also possible to look at the source code of the honeypot to find possible ways to identify the honeypot)

