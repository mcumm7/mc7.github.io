---
author: Michael Cummings
categories:
- development
date: "2020-03-09"
description: A description of how I built a Unifi network to link two buildings, with seperate intranets.
tags:
- development
- html
- php
title: Website Development
---

This blog describes how I planned and deployed a Unifi-based network solution between two buildings, to increase network performance while decreasing overall cost.
<!--more-->

## Preparation

I began by creating a diagram of the buildings and mapping out where I would need to run CAT 6a cabling. 

{{< figure src="/network-diagram.jpg" caption="My final diagram depicting layout of equipment and cabling." >}}

The network provider is Xfinity. The provided link is 1 Gbps. The Xfinity Xfi gateway is set to *Bridge Mode*, enabling passthrough of the WAN to the USG.

## Hardware

The USG, or Unifi Security Gateway, is the router (or firewall) for this network. It splits the network into two chunks, LAN 1 and LAN 2, used for building 1 and building 2 respectively. The buildings are linked by a high-strength outdoor rated CAT 6a cable. Splitting the network into seperate LAN's provides increased security, without affecting overall thoroughput or cost.

The access points are powered using POE (power over ethernet). To power such a large number of access points, I needed a powerful switch. I opted for the Unifi Switch 8 150W. It provides the number of ports needed as well as the amount of power.

The Unifi Cloud Key Gen2 (UCK-G2) is the "brains" of the network. It is a hosted controller for managing all of the Unifi products. It is powered via POE.

For the access points, I picked the Unifi nanoHD access point. The nanoHD is the successor to the AP AC Pro, providing 4x4 MU-MIMO and 802.11ac Wave 2 capabilities. 

The 3rd floor in building 1 had a special circumstance - they had a lot of devices that would perform much better with a dedicated, wired connection. So, I installed the Unifi Switch 8. Powered by POE, the switch has 7 ports for devices, and one POE port for powering the access point.

## Completion

The depoloyment was successful, and the network has been performing optimally for several months now. Using Unifi's WifiAI, the channel distributions are automatically updated, as needed, in the early hours of the morning.

{{< figure src="/unifi-control-panel.png" caption="The Unifi network control panel." >}}

As you can see in the figure above, the network is operating at 100% stability with 118 clients connected.

