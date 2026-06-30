<div align="center">
<img width="100%" src="https://capsule-render.vercel.app/api?type=waving&color=0:0F2027,50:203A43,100:2C5364&height=200&section=header&text=Priyanka%20Sagalgile&fontSize=42&fontColor=ffffff&fontAlignY=38&desc=Principal%20Site%20Reliability%20Engineer%20%C2%B7%20AWS%20%C2%B7%20Distributed%20Systems&descAlignY=58&descSize=16&animation=fadeIn"/>
Show Image
 
Show Image
 
Show Image

</div>
<br>

I don't get paged for outages I designed against. I get paged for the ones nobody thought to model — and then I make sure there's only ever one of those.



I build the layer between "it works on staging" and "it survives a region loss, a noisy neighbor, and a bad deploy landing during a traffic spike." Reliability isn't a postmortem habit here — it's a budget I plan, spend, and defend in design review, before code ships.

<br>
Operating numbers

These aren't claims on a badge — they're what I'm accountable for, quarter over quarter.

MetricWhere I hold the lineWhyMTTDMinutes — not customer ticketsIf a dashboard didn't catch it first, the dashboard is the defectMTTRSeconds to low single-digit minutesRecovery speed is a design decision made before the incident, not during itBlast radiusContained to one AZ, one regionA global outage means the isolation boundary was theoretical, not realToilDown, every quarterA runbook used three times this month should already be a controllerOn-call loadSustainable, sub-2-page nightsBurnt-out engineers write worse postmortems and ship worse fixes

<br>
Recent impact


Cut P1 incident volume by 60% by redesigning failure domains around cell-based isolation instead of retrofitting alerts onto a monolithic blast radius.
Brought region failover under 90 seconds through automated traffic shifting (Route 53 + Global Accelerator) tied to health-based, not heartbeat-based, signals.
Took 30+ services onto formal SLOs, replacing tribal-knowledge thresholds with error-budget policies that actually gate releases.
Ran recurring chaos experiments in production (AWS FIS, Gremlin) so failure modes get discovered on my schedule, not 3 a.m. on a Saturday.


<br>
Stack

<div align="center">
<img src="https://skillicons.dev/icons?i=aws,kubernetes,terraform,docker,grafana,prometheus,python,githubactions,linux,bash&theme=dark" />
</div>
<br>
Platform · EC2 · EKS · Lambda · RDS (Multi-AZ) · DynamoDB Global Tables · S3 · VPC · Route 53 · CloudFront · Global Accelerator
Infra-as-code · Terraform · AWS CDK
Observability · OpenTelemetry · CloudWatch · Prometheus · Grafana
Resilience engineering · AWS FIS · Gremlin · k6 · Locust
Delivery · Canary & blue/green rollouts · GitHub Actions

<br>
How I think about reliability

Availability isn't a number you chase after launch — it's a constraint you design against from the first architecture diagram. My approach, in order:


Define the failure domain first. If I can't draw the blast radius on a whiteboard, the system isn't ready to ship.
Instrument for detection, not just dashboards. Alerts should fire on symptoms customers feel, not on internal metrics that happen to be easy to graph.
Automate the recovery path, not just the runbook. A documented manual fix is a placeholder for a controller that doesn't exist yet.
Inject failure deliberately. If I haven't broken it in a game day, production will break it for me — at a worse time.
Treat on-call health as a reliability metric. A team paging itself to exhaustion is itself a system in degraded state.


<br>
<div align="center">
Open to conversations on distributed systems design, SRE practice, and AWS reliability architecture.

</div>
