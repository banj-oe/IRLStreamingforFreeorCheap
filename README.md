# How to IRL stream for free or cheap

## Current recommendations
### Moblin on iPhone/ios
### IRL Pro on Android

## Direct RTMP (Real-Time Messaging Protocol) to kick/twitch

If you're on iphone rawdog kick with moblin.  If you're on android, rawdog kick with IRL Pro.  Get your stream key and URL from dashboard.

### Moblin (iphone/ipad/macos)
Moblin is _the_ way to stream from an iphone/ipad/macos.  App store available but also for the latest get the testflight on the github https://github.com/eerimoq/mobs and join the discord.  Add a connection to kick or twitch.  Put your username for chat.  It supports chat on watch and the kitchen sink as far as features.  Check out moblink!  It gets deep.  Join the moblin discord.

### IRL Pro (android only)
This is a great app, don't too far into the settings. Chat is built into IRL Pro, has free built-in bonding for sending direct to platform/restream.

Go to Settings>Connections and add a connection like this:
    
rtmps://fa723fc1b171.global-contribute.live-video.net/app/{streamkey}

## Stream to OBS and then to kick/twitch

Marlow made a really nice Youtube video showing this whole process.  It's called "Self-hosted OBS for IRL live streaming - an interactive tutorial for beginners" 
https://www.youtube.com/watch?v=xoDdfiVRJHc

## IRL Pro with Free SRT direct to OBS

We're going to use SRT (Secure Reliable Transport) to get the stream into OBS, so pick a port.  We will use port 4000 for this example and SRT uses udp.

Go to Settings>Connections and add a connection like this:
    URL srt://IP_ADDRESS:4000 with default other settings
    
then on OBS add a media source (not local) like this
srt://0.0.0.0:4000?mode=listener

use local IP 0.0.0.0 on OBS even if from internet so OBS can listen for SRT "call"

Reconnect delay 2 seconds, input format mpegts

Transform source to fit to screen, good to go.  I would recommend using HEVC codec for less data transmission with this method, Settings > Video close to the bottom.

Remember, IP_ADDRESS can be a local address if you're not leaving home, but without it you will need to stream to your public IP with port 4000/udp forwarded from router to OBS computer.

## IRL Pro with $10/month SRT ingress from belabox cloud

If direct SRT from IRL Pro to OBS doesn't work, you can use a paid solution for an srtla ingress.  For this example, we will be using the belabox cloud SRTLA ingress which costs $10/month and supports belabox development and the creator, RationalIRL.  This supports bonding multiple connections.

This solution does not require port fowarding at all.

Do what you need to do to get an account on https://cloud.belabox.net/ by having a GitHub account and sponsoring the project for $10/month for the SRTLA ingress and then go to the page, get an account on belabox cloud, login and go to SRT(LA) relays and create one and pick eastern or western United States or close to where you live or will be streaming from.

Honestly, that page has screenshots, but basically you copy and paste their settings into and IRL Pro connection and then setup a Media Source on OBS (same as free SRT method) but using their credentials available on site.

Transform source to fit to scren, good to go.  I would recommend using HEVC codec for less data transmission with this method, Settings > Video close to the bottom.

## Additional iPhone apps that can use SRT/SRTLA

## The worst way: VDO Ninja

If you can't port forward, and only have $0, you can use VDO Ninja, just install the app and add a browser source to OBS.  It is really bad quality, but is does bust firewalls.

### Caveats

This will maximize heat and temperature the phone can likely handle.  No case helps. 720p uses less data and less encoding power usage.  IRL Pro can still broadcast with screen off which screen creates some heat too.  Bonding connections using multiple providers will increase heat.  But just do science and learn what works for your setup.  

### Credits

banj, Marlow, UnclePockets, Rationalirl, WilliamH, ffmpeg (the backened for OBS, VLC, all media encoding/decoding/muxing/etc), and OBS studio-- free as in beer and free as in speech.

We are scientists.
