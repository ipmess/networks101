---
title: "The show ip route command output"
date: 2024-11-22
---
# The `show ip route` command output

This tutorial explains how to read the output of the `show ip route` command in Cisco IOS. Learn how the routing table organizes the routing information, and how to view it.

The `show ip route` command displays the structure and contents of the routing table. You can use the `show ip route` for the following purposes:

* To list the routing table's entries
* To view how many routes available for a particular destination
* To view the route the router uses to forward data packets for a specific destination
* To know the routes added by a routing protocol
* To know the routes added by the router from the IP configurations
* To view the current status of a route
* To verify and troubleshoot the routing

To use the `show ip route` command, enter privileged-exec mode and run the following command.

````````
#show ip route
````````

The output of this command is organized into three sections. These sections are _Codes_, the _Default route_, and the _Routes_. The following image shows the output of this command.

![The `show ip route` command three sections](/networks101/assets/img/posts/1.show.ip.route.sections.svg)

## Codes

The routing table uses the abbreviated code to store the type of route. The Codes section displays the meaning of each abbreviated code.

## Default route

The Default Route section displays the default route. Cisco IOS calls the default route as `Gateway of last resort`. IOS routers use their routing table's routes to forward IP packets. If there is no route available for the destination address of an IP packet, the router uses the _default route_ to forward the IP packet. If the default route is not set, the router drops (discards) the IP packet.

## Routes

IOS displays all routes from its routing table in the Routes section. To arrange routes, the routing table uses _blocks of classful networks_. Each block contains a classful network and the classless subnets that are part from the classful network. If a classful network is subnetted into small classless networks and the router knows the routes for the classless networks, the routing table uses a heading to group all classless networks of the same classful network.

The routing table uses the heading for a classful network only if it knows more than one route for the classful network. If there is only one route for the classful network, the routing table adds the route without the heading.

The following image shows routes with the heading and without the heading.

![Route block headings in the output of the `show ip route` command](/networks101/assets/img/posts/2.show.ip.route.route.blocks.svg)

The heading includes three things: 

* the classful network, 
* the total number of subnets, and 
* the total number of masks used to create the subnets.

Let's understand these parts:

### The classful network

The routing table organizes routes by classful networks. If a classful network is subnetted into classless subnets and the routes for the subnets are available, the router arranges all the subnets under the classful network.

### Total number of subnets

A router learns routes from various sources. The _total number of subnets_ part shows the total number of routes the router learned from all sources for the classful network. The total number includes all routes for the classful network and all subnets of that same classful network.

When you assign an IP address to the interface, the router automatically creates two routes from the IP configuration and both of these routes to the routing table. The router adds the first route for the subnet of the IP address. The router uses this route to forward IP packets out the particular interface that has this IP address assigned. IOS also adds a second route for the interface's IP address itself. The router uses this /32 route to reach the interface. The router uses the prefix /32 for this route.

![Routes learned from a configured IP address on an interface](/networks101/assets/img/posts/3.show.ip.route.local.config.addresses.svg)

### Total number of masks

The _total number of masks_ section of the header states the total number of _different_ mask lengths used in the routes for all the subnets of the classful network mentioned in the heading.

The routing table uses a heading to organize all routes created from the same classful network into blocks. We have already discussed the things the routing table uses to create the heading. Now let's discuss the block's route entries.

## Legend code

The legend code is the first thing in a route entry. A router can learn a route from various _sources_. The legend code shows the source from which the router learned the route. The routing table displays the legend code in an abbreviated form. The first section of the output of the `show ip route` command shows the meaning of each code.

![Legend code in output and the legends on each route entry](/networks101/assets/img/posts/4.show.ip.route.legend.codes.svg)

### Network address / Subnet mask

Each route points to the next hop on a path to a specific destination. Each route entry includes only one destination network/subnet. After the legend code, the routing table places the destination network address with the subnet mask in the route entry.

![Destination prefix and subnet mask](/networks101/assets/img/posts/5.show.ip.route.masks.svg)

Routers use the routing table to make a forwarding decision. A router compares the destination address of each IP packet to the prefix stored in each entry of the routing table. If the prefix mentioned in an entry matches the destination address of the IP packet, the router forwards the IP packet from the interface or to the next-hop router's IP address mentioned in the matching route entry.

## Administrative Distance(AD)/Metric

![AD and route metric](/networks101/assets/img/posts/6.AD.metric.route.selection.svg)

The routing table stores only one route for each destination subnet. If the router learns more than one route for a destination from different routing information sources, the router adds only the best route to the routing table. To select the best route, the router uses the AD (Administrative Distance) value.

The AD value is the trustworthiness of a _routing information source_. A routing information source with a lower AD value is considered more reliable than a source with a higher AD value.

For example, consider a router that learns two routes for the same destination. The AD value of the first routing information source is 10 and the AD value of the second source is 20. The router will only add the route learned from the first source to the routing table, because the first routing information source's AD is lower.

A router can also learn more than one route from the same source. If the router learns more than one route for a destination from the same source, the router then uses the metric value of the routes as a tiebreaker to select the best route. Sources use their metric to calculate the best route for the destination.

In simple words, a router uses the AD to select the best routing information route learned from different sources and the metric to select the best route learned from the same routing information source.

![Difference between AD and metric](./index/7.show.ip.route.AD.and.metric.svg)

The `show ip route` _`prefix mask`_ command provides more detailed output than the `show ip route` output. For example, below, we can see that  for directly connected routes the AD is 0 (as per the `distance 0` text) and the metric is also 0 (as per the `metric 0` output).

````````
R1#show ip route 10.0.0.0 255.255.255.0
Routing entry for 10.0.0.0/24
  Known via "connected", distance 0, metric 0 (connected, via interface)
  Redistributing via eigrp 1
  Routing Descriptor Blocks:
  * directly connected, via Ethernet0/1
      Route metric is 0, traffic share count is 1
R1#
````````

### The IP address of the next-hop router

Next in the route entry is the IP address of the next-hop router. A router forwards the packet to the next-hop router if the destination address of the IP packet and the address specified in the route entry match.

![Next-hop IP address](/networks101/assets/img/posts/8.show.ip.route.next.hop.IP.addr.svg)

### EIGRP/OSPF Timer

The EIGRP and OSPF routing protocols use a timer for each learned route. If the route is learned by EIGRP or OSPF, the routing protocol includes the timer in the route entry.

![OSPF and EIGRP route timers](/networks101/assets/img/posts/9.show.ip.route.protocol.timers.svg)

### Egress interface

The last information of each route entry shows the local interface that the router uses to forward the IP packet.

![Egress interface](/networks101/assets/img/posts/10.show.ip.route.egress.interface.svg)

#### Reference

The above work was based on the tutorial over at [ComputerNetworkingNotes - The show ip route Command Explained](https://www.computernetworkingnotes.com/ccna-study-guide/the-show-ip-route-command-explained.html)
