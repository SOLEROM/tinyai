

burn
		openocd -s /data/tinyai/maxCNN/sdk/Tools/OpenOCD/scripts -f interface/cmsis-dap.cfg -f target/max78000.cfg  -c "program build/max78000.elf reset exit"
serial
		sudo minicom -wD /dev/ttyACM0
