# 🔍 Services

WIP. Some items may be TBD with explicitly defined services coming soon™️.

1. [Home Assistant](https://www.home-assistant.io/)
    - What: Brain of a smart home.
    - Currently running as HA OS (Home Assistant OS) on a Raspberry Pi 4B 8GB.

2. [Pi-Hole](https://pi-hole.net/)
    - What: Network ad/telemetry/naughties blocking.
    - This function is currently being served by [AdGuard Home](https://adguard.com/en/adguard-home/overview.html), currently running as a [HA OS Add-on](https://www.home-assistant.io/addons)
    - AdGuard Home was not chosen in preference to Pi-Hole. It was just more convenient to install at the time with the existing environment.

3. [Unbound](https://www.nlnetlabs.nl/projects/unbound/about/)
    - What: Caching, recursive DNS resolver.
    - Would be configured as the upstream DNS server for Pi-Hole, ensuring DNS records stored are from authoritative DNS servers. [Good documentation here](https://docs.pi-hole.net/guides/dns/unbound/).

4. [Tailscale](https://tailscale.com/kb/1282/docker)
    - What: Mesh VPN service.

5. [Traefik Proxy](https://traefik.io/traefik/)
    - What: Reverse-proxy.
