+++
title = "Homelab tour 1"
date = "2024-03-14"
author = "Janszczyrek"
+++
Hi, in my very first blog post ever, I'm very excited to show you how and what is being hosted in my homelab. Let's take a look around!

## Hardware
In the past, when SBC's weren't as efficient and cheap as now I had been using an old Dell Optiplex PC for some time. Then I realised that I could lower my power bill as well as save some precious space in my room by switching to something smaller. I wanted to try something less popular than the Raspberry Pi so I decided to give the *Orange Pi Zero 3* a try.
It has a quad-core Allwinner H618 ARM CPU paired with 4GB of LPDDR4 RAM. As for peripherals it has a USB 2.0 port and most importantly a single gigabit NIC. I'm aware that those specs aren't spectacular, but almost any modern smartphone lying around in a drawer will perform better, but considering my current needs it's my sweet spot. This server could also be used as a Wake-On-LAN server in the future to turn on more powerful servers when needed.

{{< figure src="/img/orangepi.jpg" alt="Orange pi" position="center" caption="Here I host my stuff :)" captionPosition="center" >}}

## Software
As for the operating system, I'm using the Debian Bookworm image provided by Orange Pi. Mostly all of the services that I'm running are docker containers which are set up with docker compose. For now it's sufficient.

## Connectivity
Sadly, my ISP doesn't offer static public IP addresses and all inbound traffic is being blocked so I decided to use the [Tailscale](https://tailscale.com/) service. It's a VPN solution built as a set of wireguard tunnels between each connected device. They offer a free tier up to 3 users and 100 devices, definitely check it out!

## What am i hosting?

### Pi-hole
[Pi-hole](https://pi-hole.net/) is a network-wide ad blocker that transforms how your entire home network handles unwanted traffic. By acting as a DNS sinkhole, this lightweight application intercepts and blocks advertisements. Pi-hole creates a centralized defense that protects every connected device, from smartphones and laptops to smart home gadgets. The magic happens at the DNS level, meaning you get ad-blocking coverage without installing separate extensions or apps. I also use it for convenient access to my other services by their domain name. Additional lists of unwanted domains could be attached. For example CERT publishes a warning list for domains that were flagged as phishing. However, the lists aren't updated automatically - you need to manually update them from web UI from time to time or create a script that runs `pihole -up` systematically.

### Smokeping
[SmokePing](https://oss.oetiker.ch/smokeping/) is a powerful network latency monitoring tool that provides incredible visual insight into your network's performance and reliability. Unlike simple ping tests, SmokePing creates detailed, long-term graphs that track network latency, packet loss, and jitter across multiple targets. By probing network endpoints at regular intervals, it generates graphs that help you diagnose connectivity issues and understand network quality trends. That way - when my internet connection is down, I can tell who's fault it is :).

### Uptime Kuma
Similar to Smokeping this tool allows you to monitor various types of services. [Uptime Kuma](https://uptimekuma.org/) can monitor multiple types of services - ranging from HTTP, Docker containers to specific TCP ports. It comes with a notification system and a more modern looking UI than Smokeping. I'm using it to healthcheck this website.

### Immich
Digital album for all your photos and videos. Its UI has a Google Photos feel which looks really good. It provides additional features like searching photos by describing them and can recognise a person on a photo. [Immich](https://immich.app/) comes with a native mobile app with options for automatic backups and a web interface. Recommended!

### Nextcloud
To go self-hosted solution for cloud storage. [Nextcloud](https://nextcloud.com/) functions like a personal GDrive or Dropbox, allowing file synchronization across devices and sharing them via a link. It comes with apps for various systems so you can use them on all your devices.

### Readeck
It allows you to save interesting articles for reading later. [Readeck](https://readeck.org/en/) also provides an interface for reading them directly from web interface - you can highlight important ideas and also export selected articles as an e-book to read it on your e-ink reader.

### FreshRSS
Enables you to aggregate many different RSS channels into multiple feeds. [FreshRSS](https://freshrss.org/index.html) provides a category feature that allows organizing feeds into topical groups. It supports filtering by tags and many more. If you are keen on reading news the old way or trying to reduce time spent scrolling across many different news platforms you should check it out! 

## Conclusion
Thank you for reading this post! I hope you learned something new. In my upcoming posts, I'll be writing about how I can make my setup more secure, as well as how I organized my home LAN network - so stay tuned!