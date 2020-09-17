- Networking
    - Pre-Requisites
        - switching
            - two computers, we connect them to a switch, and a switch creates a network containing the two systems
            - we need an interface on each host, physical or virtual depending on the host to see the interfaces for 
        ![image info](switch.jpg)
        - routing
            - a Router helps connect two networks together
            - it gets two IPs assigned, one on each network
            - command
                - ip route add 192.168.2.0/24 via 192.168.1.1
                    - configure a gateway on system B to reach the system on network 192.168.2.0
                - internet
                - ip route add default via 192.168.2.1
                    - this way any request to any network outside of your existing network goes to this particular router
                - ip route add 0.0.0.0 via 192.168.2.1
                    - it doesn't need a gateway because it is in its own network 
                
        - gateway
            - is a door to the outside world to other network
        ![image info](router-gateway.jpg)
        - router-table-eg:
        ![image info](router-table-build-eg.jpg)
            - +forward packets between interfaces is governed by a setting in this system at file /proc/sys/net/ipv4/ip
                - cat /proc/sys/net/ipv4/ip_forward  (0-> no forward 1-> forward)
                - /etc/sysctl.conf
                    - net.ipv4.ip_forward=1