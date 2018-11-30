# Lab Sensit

## Prerequesite

### Sigfox Cloud

1.  Head over to the [activate](https://buy.sigfox.com/activate).

2. Select your country, enter the device ID & PAC and finish creating your account.

3. Once done, log on the [backend](https://backend.sigfox.com/).

4. Try sending a message by double pressing the button.

5. Click on your device ID and select the **"Messages"** tab. You should now see a Sigfox message.

### Sens'it development environment

1. Download and install [GNU Arm Embedded Toolchain version 7.2.1](https://developer.arm.com/open-source/gnu-toolchain/gnu-rm/downloads).

2. Download and install [dfu-util 0.9](http://dfu-util.sourceforge.net/).

3. Edit `./sensit-sdk-v2.0.0/sdk/Makefile`:

    * Make sure your `CC`, `BIN_TOOL`, `SIZE_TOOL` paths links to the right folder.
    * Example:
        ```
        CC = /Users/antoine/Documents/gcc-arm-none-eabi-7-2018-q2-update/bin/arm-none-eabi-gcc
        BIN_TOOL  = /Users/antoine/Documents/gcc-arm-none-eabi-7-2018-q2-update/bin/arm-none-eabi-objcopy
        SIZE_TOOL = /Users/antoine/Documents/gcc-arm-none-eabi-7-2018-q2-update/bin/arm-none-eabi-size
        ```
4. **Copy** and **paste** the content of `main_TEMPERATURE.c` in `main.c`.

## Program your Sens'it

To program your Sens'it you will need to put it in bootloader:
1. Connect your device to your computer.
2. Reset your device. With one of the provided firmwares you can do this with 4 short presses on the button.
3. When the secondary LED starts blinking, do a long press on the button.
4. If both LEDs become white, your device is in bootloader.

Then, use the `make prog` command to program your Sens'it.

### Hint

If you want to return to the original firmware of the Sens'it 3, use the following command to program it:
```
dfu-util -a 0 -s 0x08000000:leave -D bin/sensit_discovery_vX.X.X.bin
```
Replace `X.X.X` with the current version of the Discovery firmware available in the `bin` folder.
-

# PART 2 - Implementing a use case

## Use case

1. Think of a use case with your group.
    - Fill in the blanks [here](https://goo.gl/remJnJ).
    - Describe briefly your use-case idea _(try to keep it business focused if you can)_.

## Implementation

1. Make sure your Sens’it is activated and messages are received on the Sigfox Backend.

2. Use the Sens’it SDK docs.
    - Open index.html in the `./sensit-sdk-v2.0.0/doc/html/` folder.
    
### Program your Sens'it

Implement a new firmware in the `main.c` file (located in `./sensit-sdk-v2.0.0/sdk/src/`).

- To compile use `make all`. This command will also let you verify your code.
- To flash your Sens'it you will need to put it in bootloader:
    1. Connect your device to your computer.
    2. Reset your device. With one of the provided firmwares you can do this with 4 short presses on the button.
    3. When the secondary LED starts blinking, do a long press on the button.
    4. If both LEDs become white, your device is in bootloader.
    5. Then, use the `make prog` command to program your Sens'it.

## Visualize and decode your messages

1. Head over to https://workshop.iotagency.sigfox.com.
2. Create a parser _(use your name as parser name)_ to decode your payloads.
3. Build a dashboard.

## Pitch

1. Download & fill the pitch slides [here](https://goo.gl/E6et8W)
2. Pitch your use case! **(2-3min talk max)**

---
---

# Hint

If you want to return to the **original firmware** of the Sens'it 3, use the following command to program it:
```
dfu-util -a 0 -s 0x08000000:leave -D bin/sensit_discovery_vX.X.X.bin
```
Replace `X.X.X` with the current version of the Discovery firmware available in the `bin` folder.
