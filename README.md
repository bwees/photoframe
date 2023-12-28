# Photoframe
A photo frame using a 7-color e-paper display that presents a new picture daily. Fully battery-powered and wireless.

Based on the project by [CNLohr](https://www.youtube.com/watch?v=YawP9RjPcJA) 

## Hardware

### Materials:
- [ESP32-S3-XIAO Microcontroller](https://www.amazon.com/dp/B0BYSB66S5)
- [2200mah 1s Battery](https://www.amazon.com/dp/B08214DJLJ)
- [Waveshare 5.65" 7-Color E-Paper Display](https://www.amazon.com/dp/B08J7GGRYF)
- Frame or Enclosure to house display and electronics
  - I had mine custom framed but your local craft store will likely have a cheap framing and matting service.

Connect the E-Paper Display to the XIAO using the following wiring:
```
BUSY -> D2, 
RST -> D3,
DC -> D4, 
CS -> D5
CLK -> D6
DIN -> D10
GND -> GND
VCC -> 3.3V
```

Connect the battery to the BAT+ and BAT- pads on the back of the XIAO

## Software

Using Docker Compose:
```
frame:
    image: ghcr.io/bwees/photoframe:latest
    volumes:
      - /path/to/save/images:/app/static/images
      - /etc/timezone:/etc/timezone:ro
      - /etc/localtime:/etc/localtime:ro
    ports:
      - 8000:8000
```
**Note: you will need to change the port and web URL in the firmware code to match your server.**
