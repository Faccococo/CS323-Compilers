CC=gcc
FLEX=flex
YACC=bison

SOURCES = $(wildcard src/*.c)
INCLUDE = $(wildcard include/*.h)

.PHONY: splc
splc: lex.l syntax.y $(SOURCES) $(INCLUDE)
	rm -r bin
	@mkdir bin
	touch bin/splc
	@chmod +x bin/splc
	$(YACC) -t -d syntax.y
	$(FLEX) lex.l
	mv *.c src/
	mv *.cc src/
	mv *.h include/
	$(CC) -Iinclude $(SOURCES) -o bin/splc -ll $(CFLAGS)
clean:
	@rm -rf bin/
	@rm -f *.yy.* *.tab.* splc