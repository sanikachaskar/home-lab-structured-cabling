# Network Topology

## Architecture

The home lab uses a star topology. End devices connect to a central Ethernet switch, which connects to a LAN port on the existing home router.

## Physical Connections

| Link ID | Source                          | Destination              | Cable            | Verification       |
| ------- | ------------------------------- | ------------------------ | ---------------- | ------------------ |
| C01     | Router LAN port                 | Switch port 1            | Cat6 patch cable | Link LEDs          |
| C02     | Switch port 2                   | Laptop Ethernet port     | Cat6 patch cable | Adapter status     |
| C03     | Switch port 3                   | Second device (optional) | Cat6 patch cable | Link LEDs          |
| C04     | Additional device or test cable | Available port           | As applicable    | Record actual test |

## Network Information

* Topology: Star
* Switch type: Unmanaged Gigabit Ethernet
* IP addressing: DHCP from the existing router, unless configured otherwise
* Network range: Record the actual assigned subnet
* Default gateway: Record the actual router address

