# fluffy-spoon

1 GET A NEW EMAIL  https://protonmail.com/

2 SIGN UP 4 FREE ACCOUNT 
	https://github.com
	
	SEND @ ADDRESS
3 NAVIGATE HERE 
	https://github.com/unknown-unlimited
	

++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

OPSEC101  -

UNKNOWN-ONLINE-BASICS 
TOOLS

proxychains   
    - a tool that forces any TCP connection made by any given application to follow through proxy like TOR or any other SOCKS4,      `S    OCKS5 or HTTP(S) proxy. Supported auth-types: "user/pass" for SOCKS4/5, "basic" for HTTP.   ttp://proxychains.sourceforge.net/

ProxyChains

    Download the latest source (version 3.1)
    ProxyChains HowTo (README)
    Public Forum
    ProxyChains project page at SourceForge
    Ezine articles about proxy servers (kind of humor)
    Proxy server search (try 1080 or 8080)

About proxychains tool:
     * It's a proxifier.
     * Latest version: 3.1
     * Dedicated OS: Linux and other Unices.
     * Allows TCP and DNS tunneling through proxies.
     * Supports HTTP, SOCKS4 and SOCKS5 proxy servers.
     * Different proxy types can be mixed in the same chain.
     * Proxy chain: user-defined list of proxies chained together.

Warning
	this program works only on dynamically linked programs. also both proxychains and the program to call must use the same dynamic linker (i.e. same libc)
Known limitations of the current version

when a process forks, does a DNS lookup in the child, and then uses the ip in the parent, the corresponding ip mapping will not be found, this is because the fork can’t write back into the parents mapping table. IRSSI shows this behaviour, so you have to pass the resolved ip address to it. (you can use the proxyresolv script (requires "dig") to do so)

this means that you can’t currently use tor onion urls for irssi. to solve this issue, an external data store (file, pipe, …​) has to manage the dns <→ ip mapping. of course there has to be proper locking. shm_open, mkstemp, are possible candidates for a file based approach, the other option is to spawn some kind of server process that manages the map lookups. since connect() etc are hooked, this must not be a TCP server.

I am reluctant on doing this change, because the described behaviour seems pretty idiotic (doing a fork only for a DNS lookup), and irssi is currently the only known affected program.
Installation
Using release version

Proxychains-4.2.0 are available with pkgsrc to everyone using it on Linux, NetBSD, FreeBSD, OpenBSD, DragonFlyBSD or Mac OS X. You just need to install pkgsrc-wip repository and run make install in a wip/proxychains directory.

You can find out more about pkgsrc on pkgsrc and about pkgsrc-wip on Pkgsrc-wip homepage


Usability :
     * Run any program through proxy server.
     * Access the Internet from behind a restrictive firewall.
     * Hide your IP
     * Run SSH, telnet, wget, ftp, apt, vnc, nmap through proxy servers.
     * Access Intranets (192.168.*.*/10.*.*.*) from outside through reverse proxy.
  	
    When to use it

    When the only way to get "outside" from your LAN is through proxy server.

    To get out from behind restrictive firewall which filters outgoing ports.

    To use two (or more) proxies in chain:

   like: your_host <--> proxy1 <--> proxy2 <--> target_host

    To "proxify" some program with no proxy support built-in (like telnet)

    Access intranet from outside via proxy.

    To use DNS behind proxy.

Some cool features

    This program can mix different proxy types in the same chain

  like: your_host <-->socks5 <--> http <--> socks4 <--> target_host

    Different chaining options supported random order from the list ( user defined length of chain ). exact order (as they appear in the list ) dynamic order (smart exclude dead proxies from chain)

    You can use it with any TCP client application, even network scanners yes, yes - you can make portscan via proxy (or chained proxies) for example with Nmap scanner by fyodor (www.insecire.org/nmap).

  proxychains nmap -sT -PO -p 80 -iR  (find some webservers through proxy)

    You can use it with servers, like squid, sendmail, or whatever.

    DNS resolving through proxy.

Configuration

proxychains looks for configuration in the following order:

    SOCKS5 proxy port in environment variable ${PROXYCHAINS_SOCKS5} (if set, no further configuration will be searched)

    file listed in environment variable ${PROXYCHAINS_CONF_FILE} or provided as a -f argument to proxychains script or binary.

    ./proxychains.conf

    $(HOME)/.proxychains/proxychains.conf

    /etc/proxychains.conf

see more in /etc/proxychains.conf
Usage Example

$ proxychains telnet targethost.com

in this example it will run telnet through proxy(or chained proxies) specified by proxychains.conf
Usage Example

$ proxychains -f /etc/proxychains-other.conf targethost2.com

in this example it will use different configuration file then proxychains.conf to connect to targethost2.com host.
Usage Example

$ proxyresolv targethost.com

in this example it will resolve targethost.com through proxy(or chained proxies) specified by proxychains.conf
Usage Example:

$ ssh -fN -D 4321 some.example.com
$ PROXYCHAINS_SOCKS5=4321 proxychains zsh

in this example, it will run a shell with all traffic proxied through OpenSSH’s "dynamic proxy" (SOCKS5 proxy) on localhost port 4321.


https://github.com/UnknownSec1/proxychains.git

https://github.com/UnknownSec1/proxychains

 
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

fetch-some-proxies 

Simple Python script for fetching "some" (usable) proxies. It fetches (periodically updated) list of public proxies and automatically finds in a quick manner those usable in that same moment (Note: testing of SOCKS proxies is currently possible only on non-Windows platforms).

Why should you use it? Well, if you've ever used free proxy lists around you'll know the pain of finding actually working proxies. This tool will automatically do the list fetching and proxy testing for you. Also, only proxies that support HTTPS traffic will be returned, which guarantees access to majority of Internet sites.


https://github.com/unknown-unlimited/fetch-some-proxies

+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++


vpngate-with-proxy

VPN GATE client for linux

    Be able to connect to open vpn servers at http://www.vpngate.net/en/ directly or through proxy
    Auto add DNS to fix DNS leak.
    Auto filter out dead VPN servers. (updated on August 16th)
    Can execute user defined script after vpn_tunnel is established or broken.

Work on Debian and Redhat based system. Tested on Ubuntu, Raspbian, Fedora, Bunsen.

I will wrap SoftEther_vpn later when I have time. You are welcome to fork this repo and wrap SoftEther_vpn yourself.

Indicator: is optional.

Tested on Ubuntu and is only enabled by default on Ubuntu.

For other unix os, you need to modify the run file and install packages below:

sudo apt-get install gir1.2-appindicator3-0.1 gir1.2-notify-0.7 python-gobject

If you have any trouble or request about the program, please make a new issue at https://github.com/Dragon2fly/vpngate-with-proxy/issues
Dependency:

    python 2.7.x: should already be shipped with your linux

Except python 2.7.x, all below dependencies should be automatically installed at first run.

    openvpn: $ sudo apt-get install openvpn
    python-requests: $ sudo apt-get install python-requests
    python-urwid 1.3+: $ sudo apt-get install python-urwid , for tui version (terminal user interface)
    wmctrl: $ sudo apt-get install wmctrl, for Indicator of tui version, use for focusing window from indicator.

How to use:
0. Pre-installation

    If your network is behind a proxy

  $ export http_proxy="http://your_proxy:your_port"
  $ export https_proxy="http://your_proxy:your_port"

    If you has just installed your os, please update your os for it to fetch packages list and know where to download other packages later.

$ sudo apt-get update && sudo apt-get upgrade

    Please check the os clock and calendar if it is correct for openvpn authentication to work properly.

1. Installation:

Using git:

$ sudo apt-get install git
$ git clone https://github.com/Dragon2fly/vpngate-with-proxy.git

If your network is behind a proxy:

$ sudo -E apt-get install git
$ git clone https://github.com/Dragon2fly/vpngate-with-proxy.git

You can also download the zip file It contains the "vpngate-with-proxy" folder. Extract it into anywhere you want eg: $HOME.

user_script:

Within this folder, there should be a file user_script.sh. This file allow you to run extra commands to fit your need. You have to manually edit this file and don't change the file name. Commands are divided into 2 groups:

    up: execute after vpn tunnel is established successfully.
    down: execute after vpn tunnel is broken/terminated.

2. First run:

If you have configured system wide proxy or proxy in firefox, it'd better to turn it off. After vpn tunnel is established, the programs that use system wide proxy may failed to connect to the internet using your proxy.

Launch vpngate-with-proxy by

$ cd vpngate-with-proxy
$ ./run [arg]

    arg could be either none or tui or cli.
    vpnproxy_tui.py has better UI, colorful and easier to use. Run when arg is none or tui
    vpnproxy_cli.py is normal terminal application, lightweight and is aim to run on server (RaspberryPi ?). Run when arg is cli

Then the program will first setup a configuration file config.ini by asking you for proxy if needed to connect to the Internet. After that it will show the default configuration of the program. Change any parameter to suit you and press Enter to continue. Next time launching this program, you won't see this configuration again. Either modify config.ini or check 5. Some notes

If no thing goes wrong, the vpn server's list will show up.

https://github.com/Dragon2fly/vpngate-with-proxy

https://github.com/UnknownSec1/vpngate-with-proxy


+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++


kali-anonstealth

ParrotSec's anonsurf and stealth, ported to work with Kali Linux.
How to use this repo

This repo contains the sources of both the anonsurf and pandora packages from ParrotSec combined into one.

Modifications have been made to use the DNS servers of Private Internet Access (instead of FrozenDNS), and fixes for users who don't use the resolvconf application. I have removed some functionality such as the gui and iceweasel in ram.

This repo can be compiled into a deb package to correctly install it on a Kali system.

The easiest way to get this working is to just run the installer. See the installation section for further info.

NOTE: This may work with any debian/ubuntu system, but this has only been tested to work on a kali-rolling amd64 system
Usage
Pandora

Pandora automatically overwrites the RAM when the system is shutting down. Pandora can also be ran manually:

pandora bomb

NOTE: This will clear the entire system cache, including active SSH tunnels or sessions.
anonsurf

Anonsurf will anonymize the entire system under TOR using IPTables. It will also allow you to start and stop i2p as well.

NOTE: DO NOT run this as service anonsurf $COMMAND. Run this as anonsurf $COMMAND

Usage:
 anonsurf {start|stop|restart|change|status}

 start - Start system-wide anonymous
          tunneling under TOR proxy through iptables
 stop - Reset original iptables settings
          and return to clear navigation
 restart - Combines "stop" and "start" options
 change - Changes identity restarting TOR 
 status - Check if AnonSurf is working properly
----[ I2P related features ]----
 starti2p - Start i2p services
 stopi2p - Stop i2p services

Installation

This package comes with an installer that makes things extremely easy:

./installer.sh

Once the installer is complete, you will be able to use both the anonsurf and pandora modules.

https://github.com/UnknownSec1/kali-anonsurf

https://github.com/unknown-unlimited/kali-anonsurf

++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

ALternate versions

https://github.com/UnknownSec1/AnonSurf-Installer/blob/master/README.md

https://github.com/UnknownSec1/AnonSurf-Installer

https://github.com/ParrotSec/anonsurf

https://github.com/unknown-unlimited/anonsurf?organization=unknown-unlimited&organization=unknown-unlimited


+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

Hybrid parrotsec anonsurf+ Tor-Buddy from AfterBurn @ NetSecNow  

https://github.com/unknown-unlimited/AnonSurfIPRotator

