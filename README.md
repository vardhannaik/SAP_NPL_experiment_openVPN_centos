# SAP_NPL_experiment_openVPN_centos
Connecting the SAP developer Edition over OpenVPN

One of the experiments I have successfuly tried is to do a OPENVPN from centos public IP server  over the SUSE VM acting a client, SUSE VM resides on non public IP machine.
1) Step 1: setup NPL SAP Developer Edition https://blogs.sap.com/2019/07/01/as-abap-752-sp04-developer-edition-to-download/
2) Step 2:  Harden Firewall using nftables for both tun0 and eth0 , see my github how to for eth0. https://github.com/vardhannaik/nftables_centos
3) Step 3: Have additional CA authority server, You can use a debian, Centos, Windows should also be possible
https://www.digitalocean.com/community/tutorials/how-to-set-up-and-configure-a-certificate-authority-ca-on-centos-8
4) Step 4: Configure OpenVPN for Centos server && windows as well as Suse VM as clients where NPL is hosted
https://www.digitalocean.com/community/tutorials/how-to-set-up-and-configure-an-openvpn-server-on-centos-8
4b) Ensure client to client peerview is visible
https://serverfault.com/questions/570316/how-can-multiple-clients-of-an-openvpn-server-find-each-other

"# Uncomment this directive to allow different
#clients to be able to "see" each other.
#By default, clients will only see the server.
#To force clients to only see the server, you
#will also need to appropriately firewall the
#server's TUN/TAP interface.
client-to-client

4c) Firewall nftables for tun0 with nat and masquerade for nftables.
esp postrouting and forwarding
https://gist.github.com/itsoli/f2622c878dccba171e5a

A OPENVPN client with individual certificate is much better than port forwarding. Hope this helps SAP community.

So if you have two clients connected to the public IP, SAP NPL is connected.
Example 1: Your Laptop with client id say 10.8.0.10
SuSE VM : your VM hosting NPL with client id say 10.8.0.6

![alt text]https://github.com/vardhannaik/SAP_NPL_experiment_openVPN_centos/blob/main/NPL.JPG?raw=true







