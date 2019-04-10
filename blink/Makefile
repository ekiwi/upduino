
chip.bin: chip.v blink.v upduino_v2.pcf
	yosys -q -p "synth_ice40 -json chip.json" chip.v blink.v
	nextpnr-ice40 --up5k --package sg48 --pcf upduino_v2.pcf --json chip.json --asc chip.asc
	icepack chip.asc chip.bin

.PHONY: flash
flash:
	iceprog chip.bin

.PHONY: clean
clean:
	$(RM) -f chip.json chip.asc chip.bin
