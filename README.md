# PowerCLI
Automation With PowerCLI for VMware Virtual Datacenter

# This project automates virtual datacenter deployment for VMware vCenter.

# POWERSHELL
* First NFS and iSCSI services are confgured with Powershell
* Then the disks are configured as NFS, and iSCSI storage on a Windows Server

# POWERCLI
* Using a CSV file :
  * ESXi hosts are deployed into their relevant cluster in vCenter
  * Standard Virtual Switches are created and added to each ESXi host
  * Each ESXi host is configured with VMNICs
  * VMKernels are created
  * PortGroups are created with IP addresses assigned

* NFS storage is configured and attached to all ESXi hosts
* iSCSI storage is configured and attached to 2 ESXi hosts
* vSAN storage is configured and disk groups added to 3 ESXi hosts each
