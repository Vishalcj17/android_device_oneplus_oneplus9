## Guide to lock bootloader with AOSPA.

 > Build dist with release keys first 
         './rom-build.sh -z -s /home/user/signing-keys/ -t user -v release oneplus9pro'
   Should be in this order of script.

 > Build a AVB signature bin for hash support.
          'cd external/avb; extract_public_key --key /home/user/signing-keys/releasekey.key --output /home/user/pkmd-signed.bin'

 > Download the build.

 > Flash it and do a small sanity check.

 > Reboot to bootloader, and flash pkmd image.
           'fastboot flash avb_custom_key /home/user/pkmd-signed.bin; fastboot reboot bootloader'
   Then do
           'fastboot oem lock'
   and let the device boot.
