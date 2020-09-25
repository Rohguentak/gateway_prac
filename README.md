# gateway_prac

# 노드 정보

           A server : 10.10.1.20
           B server : 10.10.2.20
           gateway  : 10.10.1.10 (eno1)
                      10.10.2.10 (eno2)
          
           ip route add (destination_network/prefix) via (gateway_ip_addr)

# A
           [root@A]# ip route add 10.10.2.0/24 via 10.10.1.0
             
# B
           [root@B]# ip route add 10.10.1.0/24 via 10.10.2.0

# gateway
           [root@gateway]# echo 1 > /proc/sys/net/ipv4/ip_forward
           [root@gateway]# systemctl restart network

           //리눅스에선 기본적으로 보안 이슈때문에 네트워크 인터페이스간 통신을 제한. 
