# k3s-homelab

## 🤔 What?

This project serves as a code repository, documentation store, and scratchpad for moving some self-hosted workloads from a Proxmox box over to a k3s cluster.

## 🤡 Why?

I could sing the virtues of resilience and ease of recovery, but that would be lying. The truth would sound more like this:

1. Its cool (nerd),
2. Its fun (nerd),
3. Its good practice (nerd),
4. I have time (unemployed).

## 🗺️ Where are we now?

I'm at the very beginning, and front of mind is:

1. Spilling the weeks of thoughts I've had into this document.
2. Listing what services I want to run.
3. Listing any hard specifications I have.

## 📝 Scratchpad

Assume that these will find their way to purposeful sections once complete, and this section to be deleted. 

* I'm assuming desired services will be available as Docker containers.
    * Desired because this allows for hardware fault tolerance (service resilience).
* A path exists for exceptions, installing to bare-metal for mission-critical services (such as a NAS using a physical RAID controller).
    * This might be removed seeing as it would be out of the scope of the `k3s-homelab` project, but at this early stage is worth noting.
* At the moment all of my critical data is backed up off-site. I don't envision anything in use by these services to be critical, so a backup stratgegy to S3 Glacier might be enough.
* Hardware
    * Likely to be some variant of ex-enterprise micro form factor PC, eg [Dell OptiPlex 7020](https://www.dell.com/en-uk/shop/cty/pdp/spd/optiplex-7020-plus-micro/s09o7020mffp_vp?redirectTo=SOC&tfcid=43590050&gQT=1)
    * Why
        * Good parts availability
        * x86
        * Low power draw at idle, and efficient enough for projected needs under load
        * Available relatively cheap used
* Worker node OS
    * Ubuntu Server or NixOS
        * Ubuntu Server: Existing experience with it, easy setup, big distro name. 
        * NixOS: Declarative config seems a perfect fit for this task. I also just really want to use NixOS for something.

## 🔍 Services in Scope

At the moment, this will be a vague/bare list with explicitly defined services coming soon™️.

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
