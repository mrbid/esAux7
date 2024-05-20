.PHONY: all

all: $(patsubst ply/%.ply,high/%.o,$(wildcard ply/*.ply)) $(patsubst ply/%.ply,high/%.h,$(wildcard ply/*.ply))

pto: pto.c haxstring.c haxstring.h
	$(CC) $(CFLAGS) -Ofast -march=native pto.c haxstring.c -o $@

high/%.o: ply/%.asm
	nasm $< -f elf64 -o $@
	$(RM) $<

ply/%.asm high/%.h: ply/%.ply pto
	cd $(dir $<) && ../pto $(notdir $<) && cd ..
	mv -f $(basename $<).h high/$(basename $(notdir $<)).h

clean:
	$(RM) high/*.o ply/*.asm pto

cleanall: clean
	$(RM) high/*.h
