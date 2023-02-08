tcpdump -i any -n -s "tcp port 2775" -vvv -w /var/log/vm/backup/dumps/smpp_failed_dlr_dump_$(date +%Y%m%d_%H%M%S).pcap - SMPP

 tcpdump -i any -n -s 0 -vvv tcp port 2775 -w /var/log/smpp_failed_dlr_dump_$(date +%Y%m%d_%H%M%S).pcap