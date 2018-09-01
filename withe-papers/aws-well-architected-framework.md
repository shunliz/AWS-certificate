# AWS Well-Architected Framework

## Introduction

---

The AWS Well-Architected Framework helps you understand the pros and cons of decisions you make while building systems on AWS

### Definitions![](/assets/fiverpillars.png)

### On Architecture

### General Design Principles

Stop guessing your capacity needs

Test systems at production scale

Automate to make architectural experimentation easier

Allow for evolutionary architectures

Drive architectures using data

Improve through game days

## The Five Pillars of the Well-Architected Framework

---

### Operational Excellence

#### Design Principles

Perform operations as code

Annotate documentation

Make frequent, small, reversible changes

Refine operations procedures frequently

Anticipate failure:

Learn from all operational failures

#### Best Practices

**Prepare:** AWS Config and AWS Config rules can be used to create standards for

workloads and to determine if environments are compliant with those standards

before being put into production.

**Operate ** Amazon CloudWatch allows you to monitor the operational health of a

workload.

**Evolve  **Amazon Elasticsearch Service \(Amazon ES\) allows you to analyze your log

data to gain actionable insights quickly and securely.

---

### Security

#### Design Principles

Implement a strong identity foundation

Enable traceability

Apply security at all layers:

Automate security best practices

Protect data in transit and at rest

Keep people away from data

Prepare for security events

#### Best Practices

1. Identity and Access Management

2. Detective Controls

3. Infrastructure Protection

4. Data Protection

5. Incident Response

---

### Reliability

#### Design Principles

Test recovery procedures

Automatically recover from failure:

Scale horizontally to increase aggregate system availability

Stop guessing capacity

Manage change in automation

#### Best Practices

1. Foundations

2. Change Management

3. Failure Management

---

### Performance Efficiency

#### Design Principles

Democratize advanced technologies

Go global in minutes

Use serverless architectures

Experiment more often:

Mechanical sympathy

#### Best Practices

1. Selection

2. Review

3. Monitoring

4. Tradeoffs

---

### Cost Optimization

#### Design Principles

Adopt a consumption model

Measure overall efficiency

Stop spending money on data center operations

Analyze and attribute expenditure

Use managed and application level services to reduce cost of ownership

#### Best Practices

1. Cost-Effective Resources

2. Matching supply and demand

3. Expenditure Awareness

4. Optimizing Over Time

---

**OPS 1 What factors drive your operational priorities?**

> _Operational priorities are the focus areas of your operations efforts. Clearly define and agree to_
>
> _your operations priorities to maximize the benefits of your operations efforts._

Evaluate business needs

Evaluate compliance requirements

Evaluate risk

**OPS 2 How do you design your workload to enable operability?**

> _The majority of the lifetime of a workload is typically spent in an operating state. Consider_
>
> _operations needs as a part of system design to help you enable long term sustainment of your_
>
> _workload._

Share design standards

Design for cloud operations e.g. elasticity, on-demand scalability, pay-as-you-go pricing, automation

Provide insights into workload behavior

Provide insights into customer behavior:

Implement practices that reduce defects, ease remediation, and improve flow:

Mitigate deployment risks

**OPS 3 How do you know that you are ready to support a workload?**

> _Evaluate the operational readiness of your workload, processes and procedures, and personnel_
>
> _to help you understand the operational risks related to your workload._

Continuous improvement culture

Share understanding of the value to the business:

Ensure personnel capability

Documented accessible governance and guidance

Use checklists

Use runbooks

Use playbooks

Practice recovery

**OPS 4 What factors drive your understanding of operational health?**

> _Define metrics for the evaluation of your workload and processes to help you understand_
>
> _operations effectiveness in supporting business outcomes. Capture and analyze metrics to gain_
>
> _visibility to processes and events so that you can take appropriate action._

Define expected business and customer outcomes

Identify success metrics

Identify workload metrics

Identify operations metrics

Established baselines

Collect and analyze metrics

Validate insights

Business-level view of operations

**OPS 5 How do you manage operational events?**

> _Prepare and validate procedures to respond to operational events to help you minimize their_
>
> _potential disruption to your workload._

Determine priority of operational events based on business impact

Processes for event, incident, and problem management

Process per alert

Identify decision makers

Defined escalation paths

Push notifications

Communicate status through dashboards

Process for root cause analysis





---

## 



