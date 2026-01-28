# 🌐 IP Command Helper - Interactive Network Configuration Tool
A comprehensive all in one tool to manage network interfaces and links using baked in kernel "ip" command

🚀 Never Forget Complex ip Commands Again!

Tired of digging through man pages to remember the exact syntax for ip commands? This interactive menu-driven tool makes network configuration on Linux systems intuitive, safe, and persistent. Perfect for sysadmins, developers, and networking students!

---

✨ Key Benefits & Features

· 🛡️ Safe & Interactive: Every command is previewed before execution with a confirmation prompt. No more accidental network disruptions!
· 💾 Configuration Persistence: Save your interface settings (IPs, VLANs, MTU) automatically to disk (/etc/network/interfaces.d/) so they survive reboots.
· 📝 Comprehensive Logging: All actions are timestamped and logged to /tmp/ip-command-helper.log for easy auditing and troubleshooting.
· 🎯 Intuitive Menu System: Forget complex syntax. Manage links, addresses, routes, and neighbors through simple numbered menus.
· ⚡ Smart Privilege Handling: The script automatically detects if you're root and uses sudo only when necessary.
· 🔧 Advanced Operations Made Simple: Easily create VLANs, bridges, bonded interfaces, modify MAC addresses, and more—all through guided prompts.

---

📦 What Can It Do? (Module Breakdown)

The tool is organized into logical modules, each handling a specific aspect of network configuration.

🔗 Link Module (Layer 2 Operations)

· Bring interfaces UP or DOWN
· Set MTU (with value validation)
· Change MAC address
· Toggle promiscuous mode
· Create VLAN subinterfaces
· Create bridge and bond interfaces
· Add interfaces to bridges

🌐 Address Module (Layer 3 - IP Management)

· Add or delete IP addresses with CIDR notation
· Flush all IP addresses from an interface
· View all assigned IPs

🛣️ Route Module (Routing Table Management)

· Add and delete static routes
· Flush routing tables
· Display the current routing table

👥 Neighbor Module (ARP/NDP Cache)

· Manage ARP/neighbor cache entries
· Add and delete static neighbor entries
· Flush neighbor cache

---

🚀 Quick Start Guide

Prerequisites

· A Linux system with iproute2 installed (usually pre-installed)
· Bash shell
· sudo privileges for some operations

Installation & Running

1. Download the script:
   ```bash
   wget https://raw.githubusercontent.com/GIGA-YZ/IP-helper/main/IP-helper.sh
   ```
2. Make it executable:
   ```bash
   chmod +x IP-helper.sh
   ```
3. Run it:
   ```bash
   ./IP-helper.sh
   # Or with sudo if you want to avoid permission prompts:
   sudo ./IP-helper.sh
   ```

---

🎮 How to Use: A Typical Workflow

The tool guides you step-by-step:

1. Launch the script and select a network interface from the list
2. Choose an operation module (Link, Address, Route, or Neighbor)
3. Select the specific operation (e.g., "Add IP address")
4. Enter required parameters when prompted (the script validates your input)
5. Review the generated ip command before it runs
6. Choose whether to save the configuration persistently
7. Return to the menu to perform more operations

Example: Adding a VLAN

```
1. Select interface: eth0
2. Choose module: Link → Create VLAN subinterface
3. Enter VLAN ID: 100
4. Enter VLAN name: eth0.100
5. Review command: ip link add link eth0 name eth0.100 type vlan id 100
6. Confirm execution (y/N): y
7. Save persistently? (y/N): y
✅ Done! VLAN created and saved.
```

---

🔧 Advanced Features Explained

📂 Configuration Persistence

The script stores your configurations in /etc/network/interfaces.d/ip-helper-persistent and creates automatic backups in /etc/network/interfaces.d/backups/. You can apply all saved configurations at once from the main menu.

🔄 Interface Selection

It intelligently parses ip -brief link show output, handling complex interface names (including parent/child relationships like virbr1.1@virbr1).

✅ Input Validation

The script validates:

· MTU values (68-9000 range)
· MAC address format
· VLAN IDs (1-4094)
· IP/CIDR notation
· Bond mode names

---

⚠️ Troubleshooting & Tips

· "Operation not permitted" errors: Run the script with sudo or ensure your user has appropriate capabilities
· Changes don't persist after reboot: Make sure to select "Save this change persistently?" when prompted
· Interface not showing up: The script only shows interfaces visible to ip link. Check if the interface exists and isn't hidden
· Log location: Check /tmp/ip-command-helper.log for detailed execution history
· Restoring backups: Manual backups are in /etc/network/interfaces.d/backups/ with timestamped filenames

---

👥 Who Is This Tool For?

· 🧑‍💻 System Administrators: Quick, reproducible network configuration
· 🎓 Networking Students: Learn ip command syntax through interactive examples
· 🔬 DevOps Engineers: Script and automate network setups
· 🏠 Homelab Enthusiasts: Experiment with VLANs, bridges, and bonds safely
· 🐧 Any Linux User who occasionally needs to configure networks but doesn't use ip commands daily

---

📄 License & Contribution

This is an open-source tool. Feel free to:

· ✨ Suggest features by opening GitHub issues
· 🔧 Submit pull requests with improvements
· 🐛 Report bugs when things don't work as expected

Pro Tip: The script's modular design makes it easy to extend. Want to add a new module? Just follow the existing pattern in the code!

---

Next time you need to configure a network interface, don't google—use the IP Command Helper! 🚀
