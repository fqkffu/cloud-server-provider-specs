# Cloud Server Providers: What $3 and $74 a Month Actually Buy, Which Specs Decide the Fit, and the Charges That Appear After Checkout (Full Plan Table)

Cloud server pricing has two useful reference points right now. A 1 GB instance with 1 core, 10 GB of storage and 250 Mbit/s starts at €3 a month on UpCloud. A 16 vCPU box with 16 GB of RAM, 320 GB of RAID-10 SSD and 15 TB of monthly transfer starts at $74 a month on SpinServers. Everything in between comes down to two questions: how many cores you genuinely use at once, and how much data you push out the door each month.

This article works through the SpinServers KVM plan line one tier at a time, flags the limits that only show up in the plan footnotes, and puts three European providers beside it on the same criteria so you can see where the money goes.

> **Quick pick:** if you need many cores, a 1 Gbps port and 8 TB or more of transfer per month, the SpinServers 16 vCPU / 16 GB / 320 GB plan at $74.00/month is the tier worth pricing first. If your site runs on 1 GB of RAM, a €3–€5 plan elsewhere costs a fraction of that. 👉 [See the 16 vCPU / 16 GB plan at $74/mo](https://bit.ly/Spinservers)

## Every SpinServers KVM plan, side by side

Five configurations are listed on the KVM VPS page. All of them include a 1 Gbps network port and one IPv4 plus one IPv6 address.

| Plan | vCPU / RAM | Storage | Monthly transfer | Price (USD/mo) |
| --- | --- | --- | --- | --- |
| Simple Application Server | 6 vCPU / 8 GB DDR4 | 120 GB RAID-10 SSD | 8 TB | Quoted per config ·  [Check the 6 vCPU price](https://bit.ly/Spinservers) |
| Simple Application Server | 8 vCPU / 8 GB DDR4 | 160 GB RAID-10 SSD | 10 TB | Quoted per config ·  [Check the 8 vCPU price](https://bit.ly/Spinservers) |
| KVM 12 vCPU | 12 vCPU / 12 GB | 160 GB SSD | 10 TB | Quoted per config ·  [Check the 12 vCPU price](https://bit.ly/Spinservers) |
| KVM 16 vCPU (Xeon) | 16 vCPU / 16 GB DDR4 | 320 GB RAID-10 SSD | 15 TB | **from $74.00** ·  [See the $74 plan](https://bit.ly/Spinservers) |
| Advanced Application Server | 32 vCPU / 32 GB | 500 GB SSD | 20 TB | Quoted per config ·  [Check the 32 vCPU price](https://bit.ly/Spinservers) |

The 16 vCPU tier is the only one that publishes a starting figure in the plan copy. The rest are quoted when you configure them, so confirm the monthly number and the billing term on the order page before you pay rather than assuming the smaller boxes scale down in a straight line.

### What's in the box, and what you have to ask for

| Item | Status on the plan listing |
| --- | --- |
| IPv4 | 1 included |
| IPv6 | 1 included |
| Network port | 1 Gbps |
| Storage type | RAID-10 SSD |
| Port 25 (SMTP) | **Closed by default**; open by ticket with justification, and requests can be refused |
| Backups / snapshots | Not stated in the plan specs |
| Uptime SLA | Not stated on the pages reviewed |
| Refund window or trial | Not stated on the pages reviewed |

That second table matters more than the first for some buyers. A closed port 25 rules out running a mail server or a relay that depends on SMTP out of the box. You can request it, but approval is discretionary, so anyone whose workload depends on sending mail should clear it with support before paying, not after.

## The vCPU-to-RAM ratio is the real spec sheet

Look at the shapes rather than the core counts. Six cores with 8 GB, sixteen with 16 GB, thirty-two with 32 GB. That 1:1 ratio is not how general-purpose cloud plans are usually cut, where 4 cores typically pair with 16 GB and the pricing reflects per-core speed.

What you get at this ratio is concurrency. Thirty-two cores with 32 GB of RAM suits workloads that keep many threads parked or lightly busy: container hosts running a dozen small services, build and CI agents, scrapers, game servers with a lot of idle players, batch jobs that spend time waiting on network. If your application is bound by single-thread clock speed (a heavy PHP stack, a big MySQL instance with slow queries, anything where one core does the work), a 32-core box will not feel faster than an 8-core one, and you would be buying the wrong thing.

Hetzner draws the same line on its own product pages, splitting shared-resource plans from dedicated-vCPU plans. Shared is pitched at personal sites, blogs, small databases and low-to-moderate traffic. Dedicated vCPUs are pitched at high-traffic sites, large databases, game servers, machine learning and bulk data processing. The core count printed on a plan tells you how much parallelism the host is willing to schedule, not how fast any one core runs. Ask which one your workload needs before comparing prices.

## What the monthly price leaves out

Transfer is where this plan line earns its money, and also where a light user overpays. Eight to twenty terabytes a month on a 1 Gbps port is generous for a single site and roughly right for a media origin, a backup target or a download host. If you push 200 GB a month, you are buying headroom you will never use. Ask support what happens past the cap, since overage pricing and throttling behaviour are not spelled out in the plan specs.

Backups are the other unknown. UpCloud shows how this line item is usually priced: daily backups for 24-hour retention add **10%** of the server plan price, a week of retention adds **20%**, four weeks plus daily adds **40%**, and a year of monthly, weekly and daily restore points adds **60%**. An on-demand backup runs €0.056 per GB per month. On a €28 plan, the year-tier backup alone turns into roughly €44.80 a month if you take the top option. Whatever SpinServers charges for snapshots, budget for it as a percentage rather than assuming it is free. 👉 [Check current SpinServers plan pricing and options](https://bit.ly/Spinservers)

Billing granularity changes the arithmetic too. UpCloud's Starter and Premium plans bill 24/7/365 until you delete the server, so powering a box off for three weeks saves nothing. Its Cloud Native plans bill CPU and RAM only while the machine is powered on, but storage and IP addresses keep billing because they stay allocated. A short-lived test environment can cost five times more than expected on the first model and a fifth on the second. SpinServers bills monthly, which is simpler to plan around but less forgiving if you only need a box for a week.

Addresses are a smaller line item, but they add up in fleets. UpCloud charges €3.47 a month for a floating IP and the same for each additional public IPv4. SpinServers includes one of each family in the plan.

## Three providers on the same criteria

No links here, just the verified numbers so you can see the spread.

| Provider | Entry price | Stated SLA | Billing model | Notes |
| --- | --- | --- | --- | --- |
| SpinServers | $74.00/mo for 16 vCPU / 16 GB / 320 GB / 15 TB | Not published on the pages reviewed | Monthly | 1 Gbps port, 1 IPv4 + 1 IPv6 included, port 25 closed by default |
| UpCloud | €3/mo (1 GB / 1 core / 10 GB / 250 Mbit/s) to €28/mo (16 GB / 4 cores / 50 GB / 500 Mbit/s) | 99.99% on Starter; 99.999% on GPU and Private Cloud | Hourly; Starter and Premium billed 24/7 until deleted | Zero egress fees, 45-second deploys, GPU from €0.58/h |
| Hetzner | Prices on the plan cards reviewed were placeholder text, so no figure is quoted | 99.9% with defined credits | Shared and dedicated tiers | Germany, Finland, Singapore, USA; ISO/IEC 27001 and BSI C5; one shared tier marked unavailable |
| hosting.de | €4.90/mo (2 vCore) to €29.90/mo (8 vCore) | 99.9% | Monthly | Germany only, NVMe, 5 TB fair-use traffic, Linux only |

Two things stand out. UpCloud's entry price is roughly a twenty-fifth of SpinServers' published tier, and the two are not substitutes. The €3 box has one core, 10 GB of storage and a 250 Mbit/s port. The other has sixteen cores and 15 TB of transfer. Compare entry prices across providers and you learn nothing; compare price per core, per GB of RAM and per TB of transfer and the picture sorts itself out.

The SLA column is where the quiet money sits. 99.9% allows about 43 minutes of downtime in a 30-day month. 99.99% allows about 4.3 minutes. 99.999% allows 26 seconds. Hetzner and hosting.de sit at the first number, UpCloud's Starter at the second, UpCloud's GPU and Private Cloud tiers at the third. If you are paying for the top tier, that is what the premium buys. If a provider publishes no SLA at all, you have no credit to claim when the box disappears for an hour.

A note on UpCloud's figures: they were taken from the pricing page dated 20 October 2026, and that page states that Cloud Server plans, Standard and Archive Block Storage and Windows Server licences are being repriced on **16 November 2026**. Treat the euro amounts as a snapshot, not a standing quote.

## When the cheapest tier is the wrong purchase

The lowest plan in any lineup is a test environment, not a production box. Hetzner says as much about its own cost-optimised shared tier, describing it as suitable for low CPU usage and medium traffic. hosting.de's cheapest tier is two vCores with RAM and SSD figures that vary by tier and, on the page reviewed, were not published in the summary.

Four situations where paying less costs more:

- **Mail.** Port 25 is closed on every SpinServers VPS by default. A mail server needs the port open and a clean IP reputation, and neither comes with a $5 plan anywhere.
- **Single-threaded apps.** A busy WordPress site with a heavy plugin stack wants clock speed. Six cheap cores will lose to two fast ones.
- **Anything with a compliance requirement.** Hetzner's German and Finnish data centres hold ISO/IEC 27001, and the company holds BSI C5. hosting.de is ISO 27001 certified and hosts only in Germany under GDPR. If a customer contract names a certification, a provider that lists one is the shorter conversation.
- **Windows or custom ISO installs.** hosting.de supports Linux only out of the box and asks you to contact sales about Windows or custom images. Confirm the OS list before you commit anywhere.

## Questions worth answering before you pay

**Is the transfer allowance hard or soft?** The plan specs list 8, 10, 15 or 20 TB a month without stating overage rates. Ask.

**Do snapshots cost extra?** They are not listed as included. Get the number in writing.

**Can I get port 25 opened?** You can request it with a justification, and the provider reserves the right to refuse.

**Is there a refund window?** None is published on the plan pages. Confirm the cancellation terms before the first invoice, especially on a monthly plan where one payment is the whole commitment.

**How long does setup take?** Not stated in the plan copy. Ask, and if a migration deadline depends on it, get it in writing.

## How to decide

Match the plan shape to the workload, then check the extras.

- A blog, a staging site or a single small app on 1 GB of RAM: the €3–€5 tier at UpCloud or hosting.de is the correct purchase. A $74 box is four times the machine you need.
- Many small services, CI runners, containers, scrapers, small game servers: the 6 vCPU / 8 GB or 12 vCPU / 12 GB tiers, where parallelism is the point and per-core speed is not.
- A media origin, download host or anything with real outbound traffic: the 16 vCPU / 16 GB tier at $74.00/month with 15 TB of transfer and a 1 Gbps port is the tier where the included bandwidth stops being a rounding error.
- Databases and anything latency-sensitive: buy fewer, faster cores and a dedicated-vCPU plan rather than a high core count on shared hardware.

Two things to confirm on the order page before you enter card details: the currency and whether tax is added at checkout, and whether the monthly price renews at the same figure or steps up after the first term. Monthly billing removes most of the renewal risk, but only if the term really is month to month.

If the 16 vCPU configuration is the one that matches your workload, start there rather than at the bottom of the range and upgrading twice. 👉 [Start with the 16 vCPU / 16 GB plan](https://bit.ly/Spinservers)
