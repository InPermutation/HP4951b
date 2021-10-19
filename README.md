# HP4951b
I want to run software on my HP4951b serial protocol analyzer.

## Board layout

I am going to name these boards by their function. They appear in top-to-bottom order, when viewed from the top of the HP4951b.

### TAPE
This board communicates with the tape device. It is not necessary to boot the machine, though the tape test functionality will fail, of course. (And, presumably, the actual tape functionality.)

![TAPE](https://user-images.githubusercontent.com/1096993/137963014-741b4ec4-fa6f-4760-84c7-4abb1266f7bc.jpg)

It has a 6.000000 MHz crystal.

The board art, unfortunately, is buried under the tape header. What I can read is:

```
MADE #########?
REV C#########?
04951-########?
```

I can also see `062585` in the bottom right. There is a hand-written `DB2645` on the top connector.

Big ICs:
* NEC D80C39C microcontroller ([appears to be](https://www.cpu-world.com/CPUs/8039/index.html) based on [Intel MCS-48](https://en.wikipedia.org/wiki/Intel_MCS-48))
* National Semiconductor NSC810AN-4I RAM-IO-TIMER (incl. 1K RAM)
* 3 EPROMs: `04951-10027 12 11 85`, `04951-10008 TAPE SM 1`, `04951-10009 TAPE SM 2`. *TODO: dump these.*
* Motorola 1820-2232, aka MC14034BCP "8-Bit Universal Bus Register"

### REMOTE
This board communicates with the `REMOTE / PRINTER` DE-25 (DB-25) connector on the back of the machine. It is not necessary to boot the machine, though the remote test functionality as well as the BNC video output will fail, of course. (And, presumably, the actual remote+printer functionality.)

![REMOTE](https://user-images.githubusercontent.com/1096993/137965411-dafeb3fa-a093-4a56-9e34-9a81d6ffa3c6.jpg)

It has a 1.8432 MHz crystal.

Big ICs:
  * Motorola 1820-1779, aka MC14411P Bit Rate Generator
  * Hitachi HD6350P Asynchronous Communications Interface Adapter (ACIA)

The green wire at the bottom of the photo is the BNC composite video signal.

Board Art:

```
04951-60017
REV A-2512-38
   MADE IN
    U.S.A.
   [(hp)]
88809F
090485
```
Handwritten `2645`. The bus connector has a handwritten `CW` on it.


### MEMORY
This board appears to have the program ROM and 56KB of RAM, plus the keyboard interface chip has an additional 1KB of RAM. I haven't actually tried booting without it, but I'm pretty sure it will cause the machine to not boot.

![MEMORY](https://user-images.githubusercontent.com/1096993/137967119-1db385e5-5f80-40a7-a869-91e027e16003.jpg)

Big ICs:

* National Semiconductor NSC810AN-4I RAM-IO-TIMER (incl. 1K RAM)
* 4 EPROMs: `04951-10024 12 11 85`, `04951-10022 12 10 85`, `04951-10021 12 09 85`, `04951-10023 12 10 85`
* 7 x HM6264LP-15 8KB static RAM

There is a NiCd battery in a plastic case. There is corrosion on the leads near this battery, so I need to remove it!

## Resources

* [HP Bench Briefs MAY-JUNE 1984](http://hparchive.com/Bench_Briefs/HP-Bench-Briefs-1984-05-06.pdf) has an article, **Replacement Parts Cross Reference**, which helps you decode mystery HP part numbers (like 1820-1779) into "generic type" part numbers (like MC14411P) which you can actually find datasheets for.
* [HP 4951B operating and service manual](https://archive.org/details/hp4951b) is actually for the ***HP 4951A***, a not-identical but very similar machine.
