## Persistence Trouble and Considerations

If you are having trouble trying to run persistence live version on your you flash drive, there are some common problems that can happen. This can depend on the following:

- You current machine.
- Usb port function.
- Size of usb drive.


A couple of solutions you can do if you are trying to run persistence-live:

- <b>Switch the usb to new ports or find your best usb port</b>. I encountered this a couple of times from both Linux 18.04.3 and 19.10. 
- <b>Use a smaller usb</b>. I recommended this in the tutorial. In all my tests, when I tried to run a flash drive that was 256GB with an estimated 400MB/s read and write speed, my devices could not keep up. However on a generic 64 GB drive, loading times were not an issue.
- <b>Disabling the floppy drive on startup</b>. In your BIOS, you may have the option to disable the floppy drive, even if your device doesn't include a floppy drive (which I guarantee). This is caused by how the `casper-rw` is looking for you image and gets stuck in the loop and keeps searching through that particular section. The error usually appears as the following:

<div id='center'>
/init: line 7: can't open /dev/sr0: No medium found
</div>

Rather than moving to a different partition to find the image, it just keeps searching through there endlessly.

If trying to boot into persistence live is still an issue, you can always run `live` and save anything you need to the `usbdata` partition. You won't be able to save any operation changes, but any packages and files downloaded to `usbdata` will be recoverable

## Considerations

Since persistence live is not a full installation, there are a couple things to keep in mind regarding using persistence:

- If you screen dims, even with a secure user, anybody can still have access to your account by pulling it back up. 
- Updates that you make to the distro will either start clogging the usb and possibly break or become corrupted after a long period of time. 

Using a persistence live version of ubuntu is great for testing out the OS and being able to save applications without fully committing. However, if you are going to use an Linux distro for an extended period of time, you will want to install a full version.