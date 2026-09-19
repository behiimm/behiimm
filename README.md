## Behnaz Moradimehr

Security analyst in Berlin. Network detection and packet analysis, and the
documentation that usually goes missing around them.

CompTIA Security+ (SY0-701) · CompTIA Network+ (N10-008) · Google IT Support Certificate

---

### [PCAP-Annotations](https://github.com/behiimm/PCAP-Annotations)

Five packet-capture investigations, eight Suricata rules, two tshark-based tools.

Every rule is tested against every capture — 8 × 4 — not just the one it was written for:

```
PASS  120 alerts, 0 false positives across 32 rule/capture combinations.
      Every rule fired on its own capture and stayed silent on the other three.
```

`make verify` rebuilds the synthetic captures from seeded generators, downloads the
public ones and checks their SHA256, then reproduces that matrix from scratch.

Each case also states **what the rule does not catch and how to evade it**, because a
signature nobody can bypass usually means the test was too easy. Covers T1046,
T1110.001, T1040, T1078, T1071.001, T1071.004 and T1048.003.

A few things I ran into that were worth writing down:

- Suricata keeps threshold counters per thread, so the same file gave 14, 15 and 15
  alerts on three runs. The tests pin `--runmode single`.
- Beacon scoring uses coefficient of variation, which has no unit — so a 60-second
  beacon and a 6-hour beacon score the same. It refuses to score a flow with fewer
  than 8 samples, because three gaps can look regular by accident.
- Suricata cannot count distinct ports, so a port-scan rule cannot tell a scan from
  many connections to one port. That check lives in tshark instead.

---

### Currently

Working through TryHackMe, and learning German (A1, studying at VHS towards B1)
alongside the security work.

Full unrestricted work authorisation in Germany — no sponsorship required.

📍 Berlin · [LinkedIn](https://www.linkedin.com/in/behi-moradi-28719440b)
