# Network Configuration

## IP Addressing

The laptop obtains its IP configuration automatically from the home router using DHCP.

The following values are examples for a typical home lab. Actual values may differ depending on the router's configuration.

| Parameter             | Expected / Sample Value |
| --------------------- | ----------------------- |
| Ethernet adapter name | Ethernet                |
| IPv4 address          | `192.168.1.100`         |
| Subnet mask           | `255.255.255.0`         |
| Default gateway       | `192.168.1.1`           |
| DHCP enabled          | Yes                     |
| Preferred DNS server  | `192.168.1.1`           |
| Alternate DNS server  | `1.1.1.1` (optional)    |
| Network address       | `192.168.1.0/24`        |

**Important:** These values assume a home network using the `192.168.1.0/24` subnet. If your router uses `192.168.0.1` or another subnet, record the values actually assigned to your laptop. Do not change your network settings just to match these examples.

## Commands and Expected Results

| Command                | Expected result                                                                    |
| ---------------------- | ---------------------------------------------------------------------------------- |
| `ipconfig /all`        | Displays the Ethernet adapter's IPv4 address, subnet mask, gateway and DNS details |
| `Get-NetAdapter`       | Ethernet adapter status is `Up` when the physical link is established              |
| `ping 192.168.1.1`     | Replies from the default gateway, if ICMP is permitted                             |
| `ping 192.168.1.101`   | Replies from a second device using that example IP, if it exists and permits ping  |
| `nslookup example.com` | Displays a DNS server and resolved IP address(es)                                  |
| `tracert example.com`  | Displays the route toward the destination; some hops may time out                  |
| `arp -a`               | Displays cached IP-to-MAC address mappings for the local network                   |

Replace example IP addresses with the actual values in your environment before executing commands.

## Connectivity Test Examples

### Test 1: Verify IP Configuration

Command:

`ipconfig /all`

Expected result:

* Ethernet adapter is present.
* IPv4 address belongs to the configured LAN subnet.
* Subnet mask matches the LAN configuration.
* Default gateway points to the home router.
* DHCP is enabled when automatic addressing is used.

### Test 2: Verify Gateway Connectivity

Command:

`ping 192.168.1.1`

Example successful output:

`Reply from 192.168.1.1: bytes=32 time=2ms TTL=64`

Expected result: Successful replies with no packet loss during the test.

The response time and TTL are examples only. They can vary by device and network. A failed ping does not necessarily mean the gateway is unavailable, because ICMP traffic may be blocked.

### Test 3: Verify DNS Resolution

Command:

`nslookup example.com`

Expected result:

* A DNS server is identified.
* The domain resolves to one or more IP addresses.
* No DNS timeout or resolution failure occurs.

The returned IP addresses may change.

### Test 4: Verify Network Adapter Status

Command:

`Get-NetAdapter`

Expected result: The Ethernet adapter shows `Up` when connected to an active switch port with a working cable and enabled adapter.

