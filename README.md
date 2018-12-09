# fluffy-spoon

proxychains   
    - a tool that forces any TCP connection made by any given application to follow through proxy like TOR or any other SOCKS4,     `````SOCKS5 or HTTP(S) proxy. Supported auth-types: "user/pass" for SOCKS4/5, "basic" for HTTP. http://proxychains.sourceforge.net/

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

 
