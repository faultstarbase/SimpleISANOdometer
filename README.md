# SimpleISANOdometer

## Requirements

* [ISAN2 with speed enabled]() (requires an [advanced YOLOL]() chip)
  * Obviously this incurs a restriction on the Odometer: it will only work within ISAN range!
* A [basic YOLOL chip]() and some kind of socket in which it can run
* A [hybrid button]()
* A [text display]()
* Three device fields for storage (`:r`, `:LOdo`, `:TOdo`)
  * These can be deployed in a variety of ways: [memory chip](), [progess bar](), [text display]()

## Setup

1. Deploy the **text display** and name it `Odometer`
1. Deploy the **hybrid button** with the following field settings:
| Name | Value |
| --- | --- |
| TripOdoRes | 1 |
| ButtonOnStateValue | 4 |
| ButtonOffStateValue | 1 |
| ButtonStyle | 0 |
1. Deploy your chosen memory device(s) that provide 3 device fields, and name them:
  1. `LOdo`
  2. `TOdo`
  3. `r`
1. Copy/paste the [YOLOL code](./odometer.yolol) into the **basic YOLOL chip** and deploy it
1. Add `:r=ss` to [line 16 of the ISAN YOLOL](), immediately *before* `gotox`. Or, you may just copy/paste this entire replacement line into line 16 (works with ISAN **v2.5.3**, the current version as of this writing):
```
w+=xx uu+=yy vv+=zz r=w-tu j=uu-uv v=vv-vt ej+=(ii++%3)>1 :r=ss gotox
```
  1. Note that this creates a readable device field `:r` which contains your ISAN-calculated speed!

## Usage

The lifetime odometer cannot be reset without additions to this setup.

The `TripOdoRes` button, if held momentarily, will reset the trip odometer to zero.

## Screenshots