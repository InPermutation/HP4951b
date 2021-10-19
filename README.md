# HP4951b
I want to run software on my HP4951b serial protocol analyzer.

## Board layout

I am going to name these boards by their function. They appear in top-to-bottom order, when viewed from the top of the HP4951b.

### TAPE
This board communicates with the tape device. It is not necessary to boot the machine, though the tape test functionality will fail, of course. (And, presumably, the actual tape functionality.)

![TAPE](https://user-images.githubusercontent.com/1096993/137963014-741b4ec4-fa6f-4760-84c7-4abb1266f7bc.jpg)

The board art, unfortunately, is buried under the tape header. What I can read is:

```
MADE #########?
REV C#########?
04951-########?
```

I can also see `062585` in the bottom right. There is a hand-written `DB2645` on the top connector.

Big ICs:
* NEC D80C39C microcontroller ([appears to be](https://www.cpu-world.com/CPUs/8039/index.html) based on [Intel MCS-48](https://en.wikipedia.org/wiki/Intel_MCS-48))
* National Semiconductor NSC810AN-4I RAM-IO-TIMER
* 3 EPROMs: `04951-10027 12 11 85`, `04951-10008 TAPE SM 1`, `04951-10009 TAPE SM 2`. *TODO: dump these.*
* Motorola 1820-2232, aka MC14034BCP "8-Bit Universal Bus Register"

## Resources

* [HP Bench Briefs MAY-JUNE 1984](http://hparchive.com/Bench_Briefs/HP-Bench-Briefs-1984-05-06.pdf) has an article, **Replacement Parts Cross Reference**, which helps you decode mystery HP part numbers (like 1820-1779) into "generic type" part numbers (like MC14411P) which you can actually find datasheets for.
* [HP 4951B operating and service manual](https://archive.org/details/hp4951b) is actually for the ***HP 4951A***, a not-identical but very similar machine.
