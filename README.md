# Network-Scanner
A network scanner is an important element for a network administrator as well as a penetration tester. It allows the user to map the network to find devices that are connected to the same network.
                                       ( ARP REQUESTS )
                                       
![image](https://user-images.githubusercontent.com/90146929/152850112-586c0d1e-2d27-42f3-83b6-da98d95312d4.png)


#REQUIREMENTS :
1.PYTHON3
2.SCAPY INSTALLED ON YOUR COMPUTER

#CODE :
from scapy.all import ARP, Ether, srp
target_ip = "192.168.1.1/24"
# IP Address for the destination
# create ARP packet
arp = ARP(pdst=target_ip)
# create the Ether broadcast packet
# ff:ff:ff:ff:ff:ff MAC address indicates broadcasting
ether = Ether(dst="ff:ff:ff:ff:ff:ff")
# stack them
packet = ether/arp
result = srp(packet, timeout=3, verbose=0)[0]
# a list of clients, we will fill this in the upcoming loop
clients = []
for sent, received in result:
    # for each response, append ip and mac address to `clients` list
    clients.append({'ip': received.psrc, 'mac': received.hwsrc})
# print clients
print("Available devices in the network:")
print("IP" + " "*18+"MAC")
for client in clients:
    print("{:16}{}".format(client['ip'], client['mac']))
    
    AFTER RUNNING MY DEVICE IP ADDRESS WE GET ,

    
    
    ![PYTHON](https://user-images.githubusercontent.com/90146929/152850587-95d47420-4739-4627-9f54-b9d80dda9ff8.JPG)

    

