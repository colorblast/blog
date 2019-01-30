---
layout: post
title: 'A Gentle Introduction To Protecting Your Privacy'
date: 2019-01-29 21:44:10
categories: privacy ethics
---

Events in the last decade have highlighted that huge colossal entities like the government and Facebook have actively collected and/or sold highly personal data . Once hailed as "benevolent benefactors", the public perception of tech companies like Google has increasingly turn negative. This is for good reason, as incidents like [Cambridge Analytica](https://www.nytimes.com/2018/03/19/technology/facebook-cambridge-analytica-explained.html) clearly demonstrate. Ad and marketing companies have used the Internet at their full disposal in terms of data collection and retention.

This has real tangible effects. Most advertising is now targeted, in which products which are more "relevant" to you, are shown to you. Information that once entered a database, is now shared among all. Even if you somehow trust these companies to be benevolent, and don't care that they essentially fit you into these filter bubbles (literally how Facebook's news article system worked), the vast breadth of them and the general insecurity of the Internet almosts guarantees that your information falls into the wrong hands. See [Apollo breach](https://www.wired.com/story/apollo-breach-linkedin-salesforce-data/) and [Exactis breach](https://www.wired.com/story/exactis-database-leak-340-million-records/).

Ultimately control of one's data is no longer the default, and one needs to proactively take steps in order to maintain one's privacy.

The first layer is the medium. Whatever you're using, a computer, a phone, or some sort of tablet, it has software on it, an operating system, that you use to do things like surf the net or listen to music.

Operating systems like Windows 10 have been known to [collect data](https://www.computerworld.com/article/3159424/microsoft-windows/you-still-can-t-turn-off-windows-10-s-built-in-spyware.html) without clearly stating what they were collecting, nor what they would do with it, or how long they would retain it. Some Android derivatives found on cheaper phones may also contain spyware. Given that Windows is run by Microsoft, and Android by Google (the open source part is increasingly deprecated with integration into the Google ecosystem being key), it should be expected that there is some depreciation of privacy of some sort in exchange for the relative convenience.  

The priority level of this relatively low. Cost-free or low cost alternatives to Windows include various flavours and distributions of Linux which requires some technical knowledge. [LineageOS](https://lineageos.org/) and [/e/](https://e.foundation/) are Android alternatives.

The second layer is the network connection. Connecting to the Internet requires the usage and reliance on an ISP, such as Verizon or Comcast. There have been numerous complaints and incidents where ISPs have sold data, whether it be "anonymized" location data (you can still be triangulated) or it by the bulk. All Internet data flows through the ISP, which means that they can (potentially) view your entire search history and keep logs (which they do).

Prevention at this layer often involves what's called a VPN, a virtual private network, in which connecting to the network creates an encrypted tunnel to the network, which can then pass the request on to the net (for the most part). This is why people can use VPNs to avoid things like geolocation restrictions (hello Netflix) and censorship with signicantly less chance of reprisal.

There are many VPNs out there; the thing to keep note of is the fact that the vpn still sees what data is passing through. You get what you pay for, so using a free vpn will often result in the vpn providers themselves selling your data, maintaining logs, etc. See the case of [Hola VPN](https://thenextweb.com/contributors/2018/05/28/be-cautious-free-vpns-are-selling-your-data-to-3rd-parties/). Even bundled-in browser ones do this, such as [Opera's](https://thebestvpn.com/how-free-vpns-sell-your-data/).

Network connections often resolve things called DNS queries. DNS stands for domain name system, in which a domain like example.net is converted to a numeric address that a computer can interpret, what is called an IP address. ISPs can glean and sell data from these queries. Using something like [1.1.1.1](https://1.1.1.1) can avoid this (You'd have to trust cloudflare though).

The next layer is the browser. Certain browsers are obviously bundled in with operating systems, and others are sponsored by certain companies, with various advertising agendas. This is something that should be kept in mind when considering a browser that would truly respect your privacy. Firefox is a good example that easily comes to mind.

The next and most obvious layer is an actual connection to a website, whether  it be through a browser, a desktop application, or whatever. The fact of the matter is that most sites employ sophisticated tracking technology in order to do things like increase impressions (meaningful page views) and thus sales.

To block tracking, going into your browser settings and enabling DNT (Do Not Track), sends your HTTP request (internet request) to the site, with a request to not track you. *The site, by no means, need to comply*. The DNT standard got stuck in some Internet bureacratic lingo and in-fighting for the past couple years, meaning slow adoption of the standard.

The next thing is enabling an ad blocker. The purpose of most tracking technology is to serve more relevant ads, and an adblockers allows you to block those scripts (and the ads too, which reduces loading time!). Be wary of in-browser adblockers due to their sponsored nature. Many adblockers are also owned and maintained by private companies that make profit off whitelisting certain companies. See the case of [Adblock Plus](https://www.cnbc.com/2016/09/14/adblock-plus-defends-new-whitelisting-ad-platform.html). I recommend and personally use Raymond Gorhill's [uBlock Origin](https://github.com/gorhill/uBlock) (this is NOT uBlock, they're two different ones).

Using HTTPS to access the Internet encrypts your traffic, vs a regular HTTP connection; I recommend using HTTPS Everywhere, an extension developed by the EFF to use HTTPS whenever possible.

For email, marketers often embed web beacons, small images, to determine whether you read or opened whatever they sent. Setting image blocking in email prevents this.

Using PGP or GPG encryption with a service like [protonmail](https://protonmail.com/), [tutanota](https://tutanota.com/), or [lavabit](https://lavabit.com/) offer addition mechanisms such as message authenticity, expiring messages, encryption, and no logs.

Using a messaging service like [Keybase](https://keybase.io) over that of Messenger or your phone's default SMS app, means end-to-end encryption, in which even the messaging app which is transmitting your messages, has no idea what's streaming  in and out. Other apps like this include [Signal](https://signal.org/) by OpenWhisperSystems.

For search, privacy-focused alternatives include [DuckDuckGo](https://duckduckgo.com), [Startpage](https://startpage.com), and [SearX](https://asciimoo.github.io/searx/).