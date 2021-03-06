
# Deprecated linux commands

<div id="container" class="group">

<h1><a href="https://dougvitale.wordpress.com/">Doug Vitale Tech Blog</a></h1>

<div id="content" class="group">
<div class="post-554 post type-post status-publish format-standard hentry category-computer-networking-techniques-and-concepts tag-ip-command tag-ip-link tag-ip-neighbor tag-ip-route tag-iproute2 tag-iwconfig tag-linux-deprecated">
	<h2 id="post-554">Deprecated Linux networking commands and their&nbsp;replacements</h2>
	
	<div class="main">
		<p>In my <a title="Troubleshooting faulty network connectivity, part 2: Essential network&nbsp;commands" href="https://dougvitale.wordpress.com/2011/12/11/troubleshooting-faulty-network-connectivity-part-2-essential-network-commands/">article</a> detailing the command line utilities available for configuring and troubleshooting network properties on Windows and Linux, I mentioned some Linux tools that, while still included and functional in many Linux distributions, are actually considered <a title="Deprecation on Wikipedia" href="http://en.wikipedia.org/wiki/Deprecation">deprecated</a> and therefore should be phased out in favor of more modern replacements.</p>
<p>Specifically, the deprecated Linux networking commands in question are: <strong>arp</strong>, <strong>ifconfig</strong>,&nbsp;<strong>iptunnel</strong>, <strong>iwconfig</strong>, <strong>nameif</strong>, <strong>netstat</strong>, and <strong>route</strong>. These programs (except <strong>iwconfig</strong>) are included in the <a title="net-tools on the Linux Foundation" href="http://www.linuxfoundation.org/collaborate/workgroups/networking/net-tools">net-tools</a> package that has been unmaintained for years. The functionality provided by several of these utilities has been reproduced and improved in the new <a title="iproute2 on Wikipedia" href="http://en.wikipedia.org/wiki/Iproute2">iproute2</a> suite, primarily by using its new <strong>ip</strong> command. The <strong>iproute2</strong> software code is available from <a href="http://www.kernel.org/pub/linux/utils/net/iproute2/" title="Iproute2 on kernel.org">Kernel.org</a>. <strong>Iproute2</strong> documentation is available from <a href="http://www.linuxfoundation.org/collaborate/workgroups/networking/iproute2">the Linux Foundation</a> and <a href="http://www.policyrouting.org/iproute2-toc.html" title="IProute2 utility suite how-to on policyrouting.org">PolicyRouting.org</a>.</p>
<table width="820" border="1">
<tbody>
<tr>
<th>
<h3><strong>Deprecated command</strong></h3>
</th>
<th>
<h3><strong>Replacement command(s)</strong></h3>
</th>
</tr>
<tr>
<td style="padding:5px;"><strong>arp</strong></td>
<td style="padding:5px;"><strong>ip n</strong> (<strong>ip neighbor)</strong></td>
</tr>
<tr>
<td style="padding:5px;"><strong>ifconfig</strong></td>
<td style="padding:5px;"><strong>ip a</strong> (<strong>ip addr</strong>), <strong>ip link</strong>, <strong>ip -s</strong> (<strong>ip -stats)</strong></td>
</tr>
<tr>
<td style="padding:5px;"><strong>iptunnel</strong></td>
<td style="padding:5px;"><strong>ip tunnel</strong></td>
</tr>
<tr>
<td style="padding:5px;"><strong>iwconfig</strong></td>
<td style="padding:5px;"><strong>iw</strong></td>
</tr>
<tr>
<td style="padding:5px;"><strong>nameif</strong></td>
<td style="padding:5px;"><strong>ip link</strong>, <strong>ifrename</strong></td>
</tr>
<tr>
<td style="padding:5px;"><strong>netstat</strong></td>
<td style="padding:5px;"><strong>ss</strong>, <strong>ip route </strong>(for <strong>netstat-r</strong>), <strong>ip -s link </strong>(for <strong>netstat -i</strong>), <strong>ip maddr </strong>(for <strong>netstat-g</strong>)</td>
</tr>
<tr>
<td style="padding:5px;"><strong>route</strong></td>
<td style="padding:5px;"><strong>ip r</strong> (<strong>ip route</strong>)</td>
</tr>
</tbody>
</table>
<p><span style="color:#ffffff;">.</span><br>
Now let’s take a closer look at these deprecated commands and their replacements.</p>
<p><span id="more-554"></span></p>
<p>This article will not focus on <strong>iproute2</strong> or the <strong>ip</strong> command in detail; instead it will simply give one-to-one mappings between the deprecated commands and their new counterparts. For replacement commands that are listed as ‘not apparent’, please <a title="Contact" href="https://dougvitale.wordpress.com/contact/">contact me</a> if you know otherwise.</p>
<p><strong>Jump to:</strong></p>
<ul>
<li><a href="#arp">Arp</a></li>
<li><a href="#ifconfig">Ifconfig</a></li>
<li><a href="#iptunnel">Iptunnel</a></li>
<li><a href="#iwconfig">Iwconfig</a></li>
<li><a href="#nameif">Nameif</a></li>
<li><a href="#netstat">Netstat</a></li>
<li><a href="#route">Route</a></li>
<li><a href="#discussion">Discussion</a></li>
<li><a href="#recommended">Recommended reading</a></li>
</ul>
<p>Please note that <strong>nslookup</strong> and <strong>dig</strong> are covered separately <a title="Troubleshooting faulty network connectivity, part 2: Essential network&nbsp;commands" href="https://dougvitale.wordpress.com/2011/12/11/troubleshooting-faulty-network-connectivity-part-2-essential-network-commands/#nslookup">here</a>.<br>
<a name="arp"></a></p>
<h2>Arp</h2>
<table width="820" border="1">
<tbody>
<tr>
<th>
<h3><strong>Deprecated arp commands</strong></h3>
</th>
<th>
<h3><strong>Replacement</strong></h3>
</th>
</tr>
<tr>
<td style="padding:5px;"><strong>arp -a [host] </strong>or<strong> <code>--</code>all [host]</strong><br>
<span style="color:#ffffff;">.</span><br>
Shows the entries of the specified host name or IP address. If the <strong>[host]</strong> parameter is not used, all entries will be displayed.<strong><br>
</strong></td>
<td style="padding:5px;"><strong>ip n</strong> (or <strong>ip neighbor</strong>), or<strong> ip n show</strong></td>
</tr>
<tr>
<td style="padding:5px;"><strong>arp -d [ip_addr]</strong> or <strong><code>--</code>delete [ip_addr]</strong><br>
<span style="color:#ffffff;">.</span><br>
Removes the ARP cache entry for the specified host.</td>
<td style="padding:5px;"><strong>ip n del [ip_addr] </strong>(this “invalidates” neighbor entries)<strong><br>
<span style="color:#ffffff;">.</span><br>
ip n f [ip_addr]</strong> (or <strong>ip n flush [ip_addr]</strong>)</td>
</tr>
<tr>
<td style="padding:5px;"><strong>arp -D </strong>or<strong> <code>--</code>use-device</strong><br>
<span style="color:#ffffff;">.</span><br>
Uses the hardware address associated with the specified interface.</td>
<td style="padding:5px;">Not apparent</td>
</tr>
<tr>
<td style="padding:5px;"><strong>arp -e</strong><br>
<span style="color:#ffffff;">.</span><br>
Shows the entries in default (Linux) style.</td>
<td style="padding:5px;">Not apparent</td>
</tr>
<tr>
<td style="padding:5px;"><strong>arp -f [filename] </strong>or<strong> <code>--</code>file [filename]</strong><br>
<span style="color:#ffffff;">.</span><br>
Similar to the <strong>-s</strong> option, only this time the address info is taken from the file that <strong>[filename]</strong> set up. If no <strong>[filename]</strong> is specified, <em>/etc/ethers</em> is used as default.</td>
<td style="padding:5px;">Not apparent</td>
</tr>
<tr>
<td style="padding:5px;"><strong>arp -H </strong>or<strong> <code>--</code>hw-type [type] </strong>or<strong> -t [type]</strong><br>
<span style="color:#ffffff;">.</span><br>
When setting or reading the ARP cache, this optional parameter tells <strong>arp</strong> which class of entries it should check for. The default value of this parameter is <strong>ether</strong> (i.e. hardware code 0x01 for IEEE 802.3 10Mbps Ethernet).</td>
<td style="padding:5px;">Not apparent</td>
</tr>
<tr>
<td style="padding:5px;"><strong>arp -i [int] </strong>or<strong> <code>--</code>device [int]</strong><br>
<span style="color:#ffffff;">.</span><br>
Selects an interface. When dumping the ARP cache only entries matching the specified interface will be printed. For example, <strong>arp -i eth0 -s 10.21.31.41 A321.ABCF.321A</strong> creates a static ARP entry associating IP address 10.21.31.41 with MAC address A321.ABCF.321A on <strong>eth0</strong>.</td>
<td style="padding:5px;"><strong>ip n [add | chg | del | repl] dev [name]</strong></td>
</tr>
<tr>
<td style="padding:5px;"><strong>arp -n </strong>or<strong> <code>--</code>numeric</strong><br>
<span style="color:#ffffff;">.</span><br>
Shows IP addresses instead of trying to determine domain names.</td>
<td style="padding:5px;">Not apparent</td>
</tr>
<tr>
<td style="padding:5px;"><strong>arp -s [ip_addr] [hw_addr] </strong>or<strong> <code>--</code>set [ip_addr]</strong><br>
<span style="color:#ffffff;">.</span><br>
Manually creates a static ARP address mapping entry for host <strong>[ip_addr]</strong> with the hardware address set to <strong>[hw_addr]</strong>.</td>
<td style="padding:5px;"><strong>ip n add [ip_addr] lladdr [mac_address] dev [device] nud [nud_state] </strong>(see example below)</td>
</tr>
<tr>
<td style="padding:5px;"><strong>arp -v</strong><br>
<span style="color:#ffffff;">.</span><br>
Uses verbose mode to provide more details.</td>
<td style="padding:5px;"><strong>ip -s n</strong> (or <strong>ip -stats n</strong>)</td>
</tr>
</tbody>
</table>
<p><span style="color:#ffffff;">.</span><br>
Some <strong>ip neighbor</strong> examples are as follows:</p>
<p style="padding:2px 6px 4px;color:#555555;background-color:#eeeeee;border:#dddddd 2px solid;"><code># ip n del 10.1.2.3 dev eth0</code></p>
<p>Invalidates the ARP cache entry for host 10.1.2.3 on device <strong>eth0</strong>.</p>
<p style="padding:2px 6px 4px;color:#555555;background-color:#eeeeee;border:#dddddd 2px solid;"><code># ip neighbor show dev eth0</code></p>
<p>Shows the ARP cache for interface <strong>eth0</strong>.</p>
<p style="padding:2px 6px 4px;color:#555555;background-color:#eeeeee;border:#dddddd 2px solid;"><code># ip n add 10.1.2.3 lladdr 1:2:3:4:5:6 dev eth0 nud perm</code></p>
<p>Adds a “permanent” ARP cache entry for host 10.1.2.3 device <strong>eth0</strong>. The Neighbor Unreachability Detection (<strong>nud</strong>) state can be one of the following:</p>
<ul>
<li><strong>noarp</strong> – entry is valid. No attempts to validate this entry will be made but it can be removed when its lifetime expires.</li>
<li><strong>permanent</strong> – entry is valid forever and can be only be removed administratively.</li>
<li><strong>reachable</strong> – entry is valid until the reachability timeout expires.</li>
<li><strong>stale</strong> – entry is valid but suspicious.</li>
</ul>
<p><a name="ifconfig"></a></p>
<h2>Ifconfig</h2>
<table width="820" border="1">
<tbody>
<tr>
<th>
<h3><strong>Deprecated ifconfig commands<br>
</strong></h3>
</th>
<th>
<h3><strong>Replacement</strong></h3>
</th>
</tr>
<tr>
<td style="padding:5px;"><strong>ifconfig</strong><br>
<span style="color:#ffffff;">.</span><br>
Displays details on all network interfaces.</td>
<td style="padding:5px;"><strong>ip a</strong> (or <strong>ip addr</strong>)</td>
</tr>
<tr>
<td style="padding:5px;"><strong>ifconfig [interface]</strong><br>
<span style="color:#ffffff;">.</span><br>
The name of the interface. This is usually a driver name followed by a unit number; for example, <strong>eth0</strong> for the first Ethernet interface. <strong>Eth0</strong> will usually be a PC’s primary network interface card (NIC).</td>
<td style="padding:5px;"><strong>ip a show dev [interface]<br>
</strong></td>
</tr>
<tr>
<td style="padding:5px;"><strong>ifconfig [address_family]</strong><br>
<span style="color:#ffffff;">.</span><br>
To enable the interpretation of differing naming schemes used by various protocols, <strong>[address_family]</strong> is used for decoding and displaying all protocol addresses. Currently supported address families include <strong>inet</strong> (TCP/IP, default), <strong>inet6</strong> (IPv6), <strong>ax25</strong> (AMPR Packet Radio), <strong>ddp</strong> (Appletalk Phase 2), <strong>ipx</strong> (Novell IPX) and <strong>netrom</strong> (AMPR Packet radio).</td>
<td style="padding:5px;"><strong>ip -f [family] a</strong><strong><br>
<span style="color:#ffffff;">.</span><br>
[family]</strong> can be <strong>inet</strong> (IPv4), <strong>inet6</strong> (IPv6), or <strong>link</strong>. Additionally, <strong>-4</strong> = <strong>-f inet</strong> and<strong> -6</strong> = <strong>-f inet6</strong>.</td>
</tr>
<tr>
<td style="padding:5px;"><strong>ifconfig [interface] add [address/prefixlength</strong><br>
<span style="color:#ffffff;">.</span><br>
Adds an IPv6 address to the <strong>[interface]</strong>.</td>
<td style="padding:5px;"><strong>ip a add [ip_addr/mask] dev [interface]</strong></td>
</tr>
<tr>
<td style="padding:5px;"><strong>ifconfig [interface] address [address]<br>
<span style="color:#ffffff;">.</span><br>
</strong>Assigns the specified IP <strong>[address]</strong> to the specified <strong>[interface].</strong></td>
<td style="padding:5px;"><strong>ip a add [ip_addr/mask] dev [interface]</strong></td>
</tr>
<tr>
<td style="padding:5px;"><strong>ifconfig [interface] allmulti </strong>or<strong> -allmulti</strong><br>
<span style="color:#ffffff;">.</span><br>
Enables or disables all-multicast mode. If selected, all multicast packets on the network will be received by the <strong>[interface]</strong> specified. This enables or disables the sending of incoming frames to the kernel’s network layer.</td>
<td style="padding:5px;"><strong>ip mr iif [name]</strong> or <strong>ip mroute iif [name]</strong>, where <strong>[name]</strong> is the interface on which multicast packets are received.</td>
</tr>
<tr>
<td style="padding:5px;"><strong>ifconfig [interface] arp</strong> or <strong>-arp</strong><br>
<span style="color:#ffffff;">.</span><br>
Enables or disables the use of the ARP protocol on this <strong>[interface]</strong>.</td>
<td style="padding:5px;"><strong>ip link set arp on</strong> or <strong>arp off</strong></td>
</tr>
<tr>
<td style="padding:5px;"><strong>ifconfig [interface] broadcast [address]</strong><br>
<span style="color:#ffffff;">.</span><br>
Specifies the address to use to use for broadcast transmissions. By default, the broadcast address for a subnet is the IP address with all ones in the host portion of the subnet address (i.e., <em>a.b.c.255</em> for a /24 subnet).</td>
<td style="padding:5px;"><strong>ip a add broadcast [ip_address]</strong><br>
<span style="color:#ffffff;">.</span><br>
<strong>ip link set dev [interface] broadcast [mac_address]</strong> (sets the link layer broadcast address)</td>
</tr>
<tr>
<td style="padding:5px;"><strong>ifconfig [interface] del [address/prefixlength]</strong><br>
<span style="color:#ffffff;">.</span><br>
Removes an IPv6 address from the <strong>[interface]</strong>, such as <strong>eth0</strong>.</td>
<td style="padding:5px;"><strong>ip a del [ipv6_addr</strong> or <strong>ipv4_addr] dev [interface]</strong></td>
</tr>
<tr>
<td style="padding:5px;"><strong>ifconfig [interface] down</strong><br>
<span style="color:#ffffff;">.</span><br>
Disables the <strong>[interface]</strong>, such as <strong>eth0</strong>.</td>
<td style="padding:5px;"><strong>ip link set dev [interface] down</strong></td>
</tr>
<tr>
<td style="padding:5px;"><strong>ifconfig [interface] hw [class] [address]</strong><br>
<span style="color:#ffffff;">.</span><br>
Sets the hardware (MAC) address of this <strong>[interface]</strong>, if the device driver supports this operation. The keyword <em>must</em> be followed by the name of the hardware <strong>[class]</strong> and the printable ASCII equivalent of the hardware address. Hardware classes currently supported include <strong>ether </strong> (Ethernet), <strong>ax25</strong> (AMPR AX.25), <strong>ARCnet</strong> and <strong>netrom</strong> (AMPR NET/ROM).</td>
<td style="padding:5px;"><strong>ip link set dev [interface] address [mac_addr]</strong></td>
</tr>
<tr>
<td style="padding:5px;"><strong>ifconfig [interface] io_addr [address]</strong><br>
<span style="color:#ffffff;">.</span><br>
Sets the start <strong>[address]</strong> in <a title="I/O Address on TechTerms" href="http://www.techterms.com/definition/ioaddress">I/O space</a> for this device.</td>
<td style="padding:5px;">Not apparent; possibly <strong>ethtool</strong>.</td>
</tr>
<tr>
<td style="padding:5px;"><strong>ifconfig [interface] irq [address]</strong><br>
<span style="color:#ffffff;">.</span><br>
Sets the <a title="IRQ on Wikipedia" href="http://en.wikipedia.org/wiki/Interrupt_request">interrupt line</a> used by the network interface.</td>
<td style="padding:5px;">Not apparent; possibly <strong>ethtool</strong>.</td>
</tr>
<tr>
<td style="padding:5px;"><strong>ifconfig [interface] mem_start [address]</strong><br>
<span style="color:#ffffff;">.</span><br>
Sets the start address for <a title="Shared memory on Wikipedia" href="http://en.wikipedia.org/wiki/Shared_memory">shared memory</a> of the interface.</td>
<td style="padding:5px;">Not apparent; possibly <strong>ethtool</strong>.</td>
</tr>
<tr>
<td style="padding:5px;"><strong>ifconfig [interface] media [type]</strong><br>
<span style="color:#ffffff;">.</span><br>
Sets physical port or medium type. Examples of <strong>[type]</strong> are <strong>10baseT</strong>, <strong>10base2</strong>, and <strong>AUI</strong>. A <strong>[type]</strong> value of <strong>auto</strong> will tell the interface driver to automatically determine the media type (driver support for this command varies).</td>
<td style="padding:5px;">Not apparent; possibly <strong>ethtool</strong>.</td>
</tr>
<tr>
<td style="padding:5px;"><strong>ifconfig [interface] mtu [n]</strong><br>
<span style="color:#ffffff;">.</span><br>
Sets the Maximum Transfer Unit (<a title="MTU on Wikipedia" href="http://en.wikipedia.org/wiki/Maximum_transmission_unit">MTU</a>) of an interface to <strong>[n]</strong>.</td>
<td style="padding:5px;"><strong>ip link set dev [interface] mtu [n]</strong></td>
</tr>
<tr>
<td style="padding:5px;"><strong>ifconfig [interface] multicast</strong><br>
<span style="color:#ffffff;">.</span><br>
Sets the <a title="Multicast addressing on Wikipedia" href="http://en.wikipedia.org/wiki/Multicast_address">multicast flag</a> on the interface (should not normally be needed as the drivers set the flag correctly themselves).</td>
<td style="padding:5px;"><strong>ip link set dev [interface] multicast on</strong> or <strong>off</strong></td>
</tr>
<tr>
<td style="padding:5px;"><strong>ifconfig [interface] netmask [mask_address]</strong><br>
<span style="color:#ffffff;">.</span><br>
Sets the <em>subnet mask</em> (not the IP address) for this <strong>[interface]</strong>. This value defaults to the standard Class A, B, or C subnet masks (based on the interface IP address) but can be changed with this command.<strong><br>
</strong></td>
<td style="padding:5px;">Not apparent</td>
</tr>
<tr>
<td style="padding:5px;"><strong>ifconfig [interface] pointopoint </strong>or<strong> -pointopoint</strong><br>
<span style="color:#ffffff;">.</span><br>
Enables or disables <a title="Point-to-point on Wikipedia" href="http://en.wikipedia.org/wiki/Point-to-point_%28telecommunications%29">point-to-point</a> mode on this <strong>[interface]</strong>.
</td>
<td style="padding:5px;">not apparent; possibly&nbsp;<strong>ipppd [device]</strong>. The command <strong>ip a add peer [address]</strong> specifies the address of the remote endpoint for point-to-point interfaces.</td>
</tr>
<tr>
<td style="padding:5px;"><strong>ifconfig [interface] promisc </strong>or<strong> -promisc</strong><br>
<span style="color:#ffffff;">.</span><br>
Enables or disables <a title="Promiscuous mode on Wikipedia" href="http://en.wikipedia.org/wiki/Promiscuous_mode">promiscuous mode</a> on the <strong>[interface]</strong>.<strong><br>
</strong></td>
<td style="padding:5px;"><strong>ip link set dev [interface] promisc on </strong>or<strong> off</strong></td>
</tr>
<tr>
<td style="padding:5px;"><strong>ifconfig [interface] txquelen [n]</strong><br>
<span style="color:#ffffff;">.</span><br>
Sets the <a title="Transmit queue length" href="http://publib.boulder.ibm.com/infocenter/pseries/v5r3/index.jsp?topic=/com.ibm.aix.prftungd/doc/prftungd/transmit_queues.htm">transmit queue length</a> on the <strong>[interface]</strong>. Smaller values are recommended for connections with high latency (i.e., dial-up modems, ISDN, etc).</td>
<td style="padding:5px;"><strong>ip link set dev [interface] txqueuelen [n]</strong> or <strong>txqlen [n]</strong></td>
</tr>
<tr>
<td style="padding:5px;"><strong>ifconfig [interface] tunnel [address]</strong><br>
<span style="color:#ffffff;">.</span><br>
Creates a Simple Internet Transition (IPv6-in-IPv4) device which tunnels to the IPv4 <strong>[address]</strong> provided.</td>
<td style="padding:5px;"><strong>ip tunnel mode sit</strong> (other possible modes are <strong>ipip</strong> and <strong>gre)</strong>.</td>
</tr>
<tr>
<td style="padding:5px;"><strong>ifconfig [interface] up</strong><br>
<span style="color:#ffffff;">.</span><br>
Activates (enables) the <strong>[interface]</strong> specified.</td>
<td style="padding:5px;"><strong>ip link set [interface] up</strong></td>
</tr>
</tbody>
</table>
<p><span style="color:#ffffff;">.</span><br>
Some examples illustrating the <strong>ip</strong> command are as follows; using the table above you should be able to figure out what they do.</p>
<p style="padding:2px 6px 4px;color:#555555;background-color:#eeeeee;border:#dddddd 2px solid;"><code># ip link show dev eth0<br>
<br>
# ip a add 10.11.12.13/8 dev eth0<br>
<br>
# ip link set dev eth0 up<br>
<br>
# ip link set dev eth0 mtu 1500<br>
<br>
# ip link set dev eth0 address 00:70:b7:d6:cd:ef</code></p>
<p><a name="iptunnel"></a></p>
<h2>Iptunnel</h2>
<table width="820" border="1">
<tbody>
<tr>
<th>
<h3><strong>Deprecated iptunnel commands</strong></h3>
</th>
<th>
<h3><strong>Replacement<br>
</strong></h3>
</th>
</tr>
<tr>
<td style="padding:5px;"><strong>iptunnel [add | change | del | show]</strong></td>
<td style="padding:5px;"><strong>ip tunnel a</strong> or <strong>add</strong><br>
<strong>ip tunnel chg</strong> or <strong>change</strong><br>
<strong>ip tunnel d</strong> or <strong>del</strong><br>
<strong>ip tunnel ls</strong> or <strong>show</strong></td>
</tr>
<tr>
<td style="padding:5px;"><strong>iptunnel add&nbsp;[name] [mode {ipip | gre | sit} ] remote [remote_addr] local [local_addr]</strong></td>
<td style="padding:5px;"><strong>ip tunnel add [name] [mode {ipip | gre | sit | isatap | ip6in6 | ipip6 | any }] remote [remote_addr] local [local_addr]</strong></td>
</tr>
<tr>
<td style="padding:5px;"><strong>iptunnel -V</strong> or <strong><code>--</code>version</strong></td>
<td style="padding:5px;">not apparent</td>
</tr>
</tbody>
</table>
<p><span style="color:#ffffff;">.</span><br>
The syntax between <strong>iptunnel</strong> and <strong>ip tunnel</strong> is very similar as these examples show.</p>
<p style="padding:2px 6px 4px;color:#555555;background-color:#eeeeee;border:#dddddd 2px solid;"><code># [iptunnel | ip tunnel] add ipip-tunl1 mode ipip remote 83.240.67.86</code> (<em>ipip-tunl1</em> is the name of the tunnel, 83.240.67.86 is the IP address of the remote endpoint).<br>
<br>
<code># [iptunnel | ip tunnel] add ipi-tunl2 mode ipip remote 104.137.4.160 local 104.137.4.150 ttl 1<br>
<br>
#&nbsp;[iptunnel | ip tunnel] add gre-tunl1 mode gre remote 192.168.22.17 local 192.168.10.21 ttl 255</code></p>
<p><strong>Iptunnel</strong> is covered in more depth <a href="http://www.deepspace6.net/docs/iproute2tunnel-en.html">here</a>.</p>
<p><a name="iwconfig"></a></p>
<h2>Iwconfig</h2>
<p><strong>Iwconfig’s</strong> successor, <strong>iw</strong>, is still in development. Official documentation for <strong>iw</strong> is available <a href="http://linuxwireless.org/en/users/Documentation/iw">here</a> and <a href="http://linuxwireless.org/en/users/Documentation/iw/replace-iwconfig">here</a>.</p>
<table width="820" border="1">
<tbody>
<tr>
<th>
<h3><strong>Deprecated iwconfig commands</strong></h3>
</th>
<th>
<h3><strong>Replacement</strong></h3>
</th>
</tr>
<tr>
<td style="padding:5px;"><strong>iwconfig</strong><br>
<span style="color:#ffffff;">.</span><br>
Displays basic details about wireless interfaces, such as supported protocols (<a title="802.11 on Wikipedia" href="http://en.wikipedia.org/wiki/IEEE_802.11">802.11a/b/g/n</a>), Extended Service Set ID (<a title="Service Set Identifier on Wikipedia" href="http://en.wikipedia.org/wiki/Service_set_%28802.11_network%29">ESSID</a>), mode, and access point. To view these details about a particular interface, use <strong>iwconfig [interface]</strong> where the interface is the device name, such as <strong>wlan0</strong>.</td>
<td style="padding:5px;"><strong>iw dev [interface] link</strong></td>
</tr>
<tr>
<td style="padding:5px;"><strong>iwconfig [interface] ap [address]</strong><br>
<span style="color:#ffffff;">.</span><br>
Forces the wireless adapter to register with the access point given by the <strong>[address]</strong>, if possible. This address is the cell identity of the access point (as reported by wireless scanning) which may be different from its MAC address.</td>
<td style="padding:5px;">Not apparent</td>
</tr>
<tr>
<td style="padding:5px;"><strong>iwconfig commit</strong><br>
<span style="color:#ffffff;">.</span><br>
Some wireless adapters may not apply changes immediately (they may wait to aggregate the changes, or apply them only when the card is brought up via <strong>ifconfig</strong>). This command (when available) forces the adapter to immediately apply all pending changes.</td>
<td style="padding:5px;">Not apparent</td>
</tr>
<tr>
<td style="padding:5px;"><strong>iwconfig [interface] essid [name]</strong><br>
<span style="color:#ffffff;">.</span><br>
Connects to the WLAN with the ESSID <strong>[name]</strong> provided. With some wireless adapters, you can disable the ESSID checking (ESSID promiscuous) with <strong>off</strong> or <strong>any</strong> (and <strong>on</strong> to re-enable it).</td>
<td style="padding:5px;"><strong>iw [interface] connect [name]</strong></td>
</tr>
<tr>
<td style="padding:5px;"><strong>iwconfig [interface] frag [num]</strong><br>
<span style="color:#ffffff;">.</span><br>
Sets the maximum fragment size which is always lower than the maximum packet size. This parameter may also control Frame Bursting available on some wireless adapters (the ability to send multiple IP packets together). This mechanism would be enabled if the fragment size is larger than the maximum packet size. Other valid frag parameters to <strong>auto</strong>, <strong>on</strong>, and <strong>off</strong>.</td>
<td style="padding:5px;">Not apparent</td>
</tr>
<tr>
<td style="padding:5px;"><strong>iwconfig [interface] [freq | channel]</strong><br>
<span style="color:#ffffff;">.</span><br>
Sets the operating frequency or channel on the wireless device. A value below 1000 indicates a channel number, a value greater than 1000 is a frequency in Hz. You can append the suffix <strong>k</strong>, <strong>M</strong> or <strong>G</strong> to the value (for example, “2.46G” for 2.46 GHz frequency). You may also use<em></em> <strong>off</strong> or <strong>auto</strong> to let the adapter pick up the best channel (when supported).</td>
<td style="padding:5px;"><strong>iw dev [interface] set freq [freq] [HT20|HT40+|HT40-]</strong><br>
<span style="color:#ffffff;">.</span><br>
<strong>iw dev [interface] set channel [chan] [HT20|HT40+|HT40-]</strong></td>
</tr>
<tr>
<td style="padding:5px;"><strong>iwconfig [interface] key [key] [mode] [on | off]</strong><br>
<span style="color:#ffffff;">.</span><br>
To set the current encryption <strong>[key]</strong>, just enter the key in <em>hex</em> digits as XXXX-XXXX-XXXX-XXXX or XXXXXXXX. You can also enter the key as an ASCII string by using the <strong>s: </strong>prefix. <strong>On</strong> and <strong>off</strong> re=enable and disable encryption. The security mode may be <strong>open</strong> or <strong>restricted</strong>, and its meaning depends on the card used. With most cards, in <strong>open</strong> mode no authentication is used and the card may also accept non-encrypted sessions, whereas in <strong>restricted</strong> mode only encrypted sessions are accepted and the card will use authentication if available.</td>
<td style="padding:5px;"><strong>iw [interface] connect [name] keys [key] </strong>(for WEP)<br>
<span style="color:#ffffff;">.</span><br>
To connect to an AP with WPA or WPA2 encryption, you must use <a href="http://wireless.kernel.org/en/users/Documentation/wpa_supplicant">wpa_supplicant</a>.<strong><br>
</strong></td>
</tr>
<tr>
<td style="padding:5px;"><strong>iwconfig [interface] mode [mode]</strong><br>
<span style="color:#ffffff;">.</span><br>
Sets the operating mode of the wireless device. The <strong>[mode]</strong> can be <strong>Ad-Hoc</strong>, <strong>Auto</strong>, <strong>Managed</strong>, <strong>Master</strong>, <strong>Monitor, Repeater</strong>, or <strong>Secondary</strong>.<strong><br>
<span style="color:#ffffff;">.</span><br>
Ad-Hoc</strong>: the network is composed of only one cell and without an access point.<br>
<strong>Managed</strong>: the wireless node connects to a network composed of many access points, with roaming.<br>
<strong>Master</strong>: the wireless node is the synchronization master, or it acts as an access point.<br>
<strong>Monitor</strong>: the wireless node is not associated with any cell and passively monitors all packets on the frequency.<br>
<strong>Repeater</strong>: the wireless node forwards packets between other wireless nodes.<br>
<strong>Secondary</strong>: the wireless node acts as a backup master/repeater.</td>
<td style="padding:5px;">Not apparent</td>
</tr>
<tr>
<td style="padding:5px;"><strong>iwconfig [interface] modu [modulation]</strong><br>
<span style="color:#ffffff;">.</span><br>
Forces the wireless adapter to use a specific set of modulations. Modern adapters support various modulations, such as 802.11b or 802.11g. The list of available modulations depends on the adapter/driver and can be displayed using <strong>iwlist modulation</strong>. Some options are <strong>11g</strong>, <strong>CCK OFDMa</strong>, and <strong>auto</strong>.</td>
<td style="padding:5px;">Not apparent</td>
</tr>
<tr>
<td style="padding:5px;"><strong>iwconfig [interface] nick [name]</strong><br>
<span style="color:#ffffff;">.</span><br>
Sets the nick name (or station name).</td>
<td style="padding:5px;">Not apparent</td>
</tr>
<tr>
<td style="padding:5px;"><strong>iwconfig [interface] nwid [name]<br>
<span style="color:#ffffff;">.</span><br>
</strong>Sets the Network ID for the WLAN. <em>This parameter is only used for pre-802.11 hardware</em> as the 802.11 protocol uses the ESSID and access point address for this function. With some wireless adapters, you can disable the Network ID checking (NWID promiscuous) with <strong>off</strong><em></em> (and <strong>on</strong> <em></em>to re-enable it).</td>
<td style="padding:5px;">Not apparent</td>
</tr>
<tr>
<td style="padding:5px;"><strong>iwconfig [interface] power [option]</strong><br>
<strong>iwconfig [interface] power min | max [secondsu | secondsm]</strong><br>
<strong>iwconfig [interface] power mode [mode]</strong><br>
<strong>iwconfig [interface] power on | off</strong><br>
<span style="color:#ffffff;">.</span><br>
Configures the power management scheme and mode. Valid <strong>[options]</strong> are: <strong>period [value]</strong> (sets the period between wake ups), <strong>timeout [value]</strong> (sets the timeout before going back to sleep), <strong>saving [value]</strong> (sets the generic level of power saving).<br>
The <strong>min</strong> and <strong>max</strong> modifiers are in seconds by default, but append the suffices <strong>m</strong> or <strong>u</strong> to specify values in milliseconds or microseconds.<br>
Valid <strong>[mode]</strong> options are: <strong>all</strong> (receive all packets), <strong>unicast</strong> (receive unicast packets only, discard multicast and broadcast) and <strong>multicast</strong> (receive multicast and broadcast only, discard unicast packets).<br>
<strong>On</strong> and <strong>off</strong> re-enable or disable power management.</td>
<td style="padding:5px;">Not apparent; some power commands are:<br>
<span style="color:#ffffff;">.</span><br>
<strong>iw dev [interface] set power_save on</strong><br>
<span style="color:#ffffff;">.</span><br>
<strong>iw dev [interface] get power_save</strong></td>
</tr>
<tr>
<td style="padding:5px;"><strong>iwconfig [interface] rate/bit [rate]</strong><br>
<span style="color:#ffffff;">.</span><br>
Sets the bit rate in bits per second for cards supporting multiple bit rates. The bit-rate is the speed at which bits are transmitted over the medium, the user speed of the link is lower due to medium sharing and various overhead.Suffixes <strong>k</strong>, <strong>M</strong> or <strong>G</strong> can be added to the numeric <strong>[rate]</strong> (decimal multiplier : 10^3, 10^6 and 10^9 b/s), or add ‘<strong>0</strong>‘ for enough. The <strong>[rate]</strong> can also be <strong>auto</strong> to select automatic bit-rate mode (fallback to lower rate on noisy channels), or <strong>fixed</strong> to revert back to fixed setting. If you specify a bit-rate numeric value and append <strong>auto</strong>, the driver will use all bit-rates lower and equal than this value.</td>
<td style="padding:5px;"><strong>iw [interface] set bitrates legacy-2.4 12 18 24</strong></td>
</tr>
<tr>
<td style="padding:5px;"><strong>iwconfig [interface] retry [option] [value]</strong><br>
<span style="color:#ffffff;">.</span><br>
To set the maximum number of retries (MAC retransmissions), enter <strong>limit [value]</strong>. To set the maximum length of time the MAC should retry, enter <strong>lifetime [value]</strong>. By default, this value is in seconds; append the suffices <strong>m</strong> or <strong>u</strong> to specify values in milliseconds or microseconds. You can also add the <strong>short</strong>, <strong>long</strong>, <strong>min</strong> and <strong>max</strong> modifiers.</td>
<td style="padding:5px;">Not apparent</td>
</tr>
<tr>
<td style="padding:5px;"><strong>iwconfig [interface] rts [threshold]</strong><br>
<span style="color:#ffffff;">.</span><br>
Sets the size of the smallest packet for which the node sends RTS; a value equal to the maximum packet size disables the mechanism. You may also set the threshold parameter to <strong>auto</strong>, <strong>fixed</strong> or <strong>off</strong>.</td>
<td style="padding:5px;">Not apparent</td>
</tr>
<tr>
<td style="padding:5px;"><strong>iwconfig [interface] sens [threshold]</strong><br>
<span style="color:#ffffff;">.</span><br>
Sets the sensitivity threshold (defines how sensitive the wireless adapter is to poor operating conditions such as low signal, signal interference, etc). Modern adapter designs seem to control these thresholds automatically.</td>
<td style="padding:5px;">Not apparent</td>
</tr>
<tr>
<td style="padding:5px;"><strong>iwconfig [interface] txpower [value]</strong><br>
<span style="color:#ffffff;">.</span><br>
For adapters supporting multiple transmit powers, this sets the transmit power in dBm. If <strong>W</strong> is the power in Watt, the power in dBm is P = 30 + 10.log(W). If the <strong>[value]</strong> is postfixed by <strong>mW</strong>, it will be automatically converted to dBm. In addition, <strong>on</strong> and <strong>off</strong> enable and disable the radio, and <strong>auto</strong> and <strong>fixed</strong> enable and disable power control (if those features are available).</td>
<td style="padding:5px;"><strong>iw dev [interface] set txpower [auto | fixed | |limit] [tx power in mBm]</strong><br>
<span style="color:#ffffff;">.</span><br>
<strong>iw phy [phyname] set txpower [auto | fixed | limit] [tx power in mBm]</strong></td>
</tr>
<tr>
<td style="padding:5px;"><strong>iwconfig <code>--</code>help</strong><br>
<span style="color:#ffffff;">.</span><br>
Displays the iwconfig help message.</td>
<td style="padding:5px;"><strong>iw help</strong></td>
</tr>
<tr>
<td style="padding:5px;"><strong>iwconfig <code>--</code>version</strong><br>
<span style="color:#ffffff;">.</span><br>
Displays the version of iwconfig installed.</td>
<td style="padding:5px;"><strong>iw <code>--</code>version</strong></td>
</tr>
</tbody>
</table>
<p><span style="color:#ffffff;">.</span><br>
Some examples of the <strong>iw</strong> command syntax are as follows.</p>
<p style="padding:2px 6px 4px;color:#555555;background-color:#eeeeee;border:#dddddd 2px solid;"><code># iw dev wlan0 link<br>
<br>
# iw wlan0 connect CoffeeShopWLAN<br>
<br>
# iw wlan0 connect HomeWLAN keys 0:abcde d:1:0011223344</code> (for WEP)</p>
<p><a name="nameif"></a></p>
<h2>Nameif</h2>
<table width="820" border="1">
<tbody>
<tr>
<th>
<h3><strong>Deprecated nameif commands</strong></h3>
</th>
<th>
<h3><strong>Replacement</strong></h3>
</th>
</tr>
<tr>
<td style="padding:5px;"><strong>nameif [name] [mac_address]</strong><br>
<span style="color:#ffffff;">.</span><br>
If no name and MAC address are provided, it attempts to read addresses from <code>/etc/mactab</code>. Each line of <code>mactab</code> should contain an interface name and MAC address (or comments starting with #).</td>
<td style="padding:5px;"><strong>ip link set dev [interface] name [name]<br>
<span style="color:#ffffff;">.</span><br>
ifrename -i [interface] -n [newname]<br>
</strong></td>
</tr>
<tr>
<td style="padding:5px;"><strong>nameif -c [config_file]</strong><br>
<span style="color:#ffffff;">.</span><br>
Reads from <strong>[config_file]</strong> instead of <code>/etc/mactab</code>.</td>
<td style="padding:5px;"><strong>ifrename -c [config_file]</strong></td>
</tr>
<tr>
<td style="padding:5px;"><strong>nameif -s</strong><br>
<span style="color:#ffffff;">.</span><br>
Error messages are sent to the syslog.</td>
<td style="padding:5px;">Not apparent</td>
</tr>
</tbody>
</table>
<p><a name="netstat"></a></p>
<h2>Netstat</h2>
<table width="820" border="1">
<tbody>
<tr>
<th>
<h3><strong>Deprecated netstat commands</strong></h3>
</th>
<th>
<h3><strong>Replacement</strong></h3>
</th>
</tr>
<tr>
<td style="padding:5px;"><strong>netstat -a </strong>or<strong> <code>--</code>all</strong><br>
<span style="color:#ffffff;">.<strong><br>
</strong></span>Shows both listening and non-listening <a title="Sockets on Wikipedia" href="http://en.wikipedia.org/wiki/Internet_socket">sockets</a>.<strong><br>
</strong></td>
<td style="padding:5px;"><strong>ss -a </strong>or<strong> <code>--</code>all</strong></td>
</tr>
<tr>
<td style="padding:5px;"><strong>netstat -A </strong> <strong>[family]</strong> or<strong> <code>--</code>protocol=[family]</strong><br>
<span style="color:#ffffff;">.</span><br>
Specifies the address families for which connections are to be shown. <strong>[family]</strong> is a comma separated list of address family keywords like <strong>inet</strong>, <strong>unix</strong>, <strong>ipx</strong>, <strong>ax25</strong>, <strong>netrom</strong>, and <strong>ddp</strong>. This has the same effect as using the <strong><code>--</code>inet</strong>, <strong><code>--</code>unix (-x)</strong>, <strong><code>--</code>ipx</strong>, <strong><code>--</code>ax25</strong>, <strong><code>--</code>netrom</strong>, and <strong><code>--</code>ddp</strong> options.</td>
<td style="padding:5px;"><strong>ss -f [family]</strong> or <strong>–family=[family]</strong><br>
<span style="color:#ffffff;">.</span><br>
Families: <strong>unix</strong>, <strong>inet</strong>, <strong>inet6</strong>, <strong>link</strong>, <strong>netlink</strong>.</td>
</tr>
<tr>
<td style="padding:5px;"><strong>netstat -c</strong> or <strong><code>--</code>continuous</strong><br>
<span style="color:#ffffff;">.</span><br>
Configures <strong>netstat</strong> to refresh the displayed information every second until stopped.</td>
<td style="padding:5px;">Not apparent</td>
</tr>
<tr>
<td style="padding:5px;"><strong>netstat -C</strong><br>
<span style="color:#ffffff;">.</span><br>
Prints routing information from the route cache.</td>
<td style="padding:5px;"><strong>ip route list cache</strong></td>
</tr>
<tr>
<td style="padding:5px;"><strong>netstat -e</strong> or <strong><code>--</code>extend</strong><br>
<span style="color:#ffffff;">.</span><br>
Displays an increased level of detail. Can be entered as twice (as <strong><code>--</code>ee</strong>) for maximum details.</td>
<td style="padding:5px;"><strong>ss -e</strong> or <strong><code>--</code>extended</strong></td>
</tr>
<tr>
<td style="padding:5px;"><strong>netstat -F</strong><br>
<span style="color:#ffffff;">.</span><br>
Prints routing information from the forward information database (<a title="Forward Information Database on Wikipedia" href="http://en.wikipedia.org/wiki/Forwarding_information_base">FIB</a>).</td>
<td style="padding:5px;">Not apparent</td>
</tr>
<tr>
<td style="padding:5px;"><strong>netstat -g</strong> or <strong><code>--</code>groups</strong><br>
<span style="color:#ffffff;">.</span><br>
Displays multicast group membership information for IPv4 and IPv6.</td>
<td style="padding:5px;"><strong>ip maddr</strong>, <strong>ip maddr show [interface]</strong></td>
</tr>
<tr>
<td style="padding:5px;"><strong>netstat -i </strong>or<strong> <code>--</code>interface=[name]</strong><br>
<span style="color:#ffffff;">.</span><br>
Displays a table of all network interfaces, or the specified<strong> [name].<br>
</strong></td>
<td style="padding:5px;"><strong>ip -s link</strong></td>
</tr>
<tr>
<td style="padding:5px;"><strong>netstat -l </strong>or<strong> <code>--</code>listening</strong><br>
<span style="color:#ffffff;">.</span><br>
Shows only listening sockets (which are omitted by <strong>netstat</strong> be default).</td>
<td style="padding:5px;"><strong>ss -l </strong>or<strong> <code>--</code>listening</strong></td>
</tr>
<tr>
<td style="padding:5px;"><strong>netstat -M</strong> or <strong><code>--</code>masquerade</strong><br>
<span style="color:#ffffff;">.</span><br>
Displays a list of <a title="NAT on Wikipedia" href="http://en.wikipedia.org/wiki/Network_address_translation">masqueraded</a> connections (connections being altered by Network Address Translation).</td>
<td style="padding:5px;">Not apparent</td>
</tr>
<tr>
<td style="padding:5px;"><strong>netstat -n </strong>or<strong> <code>--</code>numeric</strong><br>
<span style="color:#ffffff;">.</span><br>
Show numerical addresses instead of trying to determine symbolic host, port or user names (skips DNS translation).</td>
<td style="padding:5px;"><strong>ss -n</strong> or <strong><code>--</code>numeric</strong></td>
</tr>
<tr>
<td style="padding:5px;"><strong>netstat <code>--</code>numeric-hosts</strong><br>
<span style="color:#ffffff;">.</span><br>
Shows numerical host addresses but does not affect the resolution of port or user names.</td>
<td style="padding:5px;">Not apparent</td>
</tr>
<tr>
<td style="padding:5px;"><strong>netstat <code>--</code>numeric ports</strong><br>
<span style="color:#ffffff;">.</span><br>
Shows numerical port numbers but does not affect the resolution of host or user names.</td>
<td style="padding:5px;">Not apparent</td>
</tr>
<tr>
<td style="padding:5px;"><strong>netstat <code>--</code>numeric-users</strong><br>
<span style="color:#ffffff;">.</span><br>
Shows numerical user IDs but does not affect the resolution of host or port names.</td>
<td style="padding:5px;">Not apparent</td>
</tr>
<tr>
<td style="padding:5px;"><strong>netstat -N</strong> or <strong><code>--</code>symbolic</strong><br>
<span style="color:#ffffff;">.</span><br>
Displays the symbolic host, port, or user names instead of numerical representations. <strong>Netstat</strong> does this by default.</td>
<td style="padding:5px;"><strong>ss -r</strong> or <strong><code>--</code>resolve</strong></td>
</tr>
<tr>
<td style="padding:5px;"><strong>netstat -o</strong> or <strong><code>--</code>timers</strong><br>
<span style="color:#ffffff;">.</span><br>
Includes information related to networking timers.</td>
<td style="padding:5px;"><strong>ss -o</strong> or <strong><code>--</code>options</strong></td>
</tr>
<tr>
<td style="padding:5px;"><strong>netstat -p</strong> or <strong><code>--</code>program</strong><br>
<span style="color:#ffffff;">.</span><br>
Shows the process ID (PID) and name of the program to which each socket belongs.</td>
<td style="padding:5px;"><strong>ss -p</strong></td>
</tr>
<tr>
<td style="padding:5px;"><strong>netstat -r </strong>or<strong> <code>--</code>route</strong><br>
<span style="color:#ffffff;">.</span><br>
Shows the kernel routing tables.</td>
<td style="padding:5px;"><strong>ip route</strong>, <strong>ip route show all</strong></td>
</tr>
<tr>
<td style="padding:5px;"><strong>netstat -s</strong> or<strong> <code>--</code>statistics</strong><br>
<span style="color:#ffffff;">.</span><br>
Displays summary statistics for each protocol.</td>
<td style="padding:5px;"><strong>ss -s</strong></td>
</tr>
<tr>
<td style="padding:5px;"><strong>netstat -t </strong>or<strong> <code>--</code>tcp</strong><br>
<span style="color:#ffffff;">.</span><br>
Filters results to display TCP only.</td>
<td style="padding:5px;"><strong>ss -t </strong>or<strong> <code>--</code>tcp</strong></td>
</tr>
<tr>
<td style="padding:5px;"><strong>netstat -T </strong>or<strong> <code>--</code>notrim</strong><br>
<span style="color:#ffffff;">.</span><br>
Stops trimming long addresses.</td>
<td style="padding:5px;">Not apparent</td>
</tr>
<tr>
<td style="padding:5px;"><strong>netstat -u </strong>or<strong> <code>--</code>udp</strong><br>
<span style="color:#ffffff;">.</span><br>
Filters results to display UDP only.</td>
<td style="padding:5px;"><strong>ss -u </strong>or<strong> <code>--</code>udp</strong></td>
</tr>
<tr>
<td style="padding:5px;"><strong>netstat -v </strong>or<strong> <code>--</code>verbose</strong><br>
<span style="color:#ffffff;">.</span><br>
Produces verbose output.</td>
<td style="padding:5px;">Not apparent</td>
</tr>
<tr>
<td style="padding:5px;"><strong>netstat -w</strong> or <strong><code>--</code>raw</strong><br>
<span style="color:#ffffff;">.</span><br>
Filter results to display <a title="Raw sockets on Wikipedia" href="http://en.wikipedia.org/wiki/Raw_socket">raw sockets</a> only.</td>
<td style="padding:5px;"><strong>ss-w</strong> or <strong><code>--</code>raw</strong></td>
</tr>
<tr>
<td style="padding:5px;"><strong>netstat -Z </strong>or<strong> <code>--</code>context</strong><br>
<span style="color:#ffffff;">.</span><br>
Prints the <a title="SELinux on Wikipedia" href="http://en.wikipedia.org/wiki/Security-Enhanced_Linux">SELinux</a> context if SELinux is enabled. On hosts running SELinux, all processes and files are labeled in a way that represents security-relevant information. This information is called the SELinux context.</td>
<td style="padding:5px;">Not apparent</td>
</tr>
</tbody>
</table>
<p><a name="route"></a></p>
<h2>Route</h2>
<table width="820" border="1">
<tbody>
<tr>
<th>
<h3><strong>Deprecated route commands</strong></h3>
</th>
<th>
<h3><strong>Replacement</strong></h3>
</th>
</tr>
<tr>
<td style="padding:5px;"><strong>route</strong><br>
<span style="color:#ffffff;">.</span><br>
Displays the host’s routing tables.</td>
<td style="padding:5px;"><strong>ip route</strong></td>
</tr>
<tr>
<td style="padding:5px;"><strong>route -A [family] [add]</strong> or<strong> route <code>--</code>[family] [add]</strong><br>
<span style="color:#ffffff;">.</span><br>
Uses the specified address family with <strong>add</strong> or <strong>del</strong>. Valid families are <strong>inet</strong> (DARPA Internet), <strong>inet6</strong> (IPv6), <strong>ax25</strong> (AMPR AX.25), <strong>netrom</strong> (AMPR NET/ROM), <strong>ipx</strong> (Novell IPX), <strong>ddp</strong> (Appletalk DDP), and <strong>x25</strong> (CCITT X.25).</td>
<td style="padding:5px;"><strong>ip -f [family] route</strong><br>
<span style="color:#ffffff;">.</span><br>
<strong>[family]</strong> can be <strong>inet</strong> (IP), <strong>inet6</strong> (IPv6), or <strong>link</strong>. Additionally, <strong>-4</strong> = <strong>-f inet</strong> and<strong> -6</strong> = <strong>-f inet6</strong>.</td>
</tr>
<tr>
<td style="padding:5px;"><strong>route -C </strong>or<strong> <code>--</code>cache</strong><br>
<span style="color:#ffffff;">.</span><br>
Operates on the kernel’s routing cache instead of the forwarding information base (<a title="FIB on Wikipedia" href="http://en.wikipedia.org/wiki/Forwarding_information_base">FIB</a>) routing table.</td>
<td style="padding:5px;">Not apparent; <strong>ip route show cache</strong> dumps the routing cache.</td>
</tr>
<tr>
<td style="padding:5px;"><strong>route -e </strong>or<strong> -ee</strong><br>
<span style="color:#ffffff;">.</span><br>
Uses the <strong>netstat-r</strong> format to display the routing table. <strong>-ee</strong> will generate a very long line with all parameters from the routing table.</td>
<td style="padding:5px;"><strong>ip route show</strong></td>
</tr>
<tr>
<td style="padding:5px;"><strong>route -F </strong>or<strong> <code>--</code>fib</strong><br>
<span style="color:#ffffff;">.</span><br>
Operates on the kernel’s Forwarding Information Base (<a title="FIB on Wikipedia" href="http://en.wikipedia.org/wiki/Forwarding_information_base">FIB</a>) routing table (default behavior).</td>
<td style="padding:5px;">Not apparent</td>
</tr>
<tr>
<td style="padding:5px;"><strong>route -h </strong>or<strong> <code>--</code>help</strong><br>
<span style="color:#ffffff;">.</span><br>
Prints the help message.</td>
<td style="padding:5px;"><strong>ip route help</strong></td>
</tr>
<tr>
<td style="padding:5px;"><strong>route -n</strong><br>
<span style="color:#ffffff;">.</span><br>
Shows numerical IP addresses and bypass host name resolution.</td>
<td style="padding:5px;">Not apparent</td>
</tr>
<tr>
<td style="padding:5px;"><strong>route -v </strong>or<strong> <code>--</code>verbose</strong><br>
<span style="color:#ffffff;">.</span><br>
Enables verbose command output.</td>
<td style="padding:5px;"><strong>ip -s route</strong></td>
</tr>
<tr>
<td style="padding:5px;"><strong>route -V </strong>or<strong> <code>--</code>version</strong><br>
<span style="color:#ffffff;">.</span><br>
Dispays the version of <strong>net-tools</strong> and the <strong>route</strong> command.</td>
<td style="padding:5px;"><strong>ip -V</strong></td>
</tr>
<tr>
<td style="padding:5px;"><strong>route add </strong>or<strong> del</strong><br>
<span style="color:#ffffff;">.</span><br>
Adds or delete a route in the routing table.</td>
<td style="padding:5px;"><strong>ip route [add | chg | repl | del] [ip_addr] via [ip_addr]</strong></td>
</tr>
<tr>
<td style="padding:5px;"><strong>route [add </strong>or<strong> del]</strong> <strong>dev [interface]</strong><br>
<span style="color:#ffffff;">.</span><br>
Associates a route with a specific device. If <strong>dev [interface]</strong> is the last option on the command line, the word dev may be omitted.</td>
<td style="padding:5px;"><strong>ip route&nbsp;[add | chg | repl | del] dev [interface]</strong></td>
</tr>
<tr>
<td style="padding:5px;"><strong>route [add </strong>or<strong> del] [default] gw [gw]</strong><br>
<span style="color:#ffffff;">.</span><br>
Routes packets through the specified gateway IP address.</td>
<td style="padding:5px;"><strong>ip route add default via [gw]</strong></td>
</tr>
<tr>
<td style="padding:5px;"><strong>route [add </strong>or<strong> del] -host</strong><br>
<span style="color:#ffffff;">.</span><br>
Specifies that the target is a host (not a network).</td>
<td style="padding:5px;">Not apparent</td>
</tr>
<tr>
<td style="padding:5px;"><strong>route [add </strong>or<strong> del] -irtt [n]</strong><br>
<span style="color:#ffffff;">.</span><br>
Sets the initial round trip time (<a title="Round Trip Time on Wikipedia" href="http://en.wikipedia.org/wiki/Round-trip_delay_time">IRTT</a>) for TCP connections over this route to <strong>[n]</strong> milliseconds (1-12000). This is typically only used on AX.25 networks. If omitted the <a title="RFC 1122" href="http://www.rfc-editor.org/info/rfc1122">RFC 1122</a> default of 300ms is used.</td>
<td style="padding:5px;">Not apparent; <strong>ip route [add | chg | repl | del] rtt [number]</strong> sets the RTT estimate; <strong>rttvar [number]</strong> sets the initial RTT variance estimate.</td>
</tr>
<tr>
<td style="padding:5px;"><strong>route [add </strong>or<strong> del] -net</strong><br>
<span style="color:#ffffff;">.</span><br>
Specifies that the target is a network (not a host).<strong><br>
</strong></td>
<td style="padding:5px;">Not apparent</td>
</tr>
<tr>
<td style="padding:5px;"><strong>route [add</strong> or <strong>del]</strong> <strong>[-host</strong> or <strong>-net] netmask [mask]</strong><br>
<span style="color:#ffffff;">.</span><br>
Sets the subnet <strong>[mask]</strong>.</td>
<td style="padding:5px;">Not apparent</td>
</tr>
<tr>
<td style="padding:5px;"><strong>route [add </strong>or<strong> del] metric [n]</strong><br>
<span style="color:#ffffff;">.</span><br>
Sets the metric field in the routing table (used by routing daemons) to the value of <strong>[n]</strong>.
</td>
<td style="padding:5px;"><strong>ip route [add | chg | repl | del]</strong> <strong>metric [number]</strong> or <strong>preference [number]</strong></td>
</tr>
<tr>
<td style="padding:5px;"><strong>route [add </strong>or<strong> del]</strong> <strong>mod, dyn, </strong>or<strong> reinstate</strong><br>
<span style="color:#ffffff;">.</span><br>
Install a dynamic or modified route. These flags are for diagnostic purposes, and are generally only set by routing daemons.</td>
<td style="padding:5px;">Not apparent</td>
</tr>
<tr>
<td style="padding:5px;"><strong>route [add </strong>or<strong> del] mss [bytes]</strong><br>
<span style="color:#ffffff;">.</span><br>
Sets the TCP Maximum Segment Size (<a title="Maximum segment size on Wikipedia" href="http://en.wikipedia.org/wiki/Maximum_segment_size">MSS</a>) for connections over this route to the number of <strong>[bytes]</strong> specified.</td>
<td style="padding:5px;"><strong>ip route [add | chg | repl | del] advmss [number]</strong> (the MSS to advertise to these destinations when establishing TCP connections).</td>
</tr>
<tr>
<td style="padding:5px;"><strong>route [add </strong>or<strong> del] reject</strong><br>
<span style="color:#ffffff;">.</span><br>
Installs a blocking route, which will force a route lookup to fail. This is used to mask out networks before using the default route. This is not intended to provide firewall functionality.</td>
<td style="padding:5px;"><strong>ip route add prohibit [network_addr]</strong></td>
</tr>
<tr>
<td style="padding:5px;"><strong>route [add </strong>or<strong> del] window [n]</strong><br>
<span style="color:#ffffff;">.</span><br>
Set the <a title="TCP window scaling on Wikipedia" href="http://en.wikipedia.org/wiki/TCP_window_scale_option">TCP window size</a> for connections over this route to the value of <strong>[n]</strong> bytes. This is typically only used on AX.25 networks and with drivers unable to handle back-to-back frames.</td>
<td style="padding:5px;"><strong>ip route [add | chg | repl | del] window [W]</strong></td>
</tr>
</tbody>
</table>
<p><span style="color:#ffffff;">.</span><br>
Some examples of <strong>ip route</strong> command syntax are as follows.</p>
<p style="padding:2px 6px 4px;color:#555555;background-color:#eeeeee;border:#dddddd 2px solid;"><code># ip route add 10.23.30.0/24 via 192.168.8.50<br>
<br>
# ip route del 10.28.0.0/16 via 192.168.10.50 dev eth0<br>
<br>
#&nbsp;ip route chg default via 192.168.25.110 dev eth1<br>
<br>
# ip route get [ip_address]</code> (shows the interface and gateway that would be used to reach a remote host. This command would be especially useful for troubleshooting routing issues on hosts with large routing tables and/or with multiple network interfaces).</p>
<p><a name="discussion"></a></p>










			
			
						</div>

	
</div>



<a name="comments" id="comments"></a>





</div>



</div>
