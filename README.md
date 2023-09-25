# How to IRL stream for free or cheap

## Direct RTMP (Real-Time Messaging Protocol) to kick/twitch

### PRISM Live (iphone and android)
This is the most user friendly way to IRL stream via RTMP.  You can add overlays with user friendly stretching of overlays, but the built in chat not working for kick, but might work for twitch.

Login to prism via any method, and go to "ready" and add a "Custom RTMP" source with your kick credentials you can get from your dashboard.  Easy.

### IRL Pro (android only)
This is a more complicated app, but much more free (no login required) and powerful, based on historic Larix open API.  The built in kick chat is excellent, can support overlays but not a graphical way to set them up.  IRL Pro can stream directly via rtmp to kick

Go to Settings>Connections and add a connection like this:
    
rtmps://fa723fc1b171.global-contribute.live-video.net/app/{streamkey}

## Stream to OBS and then to kick/twitch

### PRISM Live with Free RTMP direct to OBS

You're going to need an nginx-rtmp install on the same system as OBS to accept the stream from PRISM.  rtmp uses port 1935 and tcp so forward port 1935/tcp from your router to OBS computer hosting nginx-rtmp

Here is a Windows build of nginx-rtmp ready to listen on port 1935 immediately and ready to accept rtmp without any configuration, just need allow port 1935 rule or disable firewall to test

https://github.com/NOALBS/nginx-obs-automatic-low-bitrate-switching#nginx-setup just get "Hosted on Github" link, unzip and run nginx_start.bat

Setup PRISM to stream to

rtmp://IP_ADDRESS/publish/ where "IP_ADDRESS" can be local if using wifi or public ip address you can get from ipchicken.com from outside of the home if ports are forwarded.

with a streamkey of a WORD that you won't share

then on OBS add a VLC Video Source (not local) like this and loop playlist and only thing in playlist is

rtmp://0.0.0.0/publish/WORD

Transform source to fit to screen, good to go.

## IRL Pro with Free SRT direct to OBS

We're going to use SRT (Secure Reliable Transmission) to get the stream into OBS, so pick a port.  We will use port 4000 for this example and SRT uses udp.

Go to Settings>Connections and add a connection like this:
    URL srt://IP_ADDRESS:4000 with default other settings
    
then on OBS add a media source (not local) like this
srt://0.0.0.0:4000?mode=listener

use local IP on OBS even if from internet so OBS can listen for SRT "call"

Reconnect delay 3 seconds, input format mpegts

Transform source to fit to screen, good to go.  I would recommend using HEVC codec for less data transmission with this method, Settings > Video close to the bottom.

Remember, IP_ADDRESS can be a local address if you're not leaving home, but without it you will need to stream to your public IP with port 4000/udp forwarded from router to OBS computer.

## IRL Pro with $10/month SRT ingress from belabox cloud

If direct SRT from IRL Pro to OBS doesn't work, you can use a paid solution for an srtla ingress.  For this example, we will be using the belabox cloud SRTLA ingress which costs $10/month and supports belabox development and the creator, rational IRL.

This solution does not require port fowarding at all.

Do what you need to do to get an account on https://cloud.belabox.net/ by having a GitHub account and sponsoring the project for $10/month for the SRTLA ingress and then go to the page, get an account on belabox cloud, login and go to SRT(LA) relays and create one and pick eastern or western United States or close to where you live or will be streaming from.

Honestly, that page has screenshots, but basically you copy and paste their settings into and IRL Pro connection and then setup a Media Source on OBS (same as free SRT method) but using their credentials available on site.

Transform source to fit to scren, good to go.  I would recommend using HEVC codec for less data transmission with this method, Settings > Video close to the bottom.

## The worst way: VDO Ninja

If you can't port forward, and only have $0, you can use VDO Ninja, just install the app and add a  browser source to OBS.  It is really bad quality, but is does bust firewall

### Caveats

This will maximize heat and temperature the phone can likely handle.  No case helps. 720p uses less data and less compational power.  IRL Pro can still broadcast with screen off which screen creates some heat too.  Bonding connections using multiple providers from IRL Pro will increase heat.  But just do science and learn what works  for your setup.  

### Credits

banj, nhotkow, UnclePockets, Rationalirl, WilliamH, OBS studio the true goat software-- free as in beer and free as in speech.  Big ups to Linux, OpenBSD, and Monero (XMR).  GetMonero.org

We are scientists.
