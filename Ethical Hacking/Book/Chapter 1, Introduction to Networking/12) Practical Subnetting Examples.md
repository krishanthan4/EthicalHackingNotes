In the previous chapter, we learned about the concept of subnetting and why it's important. Now, let's put that knowledge to practical use by exploring some real-world subnetting examples.

## Scenario 1: Home Network

**Situation:** You have a home network with the IP address range 192.168.1.1 to 192.168.1.255, and you want to create separate subnets for your family's devices and your smart home devices.

**Solution:**

- **Subnet 1 (Family Devices):**
    
    - IP Range: 192.168.1.1 to 192.168.1.126
    - Subnet Mask: 255.255.255.128 (/25 prefix length)
    - This subnet can accommodate up to 126 devices, perfect for your family's smartphones, laptops, and tablets.
- **Subnet 2 (Smart Home Devices):**
    
    - IP Range: 192.168.1.129 to 192.168.1.254
    - Subnet Mask: 255.255.255.128 (/25 prefix length)
    - This subnet can also accommodate up to 126 devices, suitable for your smart lights, thermostats, and appliances.

## Scenario 2: Office Network

**Situation:** You work in a small office with multiple departments, and you want to create separate subnets for each department to enhance security and network efficiency.

**Solution:**

- **Subnet 1 (Sales Department):**
    
    - IP Range: 192.168.1.1 to 192.168.1.63
    - Subnet Mask: 255.255.255.192 (/26 prefix length)
    - This subnet allows for up to 62 devices, suitable for the sales team's computers and phones.
- **Subnet 2 (Marketing Department):**
    
    - IP Range: 192.168.1.65 to 192.168.1.127
    - Subnet Mask: 255.255.255.192 (/26 prefix length)
    - This subnet also allows for up to 62 devices, suitable for the marketing team's devices.
- **Subnet 3 (IT Department):**
    
    - IP Range: 192.168.1.129 to 192.168.1.191
    - Subnet Mask: 255.255.255.192 (/26 prefix length)
    - This subnet provides room for up to 62 devices, suitable for the IT department's servers and devices.

By subnetting the office network, you enhance security by isolating departments and reduce network congestion by segmenting devices logically.

## Scenario 3: Data Center

**Situation:** You manage a data center with thousands of servers, and you want to efficiently organize IP addresses for various services, such as web hosting, database servers, and virtual machines.

**Solution:**

- **Web Hosting Servers:**
    
    - IP Range: 10.0.0.1 to 10.0.0.255
    - Subnet Mask: 255.255.255.0 (/24 prefix length)
    - This subnet can accommodate up to 254 web hosting servers.
- **Database Servers:**
    
    - IP Range: 10.0.1.1 to 10.0.1.255
    - Subnet Mask: 255.255.255.0 (/24 prefix length)
    - This subnet can accommodate up to 254 database servers.
- **Virtual Machines:**
    
    - IP Range: 10.0.2.1 to 10.0.2.255
    - Subnet Mask: 255.255.255.0 (/24 prefix length)
    - This subnet can accommodate up to 254 virtual machines.

By subnetting the data center, you ensure that each service has its own dedicated IP address range, making it easier to manage and scale your infrastructure.

## Wrapping It Up

These practical examples demonstrate how subnetting allows network administrators to efficiently manage IP address assignments, improve security, and optimize network performance in various scenarios, from home networks to data centers.

In the next chapter, we'll explore advanced subnetting techniques and provide tips for subnetting success.