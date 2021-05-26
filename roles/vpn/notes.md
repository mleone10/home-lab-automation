# Wireguard Installation Notes

Wireguard is a VPN implementation that should allow me to route all traffic from my phone and Pixelbook through an encrypted tunnel to my home lab. This should have three benefits:

1. No matter where I go, my IP address appears to be my home lab
1. I'll benefit from my home lab's infrastructure, such as PiHole or network storage
1. I'll be able to access and use my lab from anywhere

## Progress Thus Far

I _think_ I have most of this working correctly - at the very least, I'm able to install and start Wireguard on a separate VM on my Proxmox host, and it looks like it's receiving handshake initiation packets from peers on my network.

From there though, things get a bit messier. Depending on the specific configuration I'm tweaking, I'm _sometimes_ able to get a successful handshake between peers and the server. Usually though, the peer just keeps sending handshake initiation packets but never receives the response that the server appears to be sending.

## Notes

Among the many settings and concepts at play that may be involved are the following:

- **iptables** - since I'm running Wireguard on a VM, behind a NATting VM ("net"), on a virtualization host, behind my residential Google Nest Router, there may be something I have to configure on one or more hosts to enable traffic to work correctly.
- **Nginx** - I'm using Nginx as a reverse proxy on my net VM - the one serving as the lab's virtual router. I'm fairly certain that's working fine, but perhaps there's a misconfiguration that's preventing the VPN server's responses from being routed correctly?
- **AllowedIps** - During all of this testing, my peers are always within the same LAN (the outermost Google Nest router). I've read that I might have to customize the Allowed IP addresses at either the server or the peers to ensure that traffic can flow. Then again, maybe that's only required if I _don't_ want interLAN traffic to leave my network.
