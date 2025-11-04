# SoCks Example Project for the Raspberry Pi 4

## Create the Example Image

1. Install SoCks. Further instructions can be found in the [SoCks GitHub repository](https://github.com/kit-ipe/SoCks).

2. Move to this directory.
    ```
    $ cd SoCks-example-projects/Raspberry_Pi_4
    ```

3. Print the complete project configuration to see what SoCks will build.
    ```
    $ socks --show-configuration
    ```

4. Build the project.
    ```
    $ socks all build
    ```

5. Create SD card image.
    ```
    $ socks image build-sd-card
    ```

## Write the Image to a SD card

1. Navigate to the output directory of the *image* block.
    ```
    $ cd temp/image/output
    ```

2. Write the image to an SD card. Identify the device you want to write to e.g. with `lsblk` and unmount it.

    **WARNING:** Before writing to a device, first identify it, e.g. with `lsblk`, and unmount it.
    ```
    $ sudo dd if=rpi4-example-project_sd_card.img of=/dev/sdX bs=1M status=progress
    ```

3. The bootloader of the Raspberry Pi is picky when it comes to the boot partition. It does not accept the format created by SoCks (or mkfs). Currently, I only know of the following workaround to fix this problem: Copy all files from the bootfs partition to your PC, format the bootfs partition to FAT16 or FAT32 using gparted, and then copy the files back to the boot partition.

## Using the Example Image

1. Insert the SD card into your Raspberry Pi 4 and connect a display via micro HDMI.

2. Connect the Raspberry Pi to power and observer the boot process. The login credentials are defined in the *rootfs* section in [project.yml](project.yml).

That's it! In a next step, you can modify the example project so see what SoCks can do four you.
