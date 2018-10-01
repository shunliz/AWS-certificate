

**Q. Do X1 and X1e instances enable CPU power management state control**

Yes. You can configure C-states and P-states on x1e.32xlarge, x1e.16xlarge, x1e.8xlarge, x1.32xlarge and x1.16xlarge instances. You can use C-states to enable higher turbo frequencies \(as much as 3.1 GHz with one or two core turbo\). You can also use P-states to lower performance variability by pinning all cores at P1 or higher P states, which is similar to disabling Turbo, and running consistently at the base CPU clock speed.

**Q: Is data stored on Amazon EC2 NVMe instance storage encrypted?**

Yes, all data is encrypted in an AWS Nitro hardware module prior to being written on the locally attached SSDs offered via NVMe instance storage.

**Q: What encryption algorithm is used to encrypt Amazon EC2 NVMe instance storage?  **

Amazon EC2 NVMe instance storage is encrypted using an XTS-AES-256 block cipher.

**Q. What is VM Import/Export?**

VM Import/Export enables customers to import Virtual Machine \(VM\) images in order to create Amazon EC2 instances. Customers can also export previously imported EC2 instances to create VMs. Customers can use VM Import/Export to leverage their previous investments in building VMs by migrating their VMs to Amazon EC2.



**Q. What virtual machine file formats are supported?**

You can import VMware ESX VMDK images, Citrix Xen VHD images, Microsoft Hyper-V VHD images and RAW images as Amazon EC2 instances. You can export EC2 instances to VMware ESX VMDK, VMware ESX OVA, Microsoft Hyper-V VHD or Citrix Xen VHD images. For a full list of support operating systems, please see[What operating systems are supported?](https://amazonaws-china.com/ec2/faqs/#What_operating_systems_are_supported).

