# Starting the homelab: choosing a hypervisor

When I started putting together my homelab, the first real decision was how I wanted to run services on the server.

There were a few options:

- Just install a Linux distro (like Debian or Ubuntu) and run everything directly on it with Docker.

- Use something like [TrueNAS](https://www.truenas.com/truenas-community-edition/) or [Unraid](https://unraid.net/) and run apps through it.

- Go with a hypervisor so I could split things into VMs and containers.

The first option would definitely work, and honestly it's probably the simplest. But I knew that once the lab started growing, isolating services would become useful. Being able to spin up a VM, break something, and just roll it back is pretty valuable when you're experimenting.

That's what pushed me toward running a hypervisor. I ended up choosing [Proxmox Virtual Environment](https://www.proxmox.com/en/), which is open-source and handles both full VMs (KVM) and lightweight containers (LXC) from a web interface.

Could I have done everything manually on plain Linux? Sure. In fact, that's basically what Proxmox is doing underneath anyway. But the management layer and tooling save a lot of time.

# The server itself

The hardware is a bit of a Frankenstein build, mostly assembled from parts I've accumulated over the years.

The core of it is:

- Xeon E5-2630L v3

- 16GB ECC RAM

- Machinist MR9A motherboard

All three came from AliExpress.

The rest is even more improvised:

- the GTX 1050 GPU and case were bought used

- the PSU used to power my main PC before I upgraded it

- the drives are a mix of SSDs and HDDs that I've replaced over time in other machines

It's definitely not a shiny rack server, but that's part of the fun.

# Not doing everything the hard way

Even though you can configure everything manually inside Proxmox and the guest operating systems, I quickly discovered [tteck's helper scripts](https://github.com/community-scripts/ProxmoxVE). Besides scripts for quickly deploying common services, there are also some really useful management scripts that handle things like updates, kernel cleanup, and other small maintenance tasks. They're incredibly convenient and saved me a lot of time when getting the lab running.

Sadly, the creator tteck passed away last year, which was a big loss for the community. His work still lives on in the repo and continues to help a lot of people get started.

So while I still like understanding what's happening under the hood, I'll admit that for many services I just run one of those scripts and move on.