# Open Source N64 Expansion Pak | KiCad 9.0

![A picture of the custom Open-Source Expansion Pak running](https://github.com/MasonStooksbury/Open-Source-N64-Expansion-Pak/blob/main/pictures/Itdo.png?raw=true)

Here are all the files you need to create your own Expansion Pak! All you need to do is clone this repo, open the .kicad_pro file in KiCad, and you can poke around the files.

Fabrication can be done at JLCPCB, production files can be found under releases

<br><br>

# Changelog

- License change from CERN-OHL-P-2.0 and MIT to Attribution-NonCommercial-ShareAlike (CC BY-NC-SA 4.0) (No commercial use of this version is allowed.)
- The only approved, commercial retailers are currently: [consoles4you.ch](https://consoles4you.ch/en/open-expansion-pak) and [classicgamestore.ch](https://classicgamestore.ch/open-expansion-pak)
- Reworked the cart edge connector to be asymetrical, same as the original one
- Cleanup PCB layout
- Swap from single resistors to resistor arrays
- Add jumpers to allow for different configurations
- Reworked the 3D shell design

<br><br>

## Some things to note:

 - In order for this Pak to work you will need two 2MB RAM modules. After lots of digging, the only ones I've found that are available, work, can be found from the US [here](https://dfsales.com/upd488170lg6-a60) and from China [here](https://www.questcomp.com/part/4/upd488170lg6-a60/412376032?utm_source=findchips&utm_medium=industry-cpc&utm_term=upd488170lg6-a60&utm_content=standardpricing&utm_campaign=aktype0)

 - The "ExpansionPak.pretty" folder is a library containing all the footprints needed for the project. Including the Edge Connector footprint created by Bigbass and corrected by Consoles4You (check out more of Bigbass stuff here: [https://hachyderm.io/@bigbass](https://hachyderm.io/@bigbass) and here: [https://github.com/bigbass1997](https://github.com/bigbass1997/)).

<br><br>

# Making your own housing
You can find all the .stl files and instructions on how to print here:
 - [Printables](https://www.printables.com/model/1301125-nintendo-64-open-expansion-pak-shell)

 - The design has a 25x25mm cutout to fit a heatsink. It is recommended to use a tall heatsink made from copper for better heat transmission. Here is a link to a matching one on [Aliexpress](https://s.click.aliexpress.com/e/_ooNrkfH) (affiliate link). If you get this heatsink you can use the file with the grills so that the heatsink is better kept in place.

<br><br>

# Making your own PCB

Navigate to the releases and download the latest release files for JLCPCB.
You can also use the KiCad files to generate production files for any other PCB manufacturer.

## Selecting the correct options in JLCPCB
 - Most of these options will be selected automatically, but be sure to set the ones in the red boxes as they are either structurally required or drastically affect cost
 - `Thickness`: This has to be 1.2 otherwise it will be too thick and you risk over-bending the receiver pins in the N64 
 - `Gold Finger`: By far the most important setting. This tells JLCPCB that we have what is called an `edge connector` (similar to how a RAM stick looks). That way they know to setup all the particular manufacturing stuff that is required to make these
 - `ENIG 2U` or `ENIG 1U`: This is referring to the type of plating we want on our edge connector. We want this to be in gold so that our Exp Pak can survive a few cycles (1U: 50 cycles, 2U 100 cycles) and is less prone to oxidation
 - `Remove product No`: JLCPCB adds a tracking number to the silkscreen of your boards so that their manufacturing process is a little easier. You can select the `Remove Mark` option here at no extra cost to have them not add that. It's not a huge deal, but something to be aware of.

*__NOTE__* - You will have to bevel the edge of cart edge manually as JLCPCB does not do bevelled edges on PCBs smaller than 700mm x 700mm

<br><br>

# PDF Schematic

You can find the schematic as a pdf [here](https://github.com/MasonStooksbury/Open-Source-N64-Expansion-Pak/blob/main/files/oexp.pdf), this might be helpful if you don't use Kicad and want to know more about the jumper settings.