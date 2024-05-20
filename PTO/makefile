.PHONY: all

all: $(patsubst %.ply,%.o,$(wildcard ply/*.ply)) $(patsubst %.ply,%.h,$(wildcard ply/*.ply))

pto: pto.c haxstring.c haxstring.h
	$(CC) $(CFLAGS) -Ofast pto.c haxstring.c -o $@

ply/%.o: ply/%.asm
	nasm $< -f elf64 -o $@
	$(RM) $<
	mv -f $(basename $<).h high/$(basename $(notdir $<)).h
	mv -f $(basename $<).o high/$(basename $(notdir $<)).o

ply/%.asm ply/%.h: ply/%.ply pto
	cd $(dir $<) && ../pto $(notdir $<) && cd ..

clean:
	$(RM) pto

cleanall: clean
	$(RM) high/*.o high/*.h
