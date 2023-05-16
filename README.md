# 1.28-Round-LCD-Breakout
<img src="https://cdn.shopify.com/s/files/1/1217/2104/files/1.28_RoundLCDBreakout.png?v=1677234040">

Pico 1.28” Round LCD HAT is a 1.28-inch display HAT with 240 x 240 resolution, 65K RGB colors, clear and colorful displaying effect, and a joystick, designed for the Raspberry Pi Pico to expand its engagement via SPI communication by providing a standard 40 pin Pico GPIO interface. The Pico 1.28" Round LCD HAT includes an integrated GC9A01 display driver and SPI interface, reducing the number of IO pins required. It features a 5-input joystick that is connected to the Pico 1.28” Round LCD HAT through a stackable GPIO connector header on the inside.

### Features
* Raspberry Pi Pico compatibility.
* 4-wire SPI Communication.
* Standard Raspberry Pi Pico 40 Pins GPIO.
* 4 directions + attached band Central press button Joystick Control

## Installation
### MicroPython
Before starting, Make sure you have the v1.15 version of Micropython installed on your Pico board.
* For running this HAT, you require these components :
  * Raspberry Pi Pico X 1
  * Pico 1.28" Round LCD HAT X 1
  * USB Cable X 1
* Copy or clone code from Github.
  https://github.com/sbcshop/PICO-1.28-Round-LCD-HAT/
* Stack Pico 1.28 Round LCD HAT with Raspberry Pi Pico, Make sure USB symbol on LCD HAT should be on the same side as of PICO USB.
* Press and hold BOOTSEL pin of Raspberry Pi Pico and connect the USB cable, it will create a drive as RPI-RP2.
* Now drag and drog/copy firmware.uf2 file from firmware folder to RPI-RP2 Drive. It will reboot your raspberry pi pico.
* Open Thonny IDE and Choose interpreter as MicroPython (Raspberry Pi pico).

  <img src = "https://github.com/sbcshop/1.28-Round-LCD-Breakout-Software/blob/main/images/Thonny-interpreter.png" >
  
* Now you can run example codes from the Pico_Example_mpy folder in Thonny Ide. For example, Open the hello.py file in thonny and click on the green play button to run this example.

  <img src = "https://github.com/sbcshop/1.28-Round-LCD-Breakout-Software/blob/main/images/Pico_Round_lcd_HAT_thonny.png" >
  
It will print "Hello" on Round LCD. You can use the joystick to change the LCD color.

### Working Example
  * This module was tested on Raspberry Pi Pico. You need to provide a SPI object and the pin to use for the DC pin of the screen.
  ```
  import machine
  import gc9a01
  spi = SPI(1, baudrate=40000000, sck=Pin(10), mosi=Pin(11))
  tft = gc9a01.GC9A01(spi, 240, 240, reset=Pin(12, Pin.OUT), cs=Pin(9, Pin.OUT), dc=Pin(8, Pin.OUT), backlight=Pin(13, Pin.OUT), rotation=0)
  tft.init()
 ```
### Functions and Arguments
 * gc9a01.GC9A01(spi, width, height, reset, dc, cs, backlight, rotation, buffer_size)
required arguments:
```
 `spi` spi device
    `width` display width
    `height` display height
 ```
 optional args:
 ```
   `reset` reset pin
    `dc` dc pin
    `cs` cs pin
    `backlight` backlight pin
    `rotation` Orientation of display.
    `buffer_size` 0= buffer dynamically allocated and freed as needed.

    Rotation | Orientation
    -------- | --------------------
       0     | 0 degrees
       1     | 90 degrees
       2     | 180 degrees
       3     | 270 degrees
       4     | 0 degrees mirrored
       5     | 90 degrees mirrored
       6     | 180 degrees mirrored
       7     | 270 degrees mirrored
   ```

If buffer_size is specified it must be large enough to contain the largest bitmap, font character, and/or JPG used (Rows * Columns * 2 bytes). Specifying a buffer_size reserves memory for use by the driver otherwise, memory required is allocated and free dynamically as it is needed. Dynamic allocation can cause heap fragmentation so garbage collection (GC) should be enabled.

**This driver supports only 16bit colors in RGB565 notation.**
  * GC9A01.on()

Turn on the backlight pin if one was defined during init.
  * GC9A01.off()

Turn off the backlight pin if one was defined during init.
  * GC9A01.pixel(x, y, color)

Set the specified pixel to the given color.
  * GC9A01.line(x0, y0, x1, y1, color)

Draws a single line with the provided color from (x0, y0) to (x1, y1).
  * GC9A01.hline(x, y, length, color)

Draws a single horizontal line with the provided color and length in pixels. Along with vline, this is a fast version with reduced number of SPI calls.
  * GC9A01.vline(x, y, length, color)

Draws a single horizontal line with the provided color and length in pixels.
  * GC9A01.rect(x, y, width, height, color)

Draws a rectangle from (x, y) with corresponding dimensions
  * GC9A01.fill_rect(x, y, width, height, color)

Fill a rectangle starting from (x, y) coordinates

## Resources
  * [1.28-Round-LCD-Breakout Schematic](https://github.com/sbcshop/1.28-Round-LCD-Breakout-Hardware/blob/main/Design%20Data/SCH%201.28inch%20ROUND%20LCD%20BREAKOUT.pdf)
  * [1.28-Round-LCD-Breakout Hardware](https://github.com/sbcshop/1.28-Round-LCD-Breakout-Hardware)
  * [1.28-Round-LCD-Breakout Step File](https://github.com/sbcshop/1.28-Round-LCD-Breakout-Hardware/blob/main/Mechanical%20Data/STEP%20ROUND%20DISPLAY%20BREAKOUT.step)
  * [GC9A01 Datasheet](https://github.com/sbcshop/1.28-Round-LCD-Breakout-Software/blob/main/Documents/GC9A01A%20Datasheet.pdf)


## Related Products

   * [1.54" LCD Breakout](https://shop.sb-components.co.uk/products/1-54-lcd-breakout?_pos=3&_sid=fd594d9e8&_ss=r) - The 1.54 TFT LCD breakout is colorful and easy to experiment with graphics. The display is of 240x240 resolution and 65k RGB colors to create a colorful user interface for your project. 
   
     ![1.54" LCD Breakout](https://cdn.shopify.com/s/files/1/1217/2104/products/01.2.png?v=1677136550&width=300)
   
   * [1.3" LCD Breakout](https://shop.sb-components.co.uk/products/1-3-lcd-breakout?_pos=4&_sid=4a275fa92&_ss=r) - 
   
     ![1.3" LCD Breakout](https://cdn.shopify.com/s/files/1/1217/2104/products/01_1_a486ba53-c02b-4491-b110-a9b64736ad39.png?v=1677241189&width=300)
     
   * [1.14" LCD Breakout](https://shop.sb-components.co.uk/products/1-14-inch-lcd-breakout?_pos=4&_sid=fd594d9e8&_ss=r) - 
   
     ![1.3" LCD Breakout](https://cdn.shopify.com/s/files/1/1217/2104/products/1.14InchLCDBreakout.png?v=1622801461&width=300)

 
## Product License

This is ***open source*** product. Kindly check LICENSE.md file for more information.

Please contact support@sb-components.co.uk for technical support.
<p align="center">
  <img width="360" height="100" src="https://cdn.shopify.com/s/files/1/1217/2104/files/Logo_sb_component_3.png?v=1666086771&width=300">
</p>
