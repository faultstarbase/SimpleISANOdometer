# SimpleISANOdometer

## Requirements

* [ISAN2 with speed enabled](https://github.com/Collective-SB/ISAN) (requires an [advanced YOLOL](https://wiki.starbasegame.com/index.php/YOLOL_Chip) chip)
  * Obviously this incurs a restriction on the Odometer: it will only work within ISAN range!
* A [basic YOLOL chip](https://wiki.starbasegame.com/index.php/YOLOL_Chip) and some kind of socket in which it can run
* A [hybrid button](https://wiki.starbasegame.com/index.php/Buttons)
* A [text panel](https://wiki.starbasegame.com/index.php/Modular_displays#Text_Panel)
* Three device fields for storage (`:r`, `:LOdo`, `:TOdo`)
  * These can be deployed in a variety of ways: [memory chip](https://wiki.starbasegame.com/index.php/YOLOL_memory_chip) (this is the author's chosen method), [progess bar](https://wiki.starbasegame.com/index.php/Modular_displays#Progress_bars), text panel

## Setup

* Deploy the **text panel** and name it `Odometer`
* Deploy the **hybrid button** with the following field settings:

| Name | Value |
| --- | --- |
| `TripOdoRes` | 1 |
| `ButtonOnStateValue` | 4 |
| `ButtonOffStateValue` | 1 |
| `ButtonStyle` | 0 |

* Deploy your chosen memory device(s) to provide 3 device fields and name them:
  * `LOdo`
  * `TOdo`
  * `r`
* Copy/paste the [YOLOL code](./odometer.yolol) into the **basic YOLOL chip** and deploy it
* Add `:r=ss` to [line 16 of the ISAN YOLOL](https://github.com/Collective-SB/ISAN/blob/master/bundles/basic/ISAN-basic_bundle.yolol#L16), immediately *before* `gotox`. Or, you may just copy/paste this entire replacement line into line 16 (works with ISAN **v2.5.3**, the current version as of this writing):
```
w+=xx uu+=yy vv+=zz r=w-tu j=uu-uv v=vv-vt ej+=(ii++%3)>1 :r=ss gotox
```

Note that a secondary benefit of this setup is the creation a readable device field, `:r`, which contains your ISAN-calculated speed.

## Usage

The lifetime odometer cannot be reset without additions to this setup.

The `TripOdoRes` button, if held momentarily, will reset the trip odometer to zero.

## Screenshots

![Closeup of controls & code](https://faulty-industries.s3.us-west-1.amazonaws.com/SimpleISANOdometer/3.jpg)
![Closeup of YOLOL](https://faulty-industries.s3.us-west-1.amazonaws.com/SimpleISANOdometer/1.jpg)
![Illustrated deployment example](https://faulty-industries.s3.us-west-1.amazonaws.com/SimpleISANOdometer/2.jpg)
![In-use shot](https://faulty-industries.s3.us-west-1.amazonaws.com/SimpleISANOdometer/4.jpg)