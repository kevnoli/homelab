# Setting up Proxmox

Installing Proxmox is easy enough. If you've ever installed a Linux distro before, this feels very similar, just with a few extra steps around networking and storage.

I've worked with Proxmox clusters and other virtualized environments for a while, so nothing here was particularly new. Still, it's nice how quickly you can go from a bare-metal machine to a usable virtualization host with a web UI ready to go.

Download ISO, flash it, boot, next-next-finish and you're basically in.

## Storage

Storage took a bit more thought, mostly because of the "use whatever you already have" nature of this build.

I'm running a SATA expansion card to get more ports, and used some 3D printed 5.25" to 2.5" adapters to physically fit all the drives in the case. Nothing fancy, but it got everything mounted cleanly and without needing to buy a new chassis.

The drives themselves are a mix of SSDs and HDDs from previous upgrades, so not exactly uniform, which makes things a bit more interesting.

## ZFS (mostly)

I decided to lean mostly on ZFS for storage.

Main reasons were:
- built-in redundancy options
- snapshots (which are extremely useful in a homelab)
- have never tried it in production servers and it's about time

It's probably overkill for some use cases, and it does have a RAM cost, but even with 16GB it's been fine for what I'm doing.

I'm not going 100% ZFS for everything, but it's the default choice unless I have a reason not to use it.

## Post-install

After the initial install, there are a couple of small things I like to do right away.

First, I switched to the non-subscription repository. Although this is technically a production server (I do run experiments, but I also run a few private services that I'll write about later), just pointing it to the community repo and updating packages is enough.

I also ended up using a couple of scripts from the community-scripts project.

- [**PVE Post Install**](https://community-scripts.org/scripts/post-pve-install): it does a lot of things, but in my case I only used it to disable the subscription warning. I prefer keeping the system mostly “clean” and making changes intentionally rather than running a full automation script.

- [**PVE Cron LXC Updater**](https://community-scripts.org/scripts/cron-update-lxcs): this one adds a scheduled task to update all LXC containers weekly (Sunday at midnight). It’s a small thing, but it helps keep everything reasonably up to date without having to think about it.

That's about it for now. I'd rather keep things simple early on and automate as the need actually comes up.