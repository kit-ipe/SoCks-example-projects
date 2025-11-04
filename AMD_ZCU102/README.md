# SoCks Example Project for the AMD ZCU102 Evaluation Kit

## Create the Example Image

1. Install SoCks. Further instructions can be found in the [SoCks GitHub repository](https://github.com/kit-ipe/SoCks).

2. Move to this directory.
    ```
    $ cd SoCks-example-projects/AMD_ZCU102
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
    $ sudo dd if=zcu102-example-project_sd_card.img of=/dev/sdX bs=1M status=progress
    ```

## Using the Example Image

1. Insert the SD card into your ZCU102 evaluation kit and connect the USB UART of the ZCU102 to your PC.

2. Open the UART on your PC
    ```
    $ screen /dev/ttyUSB0 115200
    ```

3. Start the ZCU102 and observer the boot process. The login credentials are defined in the *rootfs* section in [project.yml](project.yml).

That's it! In a next step, you can modify the example project so see what SoCks can do four you.
