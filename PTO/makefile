.PHONY: all

all: $(patsubst %.ply,%.o,$(wildcard ply/*.ply))

pto: pto.c haxstring.c haxstring.h
	$(CC) $(CFLAGS) -Ofast pto.c haxstring.c -o pto

ply/%.o: ply/%.asm
	nasm $< -f elf64 -o $@ && mv -f $(basename $<).o high/$(basename $(notdir $<)).o && $(RM) $(basename $<).asm

ply/%.asm: ply/%.ply pto
	mkdir -p high && cd $(dir $<) && ../pto $(notdir $<) && cd .. && mv -f $(basename $<).h high/$(basename $(notdir $<)).h

clean:
	$(RM) ply/*.o ply/*.asm pto

cleanall: clean
	$(RM) high/*.h
