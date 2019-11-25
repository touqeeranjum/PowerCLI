# PowerCLI
Automation With PowerCLI for VMware Virtual Datacenter

This project automates virtual datacenter deployment for vCenter using Standard Virtual Switches

# Configurations

* Virtual Machines
  * 1 Windows Server 2016 VM
    * 3 disks (1 for NFS, 2 for iSCSI)
  * 1 vCenter Server Appliance version 6.7.0.41000-14836122 VM
  * 5 ESXi Hosts version 6.7.0.update03-14320388 VM with 6GB RAM each
    * 2 disks, 1 for Cache (15GB), 1 for Capacity (256GB), per ESXi host

* If the ESXi hosts are cloned in Workstation the following command must be run in each ESXi shell via SSH. This will generate a new UUID for each ESXi host, if this is not done vSAN disk creation will fail

  *sed -i 's#/system/uuid.*##' /etc/vmware/esx.conf

# vLABVMwareNetworks File
This is the configured networks file to be imported in Workstation 15.5.1 build-15018445

* 6 Networks: Management, NFS, iSCSI, vSAN, vMotion, FaultTolerance
* Windows Server has 3 NIC for Management, NFS, and iSCSI
* vCenter NIC is on Management network
* All ESXi Hosts have:
  * 1 NIC for Management
  * 1 NIC for NFS
* Any 2 ESXi hosts have 1 NIC for iSCSI each
* Remaining 3 ESXI hosts each have 1 NIC for vSAN, 1 NIC for vMotion, and 1 NIC for FaultTolerance

# Storage
* All 5 ESXi hosts have access to NFS storage disk on Windows Server
* 2 of 5 ESXi hosts have access to iSCSI storage
* 3 of 5 ESXi hosts have access to vSAN storage
  
# POWERSHELL
* Server configuration script with DNS configuration for vCenter, and ESXi hosts: https://github.com/touqeeranjum/PowerShell/blob/master/AD%20Server%20Configuration%20With%20DNS%20for%20vCenter%2C%20and%20ESXi
* NFS and iSCSI services are installed
* Disks are configured as NFS, and iSCSI storage

# esxiHostsDeployments.csv File
This is the configuration deployment file to be placed in Windows Server 2016 desktop

# POWERCLI
* Using a CSV file:
  * ESXi hosts are deployed into their relevant cluster in vCenter
  * Standard Virtual Switches are created and added to each ESXi host
  * Each ESXi host is configured with VMNICs
  * Appropriate VMNICs are attached to Virtual Switches
  * VMKernels are created and attached to VMNICs
  * PortGroups are created with IP addresses assigned

* NFS storage is configured and attached to all ESXi hosts
* iSCSI storage is configured and attached to 2 ESXi hosts
* vSAN storage is configured and disk groups added to 3 ESXi hosts each
