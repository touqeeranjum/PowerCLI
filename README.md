# PowerCLI
Automation With PowerCLI for VMware Virtual Datacenter

# This project automates virtual datacenter deployment.

# First NFS and iSCSI services are confgured with Powershell, then the disks are configured as NFS, and iSCSI storage disks on a Windows Server via Powershell.

# Then via PowerCLI ESXi hosts are deployed and their relevant cluster in vCenter, and each hosts relevant network information is also configured, all from a CSV file. This is followed by relevant standard Virtual Switch creation which are added to each ESXi host followed by appropriate VMNICs assigned and VMKernels configured, and PortGroups created with IP addresses assigned. NFS storage is configured to be accessible by all the hosts, while iSCSI storage is configured to be accessible by only 2 ESXi hosts, and finally vSAN storage is configured which is accessible only by 3 hosts.
