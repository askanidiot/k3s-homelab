# 📝 Scratchpad

Assume that these will find their way to purposeful sections once complete, and this doc to be deleted. 

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
    * Ubuntu Server: Existing experience with it, easy setup, big distro name. 
    * NixOS: Declarative config seems a perfect fit for this task. I also just really want to use NixOS for something.
    * Talos: Keeps coming up in research, "minimal, hardened, and immutable". Anecdotally a great fit for a k8s worker node.