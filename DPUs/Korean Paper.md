#### Glossary
- Die = small block of semiconducting material in which a integrated circuit is fabricated
- TSV = Through Silicion Via
vertical electronic connection that passes throught the chip, used to create 3D integrated circuits and seems to be faster than package-on-package connections.
- Slew Rate = Maximum rate an amplifier can respond to an abrupt change of input level

### Paper analysis

![[Pasted image 20220921164902.png]]

Comparison between the P2P arch and the Multi-drop one.

The main difference seems to be that each core in each layer has a RX and TX channel and to all work they had a MUX that is said to be complicated and slow. The new arch has no MUX and less RX and TX channels in each layer

It also has some sort of self-repair of the connections between the 3d stack for some of them



