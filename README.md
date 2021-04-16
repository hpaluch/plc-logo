# Samples for Siemens PLC LOGO! 8

Here are sample projects for `Siemens PLC LOGO! 8` series.

Used hardware:

- Bought on Conrad.cz:
  * [LOGO 12/24RCE][Logo-12-24-RCE-Conrad] from [LOGO 12/24RCE Starter Kit][Starter-Kit-Conrad]

- Siemens pages for these products are:
  - `Starter Kit` - `6ED1057-3BA01-0AA8`
    - https://mall.industry.siemens.com/mall/en/WW/Catalog/Product/6ED1057-3BA01-0AA8
  - `LOGO! 12/24RCE` - `6ED1052-1MD08-0BA0`
     - https://mall.industry.siemens.com/mall/cs/cz/Catalog/Product/6ED1052-1MD08-0BA0

Used software:
* OS: `XP SP3` in Virtual Box VM (use Network Interface that can access
  PLC via TCP/IP)
* `LOGO!Soft Comfort` version 8.2.1


# Examples

## Staircase timer - basic

Stairway light control using Push-button. Also
uses Base Module (BM) display to show status.

Diagram: 

![PLC Logo Staircase timer diagram](https://github.com/hpaluch/plc-logo/blob/master/assets/plc-logo-staircase-switch-diagram.png?raw=true)

Prototype (low-voltage bulb) photo:

![PLC Logo Staircase timer photo](https://github.com/hpaluch/plc-logo/blob/master/assets/plc-logo-starcaise-photo.jpg?raw=true)


File: `StairCaseSwitch.lsc` 

Status: early prototype

## Staircase timer - with potentiometer

Staircase timer where interval is set
by Potentiometer (5KOHm - actually I used 4K7 in prototype, becasue
I have no 5K in stock) - using Analog Input
of LOGO 12/24RCE.

Most important component is "Analog Amplifier" where I set:
- Offset: `10` (was `0`) - to have minimum timeout of 10 seconds (was `0`)
- Gain: `0.3` (was `1.0`) -  to have maximum timeout 300+10 (310 seconds).

File: `StairCaseSwitchWithPot.lsc` 

Status: early prototype

Diagram: 

![PLC Logo Staircase timer with POT diagram](https://github.com/hpaluch/plc-logo/blob/master/assets/staircase-with-pot/plc-logo-staircase-switch-with-pot-diagram.png?raw=true)

Prototype photo:

![PLC Logo Staircase timer with POT photo](https://github.com/hpaluch/plc-logo/blob/master/assets/staircase-with-pot/plc-logo-starcaise-pot-photo.jpg?raw=true)

And schema (created in KiCAD):

![PLC Logo Staircase timer with POT schema](https://github.com/hpaluch/plc-logo/blob/master/assets/staircase-with-pot/plc-with-pot-schem.png?raw=true)


## Troubleshooting

### "No program" error after Comfort programming

If you use improper target version in Comfort that PLC will refuse
to start uploaded program with strange error "No program".

To explain: There are 3 options in my LOGO Comfort version 8.2.1:
- `LOGO! 8.FS4` (name `LOGO! 8.FS4_1`)
- `LOGO! 0BA8` (name `Logo8_2`)
- `LOGO! 0BA7` (name `Logo7_1`)

So I change `8.FS4` to `Logo8_2` which seems to work properly.
Also when I look into PLC menu:
- Diagnostics -> Software -> FW Version: `1.82.02`


### PLC Logo refuses to start on power up

PLC Logo does not start, on pressing ESC it just prints
"detecting..." and after a while fall to sleep again.

Cause: Too low power supply voltage (encountered with 9V Supply, which is of
course out of specs)

Solution: Use proper 12V Supply.


[Logo-12-24-RCE-Conrad]: https://velkoobchod.conrad.cz/plc-ridici-modul-siemens-logo-12-24rce-6ed1052-1md08-0ba0-12-v-dc-24-v-dc.k1628679?gclid=EAIaIQobChMIuLvS8Z7S5AIVF5zVCh3_FQhzEAQYASABEgKoLPD_BwE
[Starter-Kit-Conrad]: https://www.conrad.cz/startovaci-sada-pro-plc-siemens-logo-starter-kit-12-24rce-6ed1057-3ba01-0aa8-12-v-dc-24-v-dc.k1302216
