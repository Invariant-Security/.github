# Invariant Security

We build security tools that sit at the end of the delivery pipeline and answer one question before every deploy: **is this safe to ship?**

Invariant audits Linux servers and containers against public standards (CIS Benchmarks), checks known vulnerabilities against what is actually exploited in the wild (CISA KEV, FIRST EPSS), and looks at the real context of the host: is the vulnerable code running, is it listening on the network. Only proven or unexcludable risk blocks the deploy. Everything else stays visible in the report.

🌐 [invariantsec.org](https://invariantsec.org)

## Our principles

These are the rules every Invariant feature has to follow.

1. **Block with precision, hide nothing.**
   A deploy is blocked only by proven risk, or by risk we cannot rule out where it matters most (actively exploited vulnerabilities and critical checks). Every other finding is shown in the report, without stopping the pipeline.

2. **Reports a human can act on.**
   Every blocking reason says, in plain language, what is wrong, why it matters and what to do next. The technical evidence is always there, one click away, never in the way.

3. **A failure of the tool never approves a deploy.**
   If Invariant cannot run, cannot read the target or has stale data, the pipeline stops. Silence is never treated as a pass.

4. **Your data stays with you.**
   Invariant runs inside your environment. Nothing about the audited systems leaves it. The only data we receive is license metadata. Anything beyond that is opt-in and started by you.

5. **Deterministic and auditable.**
   Same input, same decision. No AI in the decision engine. Every run records the versions, data hashes, catalog and target it used, so "why was this blocked?" can be answered months later.

6. **Exceptions are explicit.**
   Accepting a risk is a recorded decision, with an owner, a reason and an expiry date. Never a silent ignore.

7. **The scanner must not become the breach.**
   Invariant does not collect secrets, command lines or environment variables, treats everything read from the target as untrusted, and runs with the least privilege it needs.

8. **We assess, you change.**
   Invariant never alters the environment it audits. It tells you how to fix a problem; you decide when and how to apply it, because you know your infrastructure.

9. **Predictable in the pipeline.**
   Works offline, with versioned vulnerability data and controlled data age, so the same build does not get a different answer because the internet changed.

## Standards and data we build on

- [CIS Benchmarks](https://www.cisecurity.org/cis-benchmarks), referenced by our own check IDs
- [CISA Known Exploited Vulnerabilities](https://www.cisa.gov/known-exploited-vulnerabilities-catalog) (CC0)
- [FIRST EPSS](https://www.first.org/epss/)
- [Trivy](https://github.com/aquasecurity/trivy) (Apache 2.0) for vulnerability matching
