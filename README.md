<div align="center">

# Priyanka Pravin Sagalgile

### Principal Site Reliability Engineer · AWS · Distributed Systems @ Scale

<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&size=20&duration=2800&pause=1200&color=58A6FF&center=true&vCenter=true&width=620&lines=I+don't+fix+outages.+I+make+them+statistically+unlikely.;Multi-region+by+default.+Single+points+of+failure+by+accident.;Error+budgets+gate+releases%2C+not+vibes.;Every+incident+ships+a+fix%2C+not+just+a+writeup." alt="typing-svg" />

[![LinkedIn](https://img.shields.io/badge/Priyanka_Sagalgile-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/priyanka-sagalgile)

</div>

<br>

> Anyone can restart a process at 3am. That's the symptom, not the job. The job is designing the system so that failure mode never earns a page in the first place. I work where "it works on staging" becomes "it survives a region loss, a noisy neighbor, and a bad deploy — at the same time, during a traffic spike."

<br>

## 🧬 How I'd architect a system I'd actually trust

```
                         ┌────────────────────┐
                         │   Route 53 (DNS)    │
                         │   health-based       │
                         └──────────┬───────────┘
                    ┌────────────────┴────────────────┐
                    ▼                                  ▼
          ┌──────────────────┐               ┌──────────────────┐
          │  Region: us-east  │               │  Region: us-west │
          │   ──ACTIVE──      │◄─────────────►│   ──ACTIVE──     │
          │   EKS + ASG        │   replica     │   EKS + ASG      │
          └─────────┬──────────┘               └─────────┬────────┘
                    │                                     │
          ┌─────────┴──────────┐               ┌─────────┴────────┐
          │  RDS (multi-AZ)     │               │  RDS (multi-AZ)  │
          │  DynamoDB Global     │               │  DynamoDB Global │
          └──────────────────────┘               └────────────────────┘

  blast radius   →  one region, never two
  failover time  →  < 90s, automated, zero humans in the loop
  chaos-tested   →  monthly, on purpose, before customers find it for us
```

<br>

## 🔥 Incident log — the kind that taught me something

<table>
<tr>
<td width="90"><img src="https://img.shields.io/badge/SEV--1-D32F2F?style=for-the-badge"/></td>
<td>

**Manual failover took 40 minutes under pressure.**
Five whys landed on the real root cause: *the system trusted a human more than automation.* Shipped active-active multi-region failover, DNS-driven, zero manual steps.
**Result → next failure of this class: resolved in 88 seconds. Nobody paged.**

</td>
</tr>
<tr>
<td width="90"><img src="https://img.shields.io/badge/ORG--WIDE-F9A825?style=for-the-badge"/></td>
<td>

**Every team had its own definition of "down."**
Incident severity was being argued live, on the bridge, instead of decided in advance. Built a standardized SLO framework with error budgets wired into release gates — adopted across 30+ services.
**Result → the argument moved from the incident channel to the design review, where it belongs.**

</td>
</tr>
<tr>
<td width="90"><img src="https://img.shields.io/badge/SILENT-455A64?style=for-the-badge"/></td>
<td>

**P1s were being discovered by customers before they were discovered by us.**
Stood up scheduled chaos engineering against the failure domains most likely to actually break.
**Result → 60% drop in P1 volume.** Failures still happen — just in a test, on a Tuesday, with a coffee in hand.

</td>
</tr>
</table>

*(Illustrative numbers — swap in your real incident data. The format is the point: every claim has a root cause and a receipt.)*

<br>

## 📡 What I optimize for, not what I claim

| Signal | Target | Why it's not negotiable |
|---|---|---|
| **MTTD** | minutes, not customer tickets | if a dashboard didn't catch it, the dashboard is the bug |
| **MTTR** | seconds to low minutes | recovery speed is a design decision, made *before* the incident |
| **Blast radius** | one AZ / one region, contained | a global outage means the isolation boundary was theoretical |
| **Toil** | trending down, every quarter | if it's the third runbook this month, it should be code |
| **On-call load** | sustainable, sub-2-page nights | burnt-out engineers write worse postmortems |

<br>

## 🛠️ Stack

<div align="center">
<img src="https://skillicons.dev/icons?i=aws,kubernetes,terraform,docker,grafana,prometheus,python,githubactions,linux,bash&theme=dark" />
</div>

<div align="center">

`EC2` `EKS` `Lambda` `RDS (multi-AZ)` `DynamoDB Global Tables` `S3` `VPC` `Route 53` `CloudFront` `Global Accelerator` · `CDK` · `OpenTelemetry` `CloudWatch` · `AWS FIS` `Gremlin` `k6` `Locust` · canary & blue/green delivery

</div>

<br>

<div align="center">

```
$ echo $PHILOSOPHY
"Hope is not a strategy. Redundancy, tested under real load, is."
```

</div>

