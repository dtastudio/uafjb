all: payload.bin

clean:
	rm payload.elf payload.bin

../lib/lib.a:
	cd ../lib; make

payload.elf: ../lib/lib.a dbg.c main.c
	gcc -g -isystem ../../8cc/freebsd-headers -nostdinc -nostdlib -static ../lib/lib.a -D__PS4__ dbg.c main.c -o payload.elf

payload.bin: payload.elf
	objcopy payload.elf --only-section .text --only-section .data --only-section .bss --only-section .rodata -O binary payload.bin
