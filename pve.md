### windows installation

To get started, we need:

- [virtio-win](https://fedorapeople.org/groups/virt/virtio-win/direct-downloads/stable-virtio/virtio-win.iso) ISO
- [win11](https://www.microsoft.com/ru-ru/software-download/windows11) ISO

Next create VM, We need this:

- OS — use w11 image
- System — use SCSI controller — **VirtIO SCSI**  | Bios **OVMF (UEFI)** and add **TPM**
- Disk — **VirtIO Block** and minimal disk size 64 Gb

Add CD/DVD Drive to Hardware, use IDE **virtio-win** Image. Now we can start VM and press Enter to Console VM.
 As usual, go through all the steps to the disk selection window.
 Next step: “**Load Drive**” We are looking for CD **virtio-win**. Open folder **viostore** > w11 > amd64.
 We continue with the usual installation.

But, I faced the following problem.
 In the network device selection window, but a network was detected and could not be skipped this step.
 My network device received IPv6 settings for DHCP.
 Open **Shift+F10** console. Open **taskmgr** to stop network connection flow service. 
 We can open Special features and change network setting on Windows. I  set my current IPv4 parameter, and again stop network connection flow  service.

 Hooray, everything should go smoothly from here on out) But this is win11 **![:D](data:image/gif;base64,R0lGODlhAQABAIAAAAAAAP///yH5BAEAAAAALAAAAAABAAEAAAIBRAA7)**



I was not able to boot after following these fantastic instructions. I had to go to Options to change the Boot Order.
Original: Options > Boot Order > ide2, net0
Modified: Options > Boot Order > virtio0, ide2, net0