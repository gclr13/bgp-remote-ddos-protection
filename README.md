# BGP Remote DDoS Protection: Keep Your Network Online Without Buying a Single Box

It usually starts the same way. Traffic on your graph spikes. Not the good kind of spike — the kind where the line goes vertical and your monitoring dashboard turns into a Christmas tree at 2 a.m. Your upstream provider sends a polite email. Then a less polite one. Then they null-route your IP and your customers start sending you screenshots of timeouts.

If you've ever lived through that, you already know why people end up searching for **BGP remote DDoS protection**. You don't want a sales pitch. You want to know how it actually works, what it costs, and whether it'll hold up the next time someone points a few hundred Gbps at your network. That's what this article is about — and along the way I'll show you one provider that's been doing exactly this for over two decades: Sharktech.

## Why BGP Remote DDoS Protection Exists in the First Place

There are basically three ways to deal with a DDoS attack, and two of them are bad.

You can do nothing. The attack hits your servers directly, you go offline for hours or days, your upstream may null-route everything, and in the worst case they ask you to leave the network. Revenue gone, reputation dented.

You can build your own mitigation. This means buying scrubbing hardware, upgrading your transit, and hiring a network engineer who actually understands DDoS — which, depending on scale, can run into hundreds of thousands in hardware and potentially millions in network upgrades. Most organizations simply can't justify that.

Or you can use **BGP remote DDoS protection** — the option where you don't move your servers, don't buy hardware, and don't rewrite your infrastructure. You just announce your prefixes to a scrubbing provider over BGP, they clean the traffic, and they hand the good packets back to you over a GRE tunnel. That's the whole idea, and it's the one that makes sense for the vast majority of networks.

## How BGP Remote DDoS Protection Actually Works

The mechanics are easier than the marketing makes them sound. Here's the flow that Sharktech uses, which is representative of how serious BGP-based remote protection operates:

1. **A BGP session is established** between your network and the protection provider's routers. You announce your network prefixes (a minimum of a /24 block assigned to your company) to them.

2. **They announce your prefixes to the internet**, so inbound traffic headed for your network flows through their scrubbing infrastructure first.

3. **Clean traffic comes back to you over a GRE tunnel.** Importantly, this is asymmetric — only ingress (incoming) traffic is routed through the scrubber. Your outbound traffic still goes out your normal path. That cuts the latency impact roughly in half compared to symmetric tunneling.

4. **When an attack is detected**, the provider's firewalls filter the malicious traffic in real time and only the legitimate traffic makes it back through the GRE tunnel to you. No migration, no downtime, no equipment to install.

The requirements are modest: a /24 IP block assigned to your company, a system that can run BGP and a GRE tunnel (a soft router is fine — no expensive hardware router required), and ideally an MTU of at least 1550 with your upstream to account for GRE overhead.

## Why This Matters More in 2026

If you're on the fence about whether remote DDoS protection is worth it, the recent numbers should settle it. DDoS attack volume has gone industrial. Reports for 2026 show network-layer attacks up over 500% year over year, "mega attacks" above 100 Gbps climbing sharply, and a record-setting 31.4 Tbps attack logged in Cloudflare's latest threat report. Hyper-volumetric attacks grew by more than 700%.

Translation: the threat isn't theoretical and it isn't slowing down. If your network faces the public internet, the question isn't whether you'll get hit — it's whether you'll have filtering in place when you do.

## Where Sharktech Fits In

Sharktech has been running DDoS mitigation since 2003. They operate their own network (AS46844) out of five data centers — Los Angeles, Las Vegas, Denver, Chicago, and Amsterdam — with over 1.1 Tbps of global connectivity. The thing that separates them from a lot of "DDoS-protected" hosts is that their entire network was engineered around the assumption that attacks are a daily operating condition, not an edge case.

Their **Remote Network DDoS Protection** is the BGP/GRE/Anycast service for networks that live outside their data centers. So if you're an ISP, a hosting provider, or a business running your own infrastructure somewhere else, you can plug into Sharktech's scrubbing without migrating anything. You set up the BGP session, establish the GRE tunnel, announce your prefixes, and you're protected.

What I like about how they describe it: the traffic routing is asymmetric (ingress only), which is the smart design choice — it minimizes the latency penalty that symmetric tunneling imposes. And because they spread attacks across all their data centers using their full bandwidth, they can absorb large volumetric hits that would saturate a single scrubbing location.

A couple of real-world data points worth noting: a gaming operator on Sharktech's network reports regularly absorbing 3–8 Gbps attacks where "servers never skip a beat." Independent reviewers consistently highlight that the protection is structural, not a marketing checkbox.

## Sharktech DDoS Protection Options at a Glance

Here's a comparison of the protection tiers available, from the included baseline up to the full BGP remote service:

| Protection Option | Mitigation Capacity | Pricing | Best For | Get Started |
| --- | --- | --- | --- | --- |
| Standard DDoS Protection (included) | 60 Gbps per IP | Free with all hosted services (VPS, dedicated, cloud) | Anyone already hosting with Sharktech | [Get protected hosting](https://portal.sharktech.net/aff.php?aff=1611&carttpl=vps) |
| 100Gbps DDoS Protection add-on | 100 Gbps per IP | $39/month per single IP | High-traffic dedicated or colocation servers needing extra headroom | [Add 100Gbps protection](https://bit.ly/SharKTech) |
| Remote Network DDoS Protection (BGP/GRE/Anycast) | Up to 1 Tbps across all data centers | Custom — contact sales for a tailored plan | ISPs, hosting providers, and networks outside Sharktech's DCs | [Request a remote protection quote](https://bit.ly/SharKTech) |

The pricing philosophy here is the refreshing part. There are no bandwidth overage bills, no opaque tiered pricing that needs a finance degree to decode, and no "introductory price" that triples at renewal. The 100Gbps add-on at $39/month per IP is a flat rate — and compared to enterprise alternatives that start in the thousands per month, it's a fraction of the cost.

## Active Promotions Worth Knowing

If you're going to pull the trigger, a few current promo codes stack on top of the standard flat pricing:

- **Y5YET1Z9EK** — 10% recurring lifetime discount on Cloud Virtual Servers and Bare Metal Dedicated Servers. For Amsterdam-based resources, the same code unlocks 20% recurring savings.
- **WHTFALL** — 33% recurring discount on Cloud Virtual Data Center services.
- **Long billing cycles save automatically**: quarterly gets you 25% off, semi-annual 35%, and annual 50% — applied at checkout, no coupon hunting required.

For reference, the Smart VPS entry plan (which includes 60Gbps DDoS protection standard) drops to about $3.98/month on annual billing. That's not a typo — it's the same protection layer included in everything from a $4 VPS up to enterprise bare-metal.

## What to Watch Out For

Being honest about the limitations, because they matter:

- **No money-back guarantee.** All sales are final. There's no refund window, so go in knowing what you need. The only exception is a billing dispute within 30 days, and even that resolves to account credit if approved.
- **Not beginner-friendly.** The dashboard assumes you know what CPU cores, NVMe allocation, and bandwidth mean for your workload. There's no cPanel by default and no hand-holding wizard. Support is competent and fast (sub-15-minute responses in independent tests), but the baseline assumption is that you speak server admin.
- **Remote protection is custom-quoted.** Unlike the hosted services with published flat rates, the BGP remote DDoS protection plan is tailored to your network size and prefix count, so you'll need to reach out for pricing.

None of these are dealbreakers for the audience this product is actually built for — network operators, sysadmins, ISPs, and game-hosting teams who already know their way around BGP. But if you're expecting a managed, point-and-click experience, that's not what this is.

## Who BGP Remote DDoS Protection Is Really For

The short version: if you operate a network that faces the public internet and you can't afford to be knocked offline for hours, BGP remote DDoS protection is the practical answer. You keep your existing infrastructure, your existing IPs, your existing transit — you just route ingress through a scrubbing layer that's been hardened against exactly the kind of attacks that are setting records in 2026.

Sharktech's version of that is worth a serious look because the fundamentals are right: a 20-year track record, their own network (not someone else's transit resold), asymmetric GRE routing to keep latency low, multi-terabit distributed scrubbing, and flat pricing that doesn't punish you later. The combination of an included 60Gbps baseline, a $39/month 100Gbps add-on, and a custom-quoted full BGP remote service covers everyone from a small hosting customer to a regional ISP.

If you want to see how it'd map onto your specific network, the quickest move is to reach out and have their team scope a plan against your prefix list — that conversation costs nothing and it's the only way to get accurate remote protection pricing for your actual setup.

👉 [Talk to Sharktech about BGP remote DDoS protection for your network](https://bit.ly/SharKTech)

## Frequently Asked Questions

**What is BGP remote DDoS protection?**
It's a service where you establish an external BGP session with a scrubbing provider and announce your network prefixes to them. They attract your inbound traffic, filter out attack traffic at their scrubbing centers, and return clean traffic to you over a GRE tunnel. You don't need to move servers or buy hardware.

**What do I need to set it up?**
A /24 IP block assigned to your company, a system capable of running BGP and a GRE tunnel (a soft router works — no expensive hardware router required), and ideally an MTU of at least 1550 with your upstream provider to accommodate GRE overhead.

**How big an attack can Sharktech's remote protection handle?**
Their data centers are each connected with at least 1 Tbps, and their layered approach spreads attacks across all locations and upstream providers. They report having yet to receive an attack they couldn't mitigate.

**Do I have to migrate my servers to Sharktech?**
No. That's the whole point of the remote service — no migration required. Your infrastructure stays where it is; only your inbound traffic is routed through the scrubbing layer.

**How fast does mitigation kick in?**
The system is designed to detect and reroute automatically when an attack is identified, with their security team monitoring 24/7. You can also choose always-on scrubbing rather than on-demand activation.

👉 [Get a custom remote DDoS protection quote from Sharktech](https://bit.ly/SharKTech)
