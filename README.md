
# 6T-SRAM

**6T-SRAM unit - 1 bit memory with 3 modes(HOLD,WRITE,READ)**

schematic and physical design of a memory cell using 4 NMOS and 2 PMOS.
2 NMOSs and 2 PMOSs are used to compound 2 Inverters(NOT gate). Each gate connected to the output of the other gate so that any value (logic HIGH/LOW) will be helded as long as the HOLD mode is on.
We need to state which net is considered to be the bit value "Q" and which is the complementary one "QB". The other 2 NMOSs used as switches between the NOT gates and the bit lines( BL to the Q net and BLB to the QB bet).

HOLD mode: ON - means that the switches are opened so the logic value in the cell is preserved.
           OFF -  means that the switches are closed which means we are in a READ or WRITE modes.

WRITE mode: Befor writing a value we need to load the BL with the wanted value (HIGH/LOW) and the BLB with the opposite value. After loading, we need to close the switches (means HOLD mode is off) so that thr Q and QB nets will get loaded.

READ mode: Befor reading the value from the cell, we need to set BL and BLB with HIGH values.
           After loading BL and BLB we need to close the switches (means HOLD mode is off).
           The bit line that connected to a LOW value net will have a charge leakage through 
           the NMOS transistor of the feeding NOT gate, whie the HIGH value net will remain                fully charged. The two bit lines will be connected to a high sensitive comperator 
           that can detect the charge leakage and we will determine BL and BLB will be                     connected to (+) , (-) respectively so the value we read will be Q
_______________________________________________________________________________________________

**64 (8X8) 6T-SRAM array**

The 6T-SRAM units are ordered in an 8X8 2-D array in a way that each row gets its WL Line Which controlls all of the cell's switches of the line (8 cells - 16 switches). Each coulmn get a BL and BLB lines.

If we want to HOLD the array values, all need to do is to reset (Low) all the lines (WL,BL,BLB) - **THIS IS THE DEFAULT OF THE ARRAY**.

If we want to WRITE to a specific cell, we will chose the coulm of our wanted cell, set his BL,BLB to a HIGH value. After that we will set (HIGH) only the WL line of the cell's line. That way we are implementing the WRITE operation on our specific cell.

If we want to READ a specific cell, we will choose the coulmn of our wanted cell, set it's BL,BLB to HIGH. After that we will set only the WL of the cell's line to HIGH. Each coulmn has it's oen compertor.  That way we are implementing the READ operation on our specific cell.

EXAMPLE (GOTO: 8X8 SRAM Array- Test Bench.png) : In this example we can see that we are set to WRITE or READ from cell (4,6). The 4th WL gets the electrical voltage "WL4". The 6th BL, BLB gets the electrical voltage of BL6, BLB6 respectively. All the rest of the lines are in logic LOW voltage (DGND).













