# VMware安装macOS Monterey 12.6

Search for board-id.reflectHost and set the value to "FALSE"
board-id.reflectHost = "FALSE"

Search for ethernet0.virtualDev and set the value to "vmxnet3"
ethernet0.virtualDev = "vmxnet3"

Then paste the following options at the bottom of the file
board-id = "Mac-AA95B1DDAB278B95"
hw.model.reflectHost = "FALSE"
hw.model = "MacBookPro19,1"
serialNumber.reflectHost = "FALSE"
serialNumber = "C01234567890"

注意: If running an AMD processor, add the following additional options to the bottom of the file

smc.version = "0"
cpuid.0.eax = "0000:0000:0000:0000:0000:0000:0000:1011"
cpuid.0.ebx = "0111:0101:0110:1110:0110:0101:0100:0111"
cpuid.0.ecx = "0110:1100:0110:0101:0111:0100:0110:1110"
cpuid.0.edx = "0100:1001:0110:0101:0110:1110:0110:1001"
cpuid.1.eax = "0000:0000:0000:0001:0000:0110:0111:0001"
cpuid.1.ebx = "0000:0010:0000:0001:0000:1000:0000:0000"
cpuid.1.ecx = "1000:0010:1001:1000:0010:0010:0000:0011"
cpuid.1.edx = "0000:0111:1000:1011:1111:1011:1111:1111"
smbios.reflectHost = "TRUE"