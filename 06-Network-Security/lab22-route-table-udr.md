# Lab 22 - Route Tables and User-Defined Routes

## Objective

Create an Azure route table and use a User-Defined Route to control traffic from the application subnet.

## Configuration

Route table:

- Name: `rt-app`
- Associated subnet: `snet-app`
- Subnet address range: `10.10.2.0/24`

User-Defined Route:

- Name: `Drop-Test-Network`
- Destination: `192.0.2.0/24`
- Next hop: `None`

The documentation range `192.0.2.0/24` was used so the lab would not interfere with real destinations.

## What I Learned

- Route tables control where Azure sends traffic.
- UDRs can override Azure system routing behavior.
- `Next hop: None` creates a black-hole route that drops matching traffic.
- A route table must be associated with a subnet before its routes affect workload traffic.
- Azure chooses the most specific matching route.

## Memory Aid

- NSG = permission
- Route = direction
- Most specific route wins
- None = drop
- Virtual appliance = send traffic to a firewall or NVA

## Screenshots

![Route table and subnet association](screenshots/route-table-udr.png)

## Interview Takeaway

Route tables are commonly used to steer traffic through centralized security devices such as Azure Firewall or another network virtual appliance.

For example, a default route can direct outbound traffic to a firewall for centralized inspection.

## Exam Notes

- UDR = User-Defined Route
- Route tables are associated with subnets
- Most specific route wins
- `None` means drop traffic
- `Virtual appliance` is commonly used for firewall routing
- NSGs control permission; route tables control direction
