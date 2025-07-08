+++
title = 'HomeLab'
summary = 'Mein HomeLab, was darauf läuft und wie es sich entwickelt hat'
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

Ich hatte das Bedürfnis, mein HomeLab der Welt zu zeigen – also habe ich hier einmal Hardware, Services und die Geschichte des Ganzen zusammengefasst. Viel Spaß beim Lesen :)

## Geschichte
{{< timeline >}}

{{< timelineItem icon="skull-crossbones" header="Die Anfänge" badge="2021 (?)">}}
Ich weiß nicht mehr genau, wann ich mit dem Ganzen angefangen habe – es müsste aber 2021 (Registrierung der HomeLab-Domain) oder 2022 (Zeitstempel eines Fotos aus meiner Galerie) gewesen sein.

Begonnen hat alles mit zwei Raspberry Pi 3B: Auf einem liefen Discord-Music-Bots, der andere war mit einer externen HDD ausgestattet und hostete mit <a href="https://nextcloudpi.com/" target="_blank">NextcloudPi</a> eine Nextcloud. Im Nachhinein bin ich etwas überrascht, dass ich bei diesem Setup keine Daten verloren habe 🥸

{{< figure
    src="/images/homelab/Homelab-21.jpg"
    alt="Die zwei Raspberry Pis, mein damaliges HomeLab"
    caption="Mein damaliges Homelab, versteckt hinter einem Schrank"
    >}}
{{< /timelineItem >}}

{{< timelineItem icon="bomb" header="Mehr Zeug" badge="2022 (?)">}}
Nachdem ich von der Existenz von Home Assistant und Pi-hole gehört hatte, wollte ich mir diese auch selbst hosten. Da ich keine Pis mehr übrig hatte, musste ein Trekstor-Notebook herhalten, auf dem ich Debian installierte.  
Die Dienste installierte ich "bare metal", also direkt auf dem System – was heute nicht einmal mehr offiziell von Home Assistant unterstützt wird.  
Das Notebook bekam dann einen USB-Ethernet-Adapter und ein permanent angeschlossenes Netzteil. <b>Der Akku blieb eingebaut 🔥</b>

<br>  
Als nächstes musste ich feststellen, dass ich nicht sowohl Nextcloud als auch Home Assistant auf denselben Ports derselben öffentlichen IP betreiben konnte. Nachdem ich die Situation viel zu lange ausgesessen hatte, entschied ich mich (endlich), einen Reverse Proxy einzurichten.

{{< mermaid >}}
graph LR;
N[Nextcloud]<-->R[NGINX Proxy];
H[HomeAssistant]<-->R;
R<-->I[Internet]
{{< /mermaid >}}
{{< /timelineItem >}}

{{< timelineItem icon="wand-magic-sparkles" header="Ein neues Zuhause" badge="2023">}}
Mit der wachsenden Zahl an Diensten in meinem HomeLab wurde es zunehmend unpraktisch, diese auf einzelnen, schwachen Rechnern laufen zu lassen.  
Ich entschied mich daher, meinen alten Computer zu einem Server umzubauen. Dieser bestand aus einem Intel Core i7-3770, 20 GB DDR3 RAM sowie 2× 2 TB HDDs und 2× 240 GB SSDs – jeweils in einem Pool. Als Betriebssystem wählte ich Unraid, da mir das System in der Demo gefiel und ich es leicht bedienen konnte.

<br>  
Die Migration von Home Assistant und Pi-hole verlief problemlos, da ich einfach ein Backup wiederherstellen konnte. Bei NextcloudPi war das schwieriger – ich musste zuerst die Festplatten auf BTRFS umstellen. Schlussendlich war es mir nicht möglich, die Nextcloud zu übertragen, weshalb ich sie neu einrichtete und die Daten manuell hochlud.

<br>  
Alles außer Home Assistant läuft hier inzwischen in Docker :)
{{< /timelineItem >}}

{{< timelineItem icon="lock" header="Backups!" badge="2024">}}
Als mir irgendwann klar wurde, dass das RAID in meinem Server kein echtes Backup ist, machte ich mich daran, ein kleines Backup-System aufzubauen.  
Zuerst wurden wöchentliche Backups mittels <a href="https://duplicati.com/" target="_blank">Duplicati</a> auf ein altes NAS zuhause geschoben.

<br>  
Da mittlerweile ziemlich wichtige Daten auf dem Server lagen, beschloss ich, zusätzlich eine Offsite-Sicherung einzurichten. Ich ergatterte ein weiteres altes NAS, stellte es bei meiner Oma auf und richtete eine dauerhafte VPN-Verbindung zu ihrem Netzwerk ein.  
Um Strom zu sparen, legte ich einen Zeitplan fest, dass dieses NAS nur sonntags hochfährt, um die Sicherungen zu machen. Zusätzlich installierte ich einen Remote-Einschalter, um das NAS bei Bedarf manuell hochfahren zu können.

{{< gallery >}}
  <img src="/images/homelab/o-nas-remote-on-1.jpg" class="grid-w50 md:grid-w33 xl:grid-w25" />
  <img src="/images/homelab/o-nas-remote-on-2.jpg" class="grid-w50 md:grid-w33 xl:grid-w25" />
  <img src="/images/homelab/o-nas-front.jpg" class="grid-w50 md:grid-w33 xl:grid-w25" />
  <img src="/images/homelab/o-nas-back.jpg" class="grid-w50 md:grid-w33 xl:grid-w25" />
{{< /gallery >}}

<br>  
Dieses NAS wurde mit der Zeit allerdings so langsam, dass es etwa eine halbe Stunde zum Hochfahren brauchte. Deshalb entschied ich mich im Juni 2025, ein neues aus alten Teilen vom Dachboden zu bauen. Mehr dazu <a href="https://social.eike.in/@aikhae/114642633695184428" target="_blank">in diesem Mastodon-Post :)</a>

{{< gallery >}}
  <img src="/images/homelab/n-o-nas.jpg" class="grid-w50 md:grid-w33 xl:grid-w25" />
  <img src="/images/homelab/n-o-nas-deployed.jpg" class="grid-w50 md:grid-w33 xl:grid-w25" />
{{< /gallery >}}
{{< /timelineItem >}}

{{< timelineItem icon="star" header="Noch ein Umzug" badge="2025">}}
Durch das bevorstehende Ende von Windows 10 und die Hardwareanforderungen von Windows 11 konnte ich einen PC mit i7-7700 ergattern :)

<br>  
Während dieser Rechner noch unterwegs war, fiel der bisherige Netzwerkschrank einfach von der Wand 🥸

{{< gallery >}}
  <img src="/images/homelab/nw-schrank-ungluek-1.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
  <img src="/images/homelab/nw-schrank-ungluek-2.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
{{< /gallery >}}

<br>  
Dies nahm ich als Anlass, einen neuen und größeren Schrank zu kaufen, in dem auch der Server mit einer USV montiert werden konnte.  
Zuerst wurde ein <a href="https://www.reichelt.de/de/de/shop/produkt/19_wandgehaeuse_tiefe_600_mm_12_he-247176" target="_blank">EFB WGB-1912GR60</a> angeschafft und die Netzwerkhardware dort montiert.

{{< figure
    src="/images/homelab/new-rack-old-hw.jpg"
    alt="Die Netzwerkhardware im neuen Schrank"
    caption="Hat da wer vergessen, Käfigmuttern zu kaufen?"
    >}}

Kurz darauf wurde der neue Server in ein <a href="https://geizhals.de/inter-tech-3u-k-340l-88887332-a3189152.html" target="_blank">Inter-Tech 3U-K-340L</a> (<b>Nicht kaufen, das Ding ist schrecklich!</b>) eingebaut.  
Dieser kam dann zusammen mit <a href="https://geizhals.de/bluewalker-powerwalker-vi-500-r1u-10121047-a1808100.html" target="_blank">dieser</a> USV in den Schrank.  
Da alle Festplatten mit in den neuen Server umzogen, musste ich lediglich die IP-Adresse des neuen Servers auf die ursprüngliche ändern.

{{< figure
    src="/images/homelab/current-rack.jpg"
    alt="Der aktuelle Schrank mit Server und USV"
    >}}
{{< /timelineItem >}}

{{< /timeline >}}

## Hardware
Eine kleine Übersicht der Hardware in meinem Server (*keine Garantie auf Aktualität*):
* Intel Core **i7-7700**
* **48 GB** DDR4 **RAM**
  * 2× 16 GB  
  * 2× 8 GB
* NVIDIA **GTX 1650 SUPER**
* Gigabyte **B250-HD3P-CF**
* 4× **240 GB SSDs**
* 2× **2 TB HDDs**
* 16 GB PNY USB-Stick (Boot Drive)
* Thermaltake **Hamburg (530 W)**
* Inter-Tech 3U-K-340L (🤮)
* **Unraid**

## Services
Hier sind die meisten Services, die aktuell auf meinem Server laufen:
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

## Netzwerk
In meinem Netzwerk laufen die meisten Dienste als Docker-Container in einem gemeinsamen virtuellen Docker-Netzwerk. Der Zugriff von außen erfolgt über den Nginx Proxy Manager, der per Portfreigabe durch die FritzBox erreichbar ist.

Da ich eine dynamische öffentliche IP-Adresse habe, nutze ich die integrierte DynDNS-Funktion der FritzBox in Kombination mit meinem DNS-Anbieter. Sobald sich die IP-Adresse ändert, wird automatisch ein DNS-Eintrag aktualisiert.  
Alle anderen Domains verweisen per CNAME auf diesen zentralen Eintrag.
