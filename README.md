[![License: CERN-OHL-P-2.0](https://img.shields.io/badge/Hardware_License-CERN--OHL--P--2.0-blue)](https://opensource.org/license/cern-ohl-p/)
[![License: MIT](https://img.shields.io/badge/Software_License-MIT-red.svg)](https://opensource.org/licenses/MIT)

# Open Source N64 Expansion Pak

![A picture of the custom Open-Source Expansion Pak running](https://github.com/MasonStooksbury/Open-Source-N64-Expansion-Pak/blob/main/pictures/Itdo.png?raw=true)

Here are the all the files you need to create your own Expansion Pak! All you need to do is clone this repo, open the .kicad_pro file in KiCad, and you can poke around the files. Watch a video of it working [here](https://www.youtube.com/shorts/tzhRGi5v1Zo)

I use this plugin in KiCad to make it super easy to order boards with most of the correct settings: [https://www.pcbway.com/blog/News/PCBWay_Plug_In_for_KiCad_3ea6219c.html](https://www.pcbway.com/blog/News/PCBWay_Plug_In_for_KiCad_3ea6219c.html). You'll also find step-by-step instructions below.

<br><br>

# UPDATE: 05/26/2024
A potential fix has finally been found. New boards are about to be printed and I'll update on the progress as soon as I test them. Expect an update in about 2-3 weeks

# BUILD AT YOUR OWN RISK -- 12/23/2023
Recently I went to play the N64 that has been using this pak for a while and it wouldn't respond. After lots of testing, I feel like it has to be the pak. Meaning that I don't feel confident in this design anymore, and I need to do further testing to figure out what is going on. I'm glad to have videographic proof that this pak did work and didn't cause any issues at the time, but that no longer seems to be the case. While I don't know for 100% fact that this pak is the issue, it's one of the only variables, and I would rather put this warning in here now, than have people build this, brick their N64, and it be my fault because I didn't put a warning out there.

### Going forward
I intend to do more testing to isolate why exactly this is happening and work out a fix. It's really weird, doesn't seem consistent, and I'm not really sure what all needs to happen, but I'll post an update here when I have more news.

### Does not affect the OEM design repo
The OEM recreation found [here](https://github.com/MasonStooksbury/OEM-N64-Expansion-Pak) does not have this issue as it is a 1:1 replication of the original Nintendo design. So if you have any 4MB chips, you can build that one and not have to worry about this happening.

<br>
<br>

## Some things to note:

 - In order for this Pak to work you will need two 2MB RAM modules. After lots of digging, the only ones I've found that are available, work, and don't cost $25+ a piece can be found [here](https://www.questcomp.com/part/4/upd488170lg6-a60/412376032?utm_source=findchips&utm_medium=industry-cpc&utm_term=upd488170lg6-a60&utm_content=standardpricing&utm_campaign=aktype0). I realize that after buying boards and the chips that this is encroaching on the price of an OEM board from eBay. I'm currently planning out whether or not to do a Kickstarter or something to buy all of the available chips at the bulk rate and then torture myself making as many boards by hand as I can lol. No promises though; still looking at different options to make these available to more people.

 - I'm also in the process of designing a new case for this that could be 3D-printed. Not necessary, but would be a nice touch I think. I hope to have that out soon and will add it here when it's ready and tested

 - The "ExpansionPak.pretty" folder is a library containing all the footprints needed for the project. Including the Edge Connector footprint created by Bigbass (check out more of his stuff here: [https://hachyderm.io/@bigbass](https://hachyderm.io/@bigbass) and here: [https://github.com/bigbass1997](https://github.com/bigbass1997/)). This saved me countless hours and pain, so a huge shoutout to him for allowing me to use it and release it

 - The schematic is probably not in an "official" format. But it's laid out in such a way that you can easily understand which pins on the Edge Connector are connected to which pins on the RAM chip and other components. This was done on purpose as I feel it is a bit easier to understand for most people.

Thank you so much to everyone who has followed along, commented, gave me feedback, and more. It's all very much appreciated and I'm excited to be able to give back a little. And another huge shoutout to Bigbass for allowing me to use their Edge Connector as it was a perfect fit and saved me countless revisions and lots of headache.

<br>
<br>

# Making your own board

## Installing necessary software, pulling the project, and uploading everything to PCBWay
 - First, download KiCad [here](https://www.kicad.org/download/)
 - Next, install the PCBWay plugin by following the instructions [here](https://www.pcbway.com/blog/News/PCBWay_Plug_In_for_KiCad_3ea6219c.html)
 - Clone this repository or download a ZIP of the files using the green button near the top right of the page
 - Open KiCad, then open this project by navigating to where you downloaded this repo and selecting the `.kicad_pro` file
   - ![Open project](https://github.com/MasonStooksbury/Open-Source-N64-Expansion-Pak/blob/main/pictures/instructions-01.png?raw=true)
 - Once open, click on the `.kicad_pcb` file to open up the PCB so we can begin to order it
   - ![Open project](https://github.com/MasonStooksbury/Open-Source-N64-Expansion-Pak/blob/main/pictures/instructions-02.png?raw=true)
 - From there, click the PCBWay button at the top right
   - ![Open project](https://github.com/MasonStooksbury/Open-Source-N64-Expansion-Pak/blob/main/pictures/instructions-03.png?raw=true)
 - KiCad should then automatically redirect you to a browser where it has opened up PCBWay and uploaded the necessary files so that you can begin ordering. Next we need to select all the correct options so that it will be made correctly.

## Selecting the correct options in PCBWay
 - Most of these options will be selected automatically, but be sure to set the ones in the red boxes as they are either structurally required or drastically affect cost
 - ![Open project](https://github.com/MasonStooksbury/Open-Source-N64-Expansion-Pak/blob/main/pictures/instructions-04.png?raw=true)
 - ![Open project](https://github.com/MasonStooksbury/Open-Source-N64-Expansion-Pak/blob/main/pictures/instructions-05.png?raw=true)
   - `Thickness`: This has to be 1.2 otherwise it will be too thick and you risk over-bending the receiver pins in the N64 
   - `Min hole size`: This tells PCBWay how small we need the holes for some of our vias
   - `Edge connector`: By far the most important setting. This tells PCBWay that we have what is called an `edge connector` (similar to how a RAM stick looks). That way they know to setup all the particular manufacturing stuff that is required to make these
   - `HASL lead free`: This is referring to the type of plating we want on our edge connector. Most commercial edge connectors are plated with a thin layer of hard material like gold since it can handle being seated/unseated multiple times better than most other materials. However, it's *really* expensive. I encourage you to select it just to see the price jump lol. That being said, `HASL lead free` is good enough for the Expansion Pak because you won't be removing it all that often, and even if you do, it's plenty hard enough to handle it. I pick the lead free variant cause I don't want to die early from lead poisoning
   - `Surface finish`: This is the plating that will appear on the pads where you will solder things to. `HASL lead free` is plenty good enough for this and also helps with cost
   - `Remove product No`: PCBWay adds a tracking number to the silkscreen of your boards so that their manufacturing process is a little easier. You can select the `Yes` option here and pay a little extra to have them not add that. It's not a huge deal, but something to be aware of.

![KiCad view of the electrical schematic](https://github.com/MasonStooksbury/Open-Source-N64-Expansion-Pak/blob/main/pictures/schematic.png?raw=true)
![KiCad render of the front of the Expansion Pak](https://github.com/MasonStooksbury/Open-Source-N64-Expansion-Pak/blob/main/pictures/front.png?raw=true)
![KiCad render of the back of the Expansion Pak](https://github.com/MasonStooksbury/Open-Source-N64-Expansion-Pak/blob/main/pictures/back.png?raw=true)
