# Headframe

**On-premise monitoring and management for ASIC mining farms. Own the box. Own the data.**

Headframe is an open-source alternative to hosted mining-farm monitoring. It runs on a server you own, on the same network as your miners, and never needs the cloud. The name is the steel structure that stands over a mine shaft and runs the hoist: the thing that watches the whole mine and brings things up.

## Status

Building in public. Nothing here is usable yet. The first milestone is a collector that polls ASIC miners every 30 seconds, on stock firmware and third-party firmware such as Braiins OS and LuxOS, and stores live hashrate, temperatures, fan speeds and power in TimescaleDB. First drivers target the hardware on the bench; more firmware families follow as drivers are contributed.

## Why

- **No subscription.** One box, one purchase. Updates and support are optional, and the software keeps working without them.
- **No cloud.** Collector, database and dashboard all live at the site. If the internet link drops, Headframe keeps recording and alerting; nothing is lost.
- **Your data.** It never leaves hardware you own. The code that touches it is right here.
- **Owner's Window.** Each tenant of a hosting site can reach the real web interface of their own miners through the appliance, behind the appliance's login and audit log. The host decides who gets it.
- **An API that returns values.** Live hashrate, temps, fans and watts per miner, not just status filters.

## Planned architecture

- **Collector** polls miners over their native APIs (cgminer-style TCP, firmware gRPC or REST where offered) and writes locally first.
- **Storage** is PostgreSQL with TimescaleDB.
- **API** is FastAPI.
- **Dashboard** covers fleet view, site map, alerts, power and curtailment.
- **Tenant gateway** is a per-tenant WireGuard profile or reverse proxy with a firewall allow-list of that tenant's miners.
- **HQ aggregator** (optional) for operators with more than one site.

## License

AGPL-3.0. Use it, change it, run it. If you run a modified version as a service for others, publish your changes.

## Maintainer

Kent Workman ([@kentworkman](https://github.com/kentworkman)). Started October 2026.
