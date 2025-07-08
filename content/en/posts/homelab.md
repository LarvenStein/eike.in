+++
title = 'HomeLab'
summary = 'My HomeLab – what’s running on it and how it evolved over time'
date = 2025-07-08
showDate = true
showAuthor = true
featureimage = 'https://media.eike.in/data/website/current-rack.jpg'
showHero = true
heroStyle = 'big'
showTableOfContents = true
tags = ['Home Lab']
showReadingTime = true
showWordCount = true
+++

I felt the urge to share my HomeLab with the world – so here’s a little write-up covering the hardware, services, and how it all came to be. Enjoy reading :)

## History
{{< timeline >}}

{{< timelineItem icon="skull-crossbones" header="The beginnings" badge="2021 (?)">}}
I’m honestly not sure when I got started with all of this – probably 2021 (when I registered the HomeLab domain) or maybe 2022 (based on a timestamp of a photo I found in my gallery).

It all began with two Raspberry Pi 3B units. One was running Discord music bots, and the other had an external HDD and hosted a Nextcloud instance using <a href="https://nextcloudpi.com/" target="_blank">NextcloudPi</a>. Looking back, I’m kind of surprised I didn’t lose any data with that setup 🥸

{{< figure
    src="/images/homelab/Homelab-21.jpg"
    alt="The two Raspberry Pis, my HomeLab back then"
    caption="My old HomeLab, hidden behind a cabinet"
    >}}
{{< /timelineItem >}}

{{< timelineItem icon="bomb" header="More stuff" badge="2022 (?)">}}
After learning about Home Assistant and Pi-hole, I wanted to self-host those too. I didn’t have any spare Pis left, so I repurposed an old Trekstor notebook and installed Debian on it.  
I installed the services "bare metal" – directly on the OS – which, fun fact, isn’t even officially supported by Home Assistant anymore.

<br>  
The notebook got a USB Ethernet adapter and a permanently attached power cable. <b>The battery stayed inside 🔥</b>

<br>  
At some point I realized that I couldn’t run both Nextcloud and Home Assistant on the same ports using the same public IP. I ignored this issue for way too long until I finally decided to set up a reverse proxy.

{{< mermaid >}}
graph LR;
N[Nextcloud]<-->R[NGINX Proxy];
H[HomeAssistant]<-->R;
R<-->I[Internet]
{{< /mermaid >}}
{{< /timelineItem >}}

{{< timelineItem icon="wand-magic-sparkles" header="A new home" badge="2023">}}
As more and more services joined my HomeLab, it became increasingly impractical to run them on weak standalone machines. So I decided to convert my old PC into a server.

The setup: Intel Core i7-3770, 20 GB DDR3 RAM, 2× 2 TB HDDs and 2× 240 GB SSDs, all grouped into pools. I chose Unraid as my OS – the demo seemed user-friendly and worked well for me.

<br>  
Migrating Home Assistant and Pi-hole was a breeze thanks to backups. NextcloudPi, however, gave me a hard time – I had to reformat my drives to BTRFS and eventually gave up trying to transfer it. I just reinstalled it from scratch and uploaded the data manually.

<br>  
Everything except Home Assistant is now running in Docker :)
{{< /timelineItem >}}

{{< timelineItem icon="lock" header="Backups!" badge="2024">}}
Eventually I realized that the RAID on my server didn’t count as a real backup, so I started building a proper backup system.

<br>  
At first, I used <a href="https://duplicati.com/" target="_blank">Duplicati</a> to push weekly backups to an old NAS I had lying around at home.

As the amount of critical data on the server grew, I figured it was time to add a second, off-site backup location. I managed to get another old NAS and set it up at my grandma’s place, including a permanent VPN connection to her network.

To save power, I configured a schedule to turn the NAS on only on Sundays for the backups. I also installed a remote power switch in case I ever need to boot it manually.

{{< gallery >}}
  <img src="/images/homelab/o-nas-remote-on-1.jpg" class="grid-w50 md:grid-w33 xl:grid-w25" />
  <img src="/images/homelab/o-nas-remote-on-2.jpg" class="grid-w50 md:grid-w33 xl:grid-w25" />
  <img src="/images/homelab/o-nas-front.jpg" class="grid-w50 md:grid-w33 xl:grid-w25" />
  <img src="/images/homelab/o-nas-back.jpg" class="grid-w50 md:grid-w33 xl:grid-w25" />
{{< /gallery >}}

<br>  
Over time, that NAS became unbearably slow – booting up took half an hour. So in June 2025, I decided to build a new one using old parts from the attic. More on that in <a href="https://social.eike.in/@aikhae/114642633695184428" target="_blank">this Mastodon post :)</a>

{{< gallery >}}
  <img src="/images/homelab/n-o-nas.jpg" class="grid-w50 md:grid-w33 xl:grid-w25" />
  <img src="/images/homelab/n-o-nas-deployed.jpg" class="grid-w50 md:grid-w33 xl:grid-w25" />
{{< /gallery >}}
{{< /timelineItem >}}

{{< timelineItem icon="star" header="Another move" badge="2025">}}
With Windows 10 reaching end-of-life and Windows 11 having higher hardware requirements, I got lucky and snagged a PC with an i7-7700 :)

<br>  
While I was still waiting for that machine to arrive, my old network rack decided to just fall off the wall 🥸

{{< gallery >}}
  <img src="/images/homelab/nw-schrank-ungluek-1.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
  <img src="/images/homelab/nw-schrank-ungluek-2.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
{{< /gallery >}}

<br>  
Given the circumstances, I bought a larger rack that could hold both the server and a UPS.  
First, I got the <a href="https://www.reichelt.de/de/de/shop/produkt/19_wandgehaeuse_tiefe_600_mm_12_he-247176" target="_blank">EFB WGB-1912GR60</a> and mounted the network hardware inside.

{{< figure
    src="/images/homelab/new-rack-old-hw.jpg"
    alt="Network gear inside the new rack"
    caption="Someone forgot to order cage nuts?"
    >}}

Soon after, I migrated the new server into an <a href="https://geizhals.de/inter-tech-3u-k-340l-88887332-a3189152.html" target="_blank">Inter-Tech 3U-K-340L</a> case (<b>do NOT buy it – it’s awful!</b>).  
It was then mounted alongside this <a href="https://geizhals.de/bluewalker-powerwalker-vi-500-r1u-10121047-a1808100.html" target="_blank">UPS</a>.  
Since I reused all drives from the previous system, all I had to do was change the IP address of the new server to match the old one.

{{< figure
    src="/images/homelab/current-rack.jpg"
    alt="Current rack with server and UPS"
    >}}
{{< /timelineItem >}}

{{< /timeline >}}

## Hardware
A quick overview of the hardware in my server (*not guaranteed to be up to date*):
* Intel Core **i7-7700**
* **48 GB** DDR4 **RAM**
  * 2× 16 GB  
  * 2× 8 GB
* NVIDIA **GTX 1650 SUPER**
* Gigabyte **B250-HD3P-CF**
* 4× **240 GB SSDs**
* 2× **2 TB HDDs**
* 16 GB PNY USB stick (boot drive)
* Thermaltake **Hamburg (530 W)**
* Inter-Tech 3U-K-340L (🤮)
* **Unraid**

## Services
Here are most of the services currently running on my server:
{{< gallery >}}
    <div class="grid-w100 rounded-md p-4" style="background:#0082c9">
        <center>
          <img src="/images/homelab/logos/nextcloud.svg" style="height:200px" alt="Nextcloud Logo"/>
          <h3>Nextcloud</h3>
        </center>
    </div>
    <div class="grid-w100 rounded-md p-4" style="background:#10BDF2">
        <center>
          <img src="/images/homelab/logos/home-assistant.svg" style="height:200px" alt="Home Assistant Logo"/>
          <h3>Home Assistant</h3>
        </center>
    </div>
    <div class="grid-w50 rounded-md p-4" style="background:#000B25">
        <center>
          <img src="https://raw.githubusercontent.com/jellyfin/jellyfin-ux/master/branding/tizen/icon.png" style="height:150px" alt="Jellyfin Logo" />
          <h3>Jellyfin</h3>
        </center>
    </div>
    <div class="grid-w50 rounded-md p-4" style="background:#3050FF">
        <center>
          <img src="https://github.com/kilrah/unraid-docker-templates/raw/main/icons/searxng.png" style="background:white;height:150px" class="rounded-md" alt="SearXNG Logo"/>
          <h3>SearXNG</h3>
        </center>
    </div>
    <div class="grid-w100 rounded-md p-4" style="background:#17063B">
        <center>
          <img src="https://raw.githubusercontent.com/linuxserver/docker-templates/master/linuxserver.io/img/mastodon-logo.png" style="height:200px" class="rounded-md" alt="Mastodon Logo"/>
          <h3>Mastodon</h3>
        </center>
    </div>
    <div class="grid-w50 rounded-md p-4" style="background:white">
        <center>
          <img src="https://raw.githubusercontent.com/selfhosters/unRAID-CA-templates/master/templates/img/vaultwarden.png" style="height:150px" alt="Vaultwarden Logo"/>
          <h3 style="color:black">Vaultwarden</h3>
        </center>
    </div>
    <div class="grid-w50 rounded-md p-4" style="background:#FD4B2D">
        <center>
          <img src="https://raw.githubusercontent.com/ibracorp/app-logos/main/authentik/authentik.png" style="background:white;height:150px" class="rounded-md" alt="Authentik Logo"/>
          <h3>Authentik</h3>
        </center>
    </div>
    <div class="grid-w50 rounded-md p-4" style="background:#FA5252">
        <center>
          <img src="https://raw.githubusercontent.com/manuel-rw/unraid-templates/master/templates/homarr/icon.png" style="background:white;height:150px" alt="Hommarr Logo"/>
          <h3>Hommarr</h3>
        </center>
    </div>
    <div class="grid-w50 rounded-md p-4" style="background:#F46E32">
        <center>
          <img src="https://nginxproxymanager.com/icon.png" style="background:white;height:150px" alt="Nginx Proxy Manager Logo"/>
          <h3>Nginx Proxy Manager</h3>
        </center>
    </div>
    <div class="grid-w100 rounded-md p-4" style="background:#293646">
        <center>
          <img src="https://raw.githubusercontent.com/imagegenius/templates/main/unraid/img/obico.png" style="height:200px" alt="Obico Logo"/>
          <h3>Obico</h3>
        </center>
    </div>
    <div class="grid-w50 rounded-md p-4" style="background:white">
        <center>
          <img src="https://ollama.ai/public/ollama.png" style="height:150px" alt="Ollama Logo"/>
          <h3 style="color:black">Ollama</h3>
        </center>
    </div>
    <div class="grid-w50 rounded-md p-4" style="background:white">
        <center>
          <img src="https://raw.githubusercontent.com/open-webui/open-webui/main/static/favicon.png" style="height:150px" alt="Open WebUI Logo"/>
          <h3 style="color:black">Open WebUI</h3>
        </center>
    </div>
    <div class="grid-w50 rounded-md p-4" style="background:#E0E1DF">
        <center>
          <img src="https://raw.githubusercontent.com/linuxserver/docker-templates/master/linuxserver.io/img/orcaslicer-logo.png" style="height:150px" alt="Orca Slicer Logo"/>
          <h3 style="color:black">Orca Slicer</h3>
        </center>
    </div>
    <div class="grid-w50 rounded-md p-4" style="background:#DC7734">
        <center>
          <img src="https://raw.githubusercontent.com/m-klecka/unraid-templates/main/spoolman/spoolman.png" style="height:150px" alt="Spoolman Logo"/>
          <h3>Spoolman</h3>
        </center>
    </div>
    <div class="grid-w50 rounded-md p-4" style="background:#980200">
        <center>
          <img src="https://i.imgur.com/OWkNcEn.png" style="background:white;height:150px" class="rounded-md" alt="Pi-hole Logo"/>
          <h3>Pi-hole</h3>
        </center>
    </div>
    <div class="grid-w50 rounded-md p-4" style="background:white">
        <center>
          <img src="https://dl.ubnt.com/press/Company_Logos/U_Logo/WEB/U_Logo_RGB.png" style="height:150px" alt="Unifi Logo"/>
          <h3 style="color:black">Unifi</h3>
        </center>
    </div>
{{< /gallery >}}

## Networking
Most of my services run in Docker containers within a shared virtual Docker network. External access is handled by Nginx Proxy Manager, which is reachable via a port forwarding rule on my FritzBox.

Since I have a dynamic public IP, I use the FritzBox’s built-in DynDNS support in combination with my DNS provider. Whenever the IP changes, a specific DNS record is automatically updated.  
All other domains use CNAMEs pointing to that single record.
