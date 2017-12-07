# Design Notes for my DYI Eletric Longboard
Here are my design notes and the parts and resources I used to build my electric longboard

## Drivetrain
Recommended parts: http://www.electric-skateboard.builders/t/new-builder-list-of-known-and-commonly-used-parts/2983

## Sizing Estimates + Calculations
http://www.elektro-skateboard.de/wiki/wissenswertes/strom-spannung-reichweite-vii
http://calc.esk8.today

## Continuous Power Draw
* 4P: max rated current per pack is 2C, 5.5A/cell → max 22A continuous draw
* 7P: max rated current per pack is 2C, 5.5A/cell → max 38.5A continuous draw

## Drivetrain Calculations
* 6S, 245kV (SK3), 70mm, 36t/15t → 29.1 km/h @ 15.4A
* 6S, 245kV (SK3), 80mm, 36t/15t → 33.3 km/h @ 21.8A
* 6S, 245kV (SK3), 90mm, 36t/15t → 38.4 km/h @ 32.2A
* 8S, 245kV (SK3), 70mm, 36t/15t → 38.8 km/h @ 24.8A    
* 8S, 245kV (SK3), 80mm, 36t/15t → 44.3 km/h @ 35.8A
* 10S, 245kV (SK3), 70mm, 36t/15t → 48.5 km/h @ 36.8A
* 10S, 245kV (SK3), 80mm, 36t/15t → 55.4 km/h @ 53.7A


## Ideal Motor kV
Forum recommends max 60k eRPM on VESC (8571 motor RPM with a 14 pole). 8571/pack voltage gives ideal motor kV. LiPos under load are at 3.8V for the longest time of discharge. 
* 6S:   8571 / (6*3.8) = 376 kV
* 8S:   8571 / (8*3.8) = 282 kV
* 10S: 8571 / (10*3.8) = 225 kV

## Motor
https://hobbyking.com/de_de/turnigy-aerodrive-sk3-6364-245kv-brushless-outrunner-motor.html
* 245kV
* 2700W
* 10S
* 8mm shaft
Not sensored! But OK for most (says forum), especially with VESC 
Dimensions: https://hobbyking.com/media/file/s/k/sk3-6364_dt5035-14p_motor_edited__2.pdf


## ESC
https://www.banggood.com/FVT-CBWI120A-ESC-Brushless-Speed-Controller-For-110-and-18Series-RC-Cars-Skateboard-ESC-p-985970.html
* Has skateboard firmware, programmable with set key/led flashes

Manuals: 
* http://img.banggood.com/file/products/20151109031117FVT%20ESC%20Manual_141227.pdf
* http://img.banggood.com/file/products/20151109031144Car%20ESC%20set%20button-1%20(FVT).doc

USB Programmer (7,50€)
* https://www.banggood.com/RC-Car-Program-Card-For-FTV-Series-Car-Brushless-ESC-USB-Link-Card-p-985974.html

Skateboard firmware: 
* http://www.electric-skateboard.builders/t/has-anybody-had-issues-with-their-120a-fvt-escs/829/18
* recommends 161214 fw (brakeLine / linear brake...) from http://szfvt.com/en/download-25-5-6-6.html
* attention: skateboard firmware on banggood site is 160406 (brakeStrong...)
* More info: http://makertuts.com/build-electric-longboard-tutorial/#tab-1501905592008-2-2
* https://www.youtube.com/watch?v=Nu4t1w3NTsM (settings + test)

### Max Current for FVT 120A ESC
According to datasheet, each MOSFET can sustain 100A continuous at max 100 °C. Max temperature is 150 °C. Pulsed drain current can be up to 400A . MOSFETs on the board are IRFH5301. Datasheet: https://www.infineon.com/dgdl/irfh5301pbf.pdf?fileId=5546d462533600a40153561b477b1ebe


## Truck mounting kit and Gear ratio
Note: Aliendrive gear ratio is 2! (32t / 15t)

15mm belt, 8mm shaft. Gears: 15 (drive), 36 (wheel)
* https://hobbyking.com/en_us/catalog/category/view/s/electric-skateboard-conversion-kit/id/7590/?wrh=7
* Set also has truck, assuming best fitment, least hassle
* Gears are for 8mm shaft
* Gear ratio: 36/15 = 2.4

## Battery Pack
DYI, 6s4p + 4s4p, from old laptop 18650 cells, with ebay 18650 holders

### Cell datasheet
Panasonic NCR18650: 
* https://engineering.tamu.edu/media/4247819/ds-battery-panasonic-18650ncr.pdf
* https://na.industrial.panasonic.com/sites/default/pidsa/files/ncr18650.pdf
* Capacity: 2900mAh
* Discharge: 2C max (5.5A) 
* Standard Charge: 4.2V @ 0.3C (825mA), max 0.7C (1900mA)
* Cut-off voltage: 2.5V
* 5A discharge curve: http://www.dampfakkus.de/akkutest.php?id=121&a=5
* Chemistry: NCA
* https://batterybro.com/blogs/18650-wholesale-battery-reviews/18880255-battery-chemistry-finally-explained

### Max Power Draw Estimate
vedder.se data logging videos show max 50A (clamped, VESC feature. Car ESCs don't clamp!), 37 km/h, 1200W draw during hardest acceleration: https://youtu.be/nGb-zt2Jp9k

4P pack
* 50A / 4 = 12.5A per cell, Cell max: 5.5A → 2.3x above datasheet max!
7P pack
* 50A / 7 = 7.1A per cell, Cell max: 5.5A → 1.3x above datasheet max

## Charger
Imax B6AC V2 (max 6s), balancing charger


## Capacity and Voltage Display
http://www.ebay.de/itm/LY6-8V-63V-Lithium-Battery-Capacity-Tester-12V-48V-Lead-acid-Indicator-BI665/322503659312?_trkparms=aid%3D555018%26algo%3DPL.SIM%26ao%3D2%26asc%3D20140117130753%26meid%3D42048d9cc1e44a9b8ee9989d608406a0%26pid%3D100005%26rk%3D3%26rkt%3D6%26sd%3D291565640012&_trksid=p2047675.c100005.m1851

## Wheels
https://www.ebay.com/itm/Cal-7-90mm-78A-Longboard-Flywheel-Skateboard-Orange-Wheel-Free-Bearings/362080921175?hash=item544db46657:g:jtEAAOSwxh1ZoFzs

## Accessories
Anti-spark connectors, as battery connector + main power switch
* https://hobbyking.com/de_de/xt90-s-anti-spark-connector-2pairs-bag.html
Power switch
* http://www.ebay.de/itm/19mm-12V-KFZ-Schalter-Drucktaster-Taster-Druckschalter-LED-Beleuchtet-Blau-HY/371932020013?_trkparms=aid%3D888007%26algo%3DDISC.MBE%26ao%3D1%26asc%3D46153%26meid%3D2c555a946659458cb913be5bcba83c6c%26pid%3D100009%26rk%3D1%26rkt%3D1%26sd%3D291925934926&_trksid=p2047675.c100009.m1982
Cables + Connectors
* 10AWG wire, 22 AWG wire
* Balancer plug
* Solid copper wire for battery holder

## Deck, Trucks
https://www.amazon.de/Osprey-Longboard-Twin-flameskull-TY5252/dp/B009FUN54Y

## Remote
https://www.amazon.de/gp/aw/d/B073GX83NH/ref=pd_aw_fbt_200_img_2?ie=UTF8&psc=1&refRID=ZVD71XJBYTE2EMCK0ZE0

## Enclosure
DYI, 2mm aluminium sheet

Aluminum, custom size (length x height) possible, use 1.5mm width
http://www.ebay.de/itm/Alublech-0-5-4-mm-Aluminiumblech-ALMg3-Zuschnitt-Format-nach-Mas-Alu-Neu-/171747996796?var=&hash=item27fcfa747c:m:mc2T-lqpOOlLfsBUaAyTSzg

## Fuse
Datasheet: http://www.mta.it/flex/cm/pages/ServeAttachment.php/L/EN/D/2%252Fb%252F6%252FD.cf85c11584525294b9b5/P/BLOB%3AID%3D39/E/pdf

80A should be enough. This one breaks at 120A after 100s. (5s at 200A). 

