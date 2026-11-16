# CHANGELOG

All notable changes to Phaser-DIOT are documented in this file.

## v2.0

**Release owner:** Mikołaj Sowiński (TS)

**Designers:** 
- Krzysztof Belewicz (WUT)

**Reviewers:** 
- Maciej Przybysz (TS)
- Marta Fąfara (TS)

**Contributors:** 
- Marcin Kiepiela (TS)

**Funded by:** 
- WUT ISE
- Technosystem

All schematic files updated according to DIOT template v1.4.  
Changes in respect to the previous revision:

- synchronized with v1.4 DIOT Template:
	- updated project parameters
	- updated sheet template on each page
	- 4u7F 0805 capacitors unified with DIOT Template PN
	- 100nF 0402 capacitors unified with DIOT Template PN
	- updated temperature sensor ICs (#162)
	- updated schematics sheet order
	- updated draftsman document
	- layers renamed to match DIOT template
	- added LICENSE.md and CHANGELOG.md files as per DIOT Template
	- added README.md from main branch
	- Updated SMA connectors (J2, J3, J4, J5, J6) to DELOCK_65848
- supply section rearranged for better readability and to reflect power-up sequence
	- PSU_EN P12V0 pullup removed as per DIOT template
	- added missing LEDs for: P1V8A, P1V2D, P11V5A, N11V5A
	- added missing testpoints for: P1V8A, P1V2D, P11V5A, N11V5A, P5V5A
	- PG circuit changed to monitor last power rails in the sequence, not the first ones
- fan moved from supply section to the FPGA section as it is not a supply circuit fan
- corrected DAC filter components (#158, #160)
- PN updated as per new DIOT template (#159)
- header added on AB3/Y4 IO pins (#161)
- added dipswitch for manual clock source selection (#164)
- polarity swapped on the IC5 inputs as well to fix the issue in the pcb (#165), added note regarding the polarity on the schematics
- incremented HW revision on FPGA jumpers
- front panel LED change: CLK source LED changed to power LED (PGOOD) to match DIOT template
- DAC_OUT0/ DAC_OUT1 renamed to DAC_OUTC/ DAC_OUTA to match differential output naming.
- uFL DAC outputs changed to SMA on moved to the front panel with added attenuators (#166)
	- FPGA IOs moved to different banks to make space on bank34 (the only 3V3 available) for attenuator controls:
		* FAN_PWM/ FAN_TACHO moved to bank 14
		* LED0-7 moved to bank 14
		* TERM_STAT0/1 moved to bank 35 (pullups changed to match new bank)
	- due to additional FPGA IOs, testpoints on bank 14 reduced from 6 to just 1
	- pin-swapped FPGA IOs used for attenuator configuration to simplify layout
- ADC inputs moved to pigtails (ufl)
- Front panel LEDs adjusted for new front panel design 
- added new front panel & changed associated connector positions (#155 #168)
- added fan model (#156)
- added pigtail plug 3D models to the board (#169)
- changed FPGA-JTAG programming scheme (based on EEM_FMC_Carrier):
	- added JTAG over backplane in SERVMOD
	- changed J8 JTAG header to 3V3, added voltage translators
	- added JTAG header/ EEM signal mux
	- added I2C I/O expander to drive SERVMOD in EEM variant
	- FPGA_Flash.SchDoc and FPGA_Config.SchDoc collated to share level translator ICs
- L7 connected to P3V3 instead of P2V5 (DAC IOVDD2 pin voltage changed to match FPGA bank voltage, net IOVDD25 renamed to IOVDD2_33)
- added IC13 - P1V5 rail supervisor
- Added more reliable P1V5 polygons connection between TOP and L2

BOM optimizations
- fiducials/ testpoints set to (No Bom)
- TR1, TR2, TR6A, TR6B updated from libraries
- R167 changed from 0603 to 0402 (matching R131)
- R132, R262 parameters corrected to match the rest of the project (no part change)
- R181, R256 changed from 0603 to 0402 (matching R134)
- R19, R146, R148, R155, R159, R162 changed from 0603 to 0402 (R94, R145, T_R76, T_R77)
- T_R3, T_R8, R180, R220, R255 changed from 0603 to 0402 (matching R29, ...)
- R22, R49A, R49B, R71A, R71B, R163, R191 PN updated to match the rest of the project
- R92, R36, R187A, R187B, R211, R232, R240 changed from 0603 to 0402 (matching R26, ...)
- C85 changed from 0603 16V 2.2uF to 0402 6.3V 2.2uF (matching C322, C1009)
- C211 changed from 0603 1nF 100V 10% X7R to 0603 1nF 50V 1% NP0 (matching C224A, C224B, C226A, C226B, C227A, C227B)
- C139, C178, C191, C257, C260, C264, C269, C336, C344, C348 PN updated to match the rest of the project (C218, C235)
- C42, C155, C179, C181, C253, C258, C259, C262, C263, C268, C334, C335, C337, C338, C342, C343, C346, C347, C366 changed from 16V to 25V to match the rest of the project
- C22A, C22B, C22C, C22D, C229A, C229B, C230A, C230B, C239A, C239B, C241A, C241B, T_C3, T_C4, T_C5, T_C6, T_C7, T_C8, T_C14, T_C15, T_C20, T_C21, C1, C8, C17, C18, C20, C21, C55, C309 changed to unify 0402 100nF accross the project
- C11, C31, C33, C34, C35, C37, C41, C142, C150, C157, C175, C238, C242, C161, C267, C369A, C369B, C370A, C370B, C371A, C371B, C372A, C372B, C373A, C373B, C374A, C374B, C375A, C375B, C376A, C376B, C377A, C377B changed to unify 0402 10nF accross the project
- C277A-D changed from 0603 to 0805 to match the rest of the project
- L10 parameters corrected to match the rest of the project (no part change)
- LD1, LD4, LD9, LD10, LD11, LD12, LD13, LD14, LD15, LD16, LD17, LD18, LD19, LD20, LD21, LD22, LD23A, LD23B to match DIOT Template PN

---

## Prior releases

**Designers:**
- Grzegorz Kasprowicz (WUT)
- Krzysztof Belewicz (WUT)

**Reviewers:**
- unspecified

**Contributors:**
- unspecified