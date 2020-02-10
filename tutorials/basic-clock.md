# Halo HD Basic Clock

## Introduction @unplugged
Learn how to use the Halo HD with its features to make a fully functioning clock
INSERT GIF OF THE HALO HD


![Heart shape in the LEDs](/static/mb/projects/flashing-heart/sim.gif)

## Step 1 @fullscreen
First, let's make sure the Halo HD is working correctly with a simple piece of code.
Place the ``||kitronik_halo_hd.createZIPHaloDisplay(60)||`` into the on start followed by ``||kitronik_halo_hd.showRainbow||`` block.

```blocks
let haloDisplay = kitronik_halo_hd.createZIPHaloDisplay(60)
haloDisplay.showRainbow()
```

```ghost
let haloDisplay = kitronik_halo_hd.createZIPHaloDisplay(60)
haloDisplay.showRainbow()
```

## Step 2 @fullscreen
If you have a @boardname@ connected, click ``|Download|`` to transfer your code and see the Halo HD display a rainbow of colours!

## Introduction @unplugged
Now we know the Halo HD is working, its time to code a clock.
The Halo HD has a component that remembers the time and increments the time.  This is called a Real Time Clock (RTC).  
The device can be controlled via two data lines from the BBC micro:bit.  With this, its possible to set and read the time (as well as other functions).

## Step 1 @fullscreen
Remove the ``||haloDisplay.showRainbow()||`` block from the code.

## Step 2 @fullscreen
The Halo HD package has a custom block that allows you to set a particular LED with a particular colour.
Place one of these ``||haloDisplay.setZipLedColor||`` in the forever loop.

```blocks
basic.forever(function () {
    haloDisplay.setZipLedColor(0, kitronik_halo_hd.colors(ZipLedColors.Red))
})
```

## Step 3 @fullscreen
Currently the code will only set LED0 to red.  We want this LED to move with the time.
Inside the clock section of the Halo HD package is the ``||kitronik_halo_hd.readTimeForZip||`` block.
Place this inside the ``||haloDisplay.setZipLedColor||``.

```blocks
basic.forever(function () {
    haloDisplay.setZipLedColor(kitronik_halo_hd.readTimeForZip(TimeParameter.Hours), kitronik_halo_hd.colors(ZipLedColors.Red))
})
```

## Step 4 @fullscreen
Now, we have the hours being set to an LED.  See if you can create the blocks but for showing the minutes and seconds..

### ~ tutorialhint
Its the same blocks but different selection on the drop downs

## Step 5 @fullscreen
The LED's have been set we need to make sure these are the only LED's to show.
Add the ``||haloDisplay.clear()||`` to the start of the forever loop. Add the ``||haloDisplay.show()||`` to the end of the forever loop.

## Step 6 @fullscreen
The forever loop will be too quick for anyone to see the LEDs being illuminated. We can slow this down by adding a ``||basic.pause()||`` set to 100 and place it after the show.

## Step 7 @fullscreen
The forever loop will beIf you have a @boardname@ connected, click ``|Download|`` to transfer your code and if the Halo HD is working as a clock!