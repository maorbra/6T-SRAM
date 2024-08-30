
# 6T-SRAM

**6T-SRAM unit - 1 bit memory with 3 modes(HOLD,WRITE,READ)**

schematic and physical design of a memory cell using 4 NMOS and 2 PMOS.
2 NMOSs and 2 PMOSs are used to compound 2 Inverters(NOT gate). Each gate connected to the output of the other gate so that any value (logic HIGH/LOW) will be helded as long as the HOLD mode is on.
We need to state which net is considered to be the bit value "Q" and which is the complementary one "QB". The other 2 NMOSs used as switches between the NOT gates and the bit lines( BL to the Q net and BLB to the QB bet).

HOLD mode: ON - means that the switches are closed so the logic value in the cell is preserved.
           OFF -  means that the switches are opened which means we are in a READ or WRITE modes.

WRITE mode: Befor writing a value we need to load the BL with the wanted value (HIGH/LOW) and the BLB with the opposite value. After loading, we need to open the switches
