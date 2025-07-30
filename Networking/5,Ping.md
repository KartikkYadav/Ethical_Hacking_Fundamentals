# Ping (Packet InterNet Groper)

- Definition: A network utility that uses ICMP echo request and reply packets to test if a host (computer, server, device) is reachable and to measure round-trip latency.

- How it works:

  - Send ICMP echo request to a specified IP or hostname

  - Wait for ICMP echo reply

  - Report on connectivity, packet loss, and response times

- Main uses and features:

  - Test local or remote network connectivity

  - Diagnose unreachable hosts, routing issues, or firewall blocks

  - nMeasure latency in milliseconds

  - Command-line usage: use ping <address> with adjustable parameters like packet count, size, timeout

- Etymology/misconceptions:

  - Name inspired by sonar “ping”

  - Backronym “Packet InterNet Groper” (sometimes “Gopher”) adopted later as a playful expansion, but not original creator intent

  - The correct term is Packet InterNet Groper, not “Gopher”; the confusion may stem from the unrelated Gopher protocol

Summary:

 - Ping is an essential diagnostic tool for IP connectivity using ICMP echo request/reply; “Gopher” is a misunderstanding if encountered

## Ping sweep (ICMP sweep)

- Definition: Scanning technique that sends ICMP echo requests across a range of IP addresses (e.g. 192.168.1.1–192.168.1.254) to find all live hosts in that subnet

- Typical steps:

   1.Define IP range to scan (e.g. 192.168.1.1–254)

   2.Send ICMP echo requests either sequentially or in parallel

   3.Wait for ICMP echo replies

   4.Record responding addresses (live hosts)

- Key points and considerations:

   - ICMP blocking: Firewalls or routers often block ICMP to prevent reconnaissance or DoS, making sweeps ineffective in protected networks

    - Detection: Excessive or repeated ICMP traffic may trigger IDS/firewall alerts

    - Legal/ethical use: Only perform sweeps on networks where you have permission; unauthorized scanning is often unlawful or considered intrusive

    - Tools: Common tools include fping, nmap ‑sn, SolarWinds Ping Sweep, or shell/batch scripts using ping

- Command examples:

   - Windows:

            ping 192.168.1.1              # check connectivity to a single host

            ping 192.168.1.1 -t           # continuous ping until manually stopped (Ctrl+C)

            ping 192.168.1.1 -n 50        # send exactly 50 echo requests

            ping 192.168.1.1 -l 5000      # specify packet size (5,000 bytes)

            ping 192.168.1.1 -w 2000      # set timeout in ms (default 1000 ms)

            ping 192.168.1.1 -l 5000 -t   # continuous 5,000‑byte pings

    - Linux

            ping 8.8.8.8                      # test connectivity to remote host (Google DNS)
   
            ping 8.8.8.8 -c 2                 # send exactly 2 ICMP requests

            ping 192.168.1.1 -s 65500         # send ping with large packet size (65,500 bytes)

            ping -I eth0 192.168.1.1 -s 65500 -c 4   # send 4 large ICMP packets via specific interface (eth0)

            ping 192.168.1.1 -i 10 -c 2       # send 2 pings at 10‑second intervals

            ping 192.168.1.1 -i 10 -c 2 ‑p 42   # same, with byte pattern 0x42 in packet

            ping armourinfosec.com            # connect via DNS hostname

            ping -6 google.com                # ping an IPv6 hostname

            ping -6 2404:6800:4009:80e::200e -i 10 -c 2 ‑p 42  # ping an IPv6 address with options

            ping 192.168.1.1 ‑f               # flood ping (root/sudo required, Linux)

            ping 192.168.1.1 -f -s 65500      # flood ping using max packet size


   - Notes:

       - -c: count (number of packets)

       - -s: packet size

       - -I: network interface

       - -i: interval between pings (seconds)


      
