## Usage

### wait until button is pressed

Waits until button A is pressed before the next line of code is executed. You can also choose button B or A + B.

```blocks
WaitUntilBlocks.waitUntilButtonPressed(Button.A)
```

### wait until button is released

Waits until button A or B is released before the next line of code is executed. You can also choose button B or A + B.

```blocks
WaitUntilBlocks.waitUntilButtonReleased(Button.A)
```

### wait until pin is pressed


Waits until the chosen pin is pressed before the next line of code is executed. You can choose pin 0, 1 and 2.


```blocks
WaitUntilBlocks.waitUntilPinPressed(TouchPin.P0)
```

### wait until pin is released


Waits until the chosen pin is released before the next line of code is executed. You can choose pin 0, 1 and 2.


```blocks
WaitUntilBlocks.waitUntilPinReleased(TouchPin.P0)
```

### wait until sound level is below

This block can only be used with a micro:bit V2.

Waits until the sound level is below a chosen value before the next line of code is executed.

```blocks
WaitUntilBlocks.waitUntilSoundLevelBelow(80)
```

### wait until sound level is above

This block can only be used with a micro:bit V2.

Waits until the sound level is above a chosen value before the next line of code is executed.

```blocks
WaitUntilBlocks.waitUntilSoundLevelAbove(80)
```

## Examples

The costum block that waits for a pin to be released is useful when making games in which you close a circuit, for example by throwing a conductive ball in a basket, and the circuit is closed for more than 1 second.

It's also useful if a ball bounces a bit, closing the circuit a few times. In both cases the regular "On pin pressed" block doesn't work.

```blocks
let score = 0
basic.showNumber(score)
basic.forever(function () {
    if (input.pinIsPressed(TouchPin.P0)) {
        score += 1
        basic.showNumber(score)
        WaitUntilBlocks.waitUntilPinReleased(TouchPin.P0)
    }
})
```


To get a quick idea of what the other blocks do, you can test this code:

```blocks
WaitUntilBlocks.waitUntilButtonPressed(Button.A)
basic.showIcon(IconNames.Yes)
WaitUntilBlocks.waitUntilButtonReleased(Button.A)
basic.showIcon(IconNames.Heart)
WaitUntilBlocks.waitUntilPinPressed(TouchPin.P0)
basic.showIcon(IconNames.Butterfly)
WaitUntilBlocks.waitUntilPinReleased(TouchPin.P0)
basic.showIcon(IconNames.Duck)
WaitUntilBlocks.waitUntilSoundLevelBelow(80)
basic.showIcon(IconNames.Happy)
```

You have to press button A and touch P0 before the micro:bit will detect a sound below level 80 and to be able to get the happy face at the end. The advantage of the "wait until" blocks is that you don't need a variable to make this happen. That makes it more beginner friendly.

This idea can also be used when making an alarm, for example with ABBA as secret code, meaning you have to press button A, press button B twice and press A again to put on or off an alarm.

```blocks
input.onButtonPressed(Button.A, function () {
    pushed_how_many_times += 1
})
input.onButtonPressed(Button.B, function () {
    pushed_how_many_times += 1
})
let pushed_how_many_times = 0
basic.showIcon(IconNames.No)
WaitUntilBlocks.waitUntilButtonPressed(Button.A)
WaitUntilBlocks.waitUntilButtonReleased(Button.A)
WaitUntilBlocks.waitUntilButtonPressed(Button.B)
WaitUntilBlocks.waitUntilButtonReleased(Button.B)
WaitUntilBlocks.waitUntilButtonPressed(Button.B)
WaitUntilBlocks.waitUntilButtonReleased(Button.B)
WaitUntilBlocks.waitUntilButtonPressed(Button.A)
WaitUntilBlocks.waitUntilButtonReleased(Button.A)
if (pushed_how_many_times == 4) {
    basic.showIcon(IconNames.Yes)
} else {
    basic.showIcon(IconNames.Sad)
}
```

More examples can be found on this blog: https://tinker-club.blogspot.com/p/makecode-extension.html

## Gebruiken als extensie

Deze repository kan worden toegevoegd als **extensie** in MakeCode.

* open [https://makecode.microbit.org/](https://makecode.microbit.org/)
* klik op **Nieuw project**
* klik op **Extensies** onder het tandwielmenu
* zoeken naar **https://github.com/teacherpinky/wait-until-blocks** en importeren

## Dit project bewerken ![Badge buildstatus](https://github.com/teacherpinky/wait-until-blocks/workflows/MakeCode/badge.svg)

Om deze repository te bewerken in MakeCode.

* open [https://makecode.microbit.org/](https://makecode.microbit.org/)
* klik op **Importeren** en klik vervolgens op **Importeer URL**
* plak **https://github.com/teacherpinky/wait-until-blocks** en klik op importeren


#### Metadata (gebruikt voor zoeken, rendering)

* for PXT/microbit
<script src="https://makecode.com/gh-pages-embed.js"></script><script>makeCodeRender("{{ site.makecode.home_url }}", "{{ site.github.owner_name }}/{{ site.github.repository_name }}");</script>
