all:
	arm-none-eabi-gcc -o test.o -c test.S -mthumb -mcpu=cortex-m3 -g3
	arm-none-eabi-gcc -o main.o -c main.c -mthumb -mcpu=cortex-m3 -Os -g3
	arm-none-eabi-gcc -o sram.elf ./test.o ./main.o -nostartfiles -nostdlib -Tram.ld -mcpu=cortex-m3 -mthumb -g3
