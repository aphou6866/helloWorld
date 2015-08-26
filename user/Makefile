include makefile.include

SHRD = .
SRCS = helloWorld.cpp \

LIBS =

OBJS = ${SRCS:%.cpp=./obj/%.cpp.o}
# LIB_OBJS = ./obj/utility.cpp.o
PROG = ${SRCS:%.cpp=./%.bin}

INCDIR = -I../../Jericho/include -I$(SHRD)


all:	clean $(LIB_OBJS) $(OBJS) $(PROG)
	@$(E) Finished $(LIB_OBJS) $< to $@

./%.bin:./obj/%.cpp.o
	@$(E) Linking $< to $@
	$(CC) $(LFLAGS) $(INCDIR) $(LIBDIR) -o $@  $(LIB_OBJS) $< $(LIBS)   2>&1 | c++filt

./obj/%.cpp.o : $(SHRD)/%.cpp
	@$(E) Compiling $< to $@
	$(CC) $(CFLAGS) $(INCDIR) -c -o $@ $<

install: $(PROG)
	@$(E) Installing $< to $@
	mkdir -p ${DESTDIR}/${SBINDIR}
	install -m 0755 $^ ${DESTDIR}/${SBINDIR}/
	
clean:
	@$(E) Removing $(OBJS), $(LIB_OBJS) and $(LIB_OBJS)
	rm -rf $(OBJS) $(LIB_OBJS) $(PROG)
