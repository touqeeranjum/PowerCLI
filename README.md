# PowerCLI
Automation With PowerCLI for VMware Virtual Datacenter

# This project automates virtual datacenter deployment.

# First NFS and iSCSI services are confgured with Powershell, then the disks are configured as NFS, and iSCSI storage disks on a Windows Server via Powershell.

# Then via PowerCLI ESXi hosts are deployed from a CSV file into vCenter, and assigned with appropriate VMNICs and their VMKernels are configured, and PortGroups are configured and IP addresses added. Then configures NFS, iSCSI, and vSAN storage to the deployed ESXi hosts.
