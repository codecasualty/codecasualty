### Hi, I'm Subodh

I'm a senior backend engineer at [Clickpost](https://www.clickpost.ai), working remotely from India. I work on
the platform that predicts delivery dates for e-commerce orders: making APIs fast, keeping data
consistent, and finding out why something slowed down. Before that I was at [OnePlus R&D](https://www.oneplus.in)
and [TCS](https://www.tcs.com), and I did my M.Tech in Computer Science at [IIT Bombay](https://www.cse.iitb.ac.in).

Outside work I build things to understand how distributed systems actually behave when parts of them fail.

---

#### What I'm building

**[BeeDB](https://beedb.subodhlatkar.com)** is a replicated key-value store in Java 21 with a
Raft implementation I wrote by hand. It speaks the memcached protocol, writes every change to a
CRC-framed write-ahead log, and only acknowledges a write once a majority has it and it is on disk.

It runs live on three nodes at **[beedb.subodhlatkar.com](https://beedb.subodhlatkar.com)**. Every few
minutes one of them is killed on purpose, and you can watch the other two elect a new leader and the
dead one catch up. From the live server:

- about 1,500 writes a second with a p99 of 20 ms, on one 2-vCPU machine
- no acknowledged write lost in the crash tests
- 37 hours of continuous node kills after the latest fix, with the write-ahead log never above 200 KB

The bug behind that last fix was the most interesting one so far: a follower saved the same five
entries half a million times, until its log was 478 MB and it could no longer restart.

It started as John Crickett's [build your own memcached](https://codingchallenges.fyi/challenges/challenge-memcached/)
challenge.

#### Writing

[Building BeeDB](https://subodhlatkar.com/blogs/) is a short series for people who have never heard of Raft:

- [Why I built a database from scratch](https://subodhlatkar.com/blogs/why-i-built-a-database-from-scratch)
- [Following one write through BeeDB](https://subodhlatkar.com/blogs/following-one-write)
- [Writing to disk without lying](https://subodhlatkar.com/blogs/writing-to-disk-without-lying)
- [Mistakes that taught me the most](https://subodhlatkar.com/blogs/mistakes-that-taught-me-the-most)

#### Earlier work

The pinned repos below are mostly from IIT Bombay: a C++ key-value server over gRPC, my M.Tech thesis
(BPMN models to Petri nets), a shell for xv6, and a concurrency assignment on sequential consistency.

#### Things I work with

Java, Python, C++ · Django, Spring Boot, FastAPI · ScyllaDB, PostgreSQL, Redis, Kafka · Raft,
write-ahead logs, replication · Docker, Linux, AWS

#### Reading now

*In Search of an Understandable Consensus Algorithm* (Ongaro & Ousterhout) and, next, the Raft dissertation.

---

[subodhlatkar.com](https://subodhlatkar.com) · [LinkedIn](https://www.linkedin.com/in/subodh-latkar-b56b23209/) · [mail.subodhlatkar@gmail.com](mailto:mail.subodhlatkar@gmail.com)
