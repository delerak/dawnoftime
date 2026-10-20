MAKE	= make
CPP 	= g++
PROF	= -g -O
OBJDIR	= obj
VPATH	= .:obj
NOCRYPT	=
C_FLAGS = -Wall $(PROF) $(NOCRYPT) -std=c++03 -fpermissive -Wno-write-strings -Wno-literal-suffix
L_FLAGS = $(PROF)
LIBS	= -lz

O_FILES = \
	act_comm.o act_ente.o act_info.o act_move.o act_obj.o \
	act_wiz2.o act_wiz.o aedit.o affects.o alias.o areas.o autostat.o \
	banedit.o ban.o base64.o bit.o cedit.o channels.o chardata.o \
	clanedit.o clan.o class.o colour.o comedit.o comm.o const.o \
	connect.o corpse.o cust_col.o d2magsys.o dawnlib.o dawnlog.o dawnstat.o \
	db2.o db.o debug.o deity.o duel.o dynamics.o dyntable.o effects.o \
	entity.o events.o exitlist.o ey_crypt.o fight.o flags.o ftp.o gamble.o \
	gameedit.o gio.o global.o grpedit.o handler.o healer.o hedit.o help.o \
	herbedit.o hreboot.o ictime.o immquest.o interp.o intro_ex.o \
	intro.o ispell.o jail.o langedit.o language.o laston.o letters.o lockers.o \
	lookup.o magic_ce.o magic_da.o magic_ja.o magic_ke.o magic.o magic_ob.o \
	magic_qu.o magic_ra.o magic_re.o magic_sb.o magic_ti.o map.o match.o \
	medit.o mem.o mining.o mixedit.o mix.o mp_cmds.o mud_prog.o mount.o \
	msp.o mud2web.o mxp.o namegen.o nanny.o netio.o network.o noble.o notenet.o \
	note.o obdb.o objdata.o obskill.o oedit.o offmoot.o olc_act.o olc_ex.o \
	olc_mpcd.o olc.o olc_save.o o_lookup.o password.o pushdrag.o pipe.o \
	pload.o qedit.o raceedit.o races.o recycle.o redit.o remort.o resolve.o \
	roles.o rp.o save.o saymote.o scan.o score.o scripts.o sedit.o shop.o \
	skill_ke.o skills.o skill_ti.o skill_tr.o sk_type.o socedit.o socials.o \
	special.o statset.o string.o support.o tables.o textsrch.o \
	tokens.o track.o trap.o update.o websrv.o whofmt.o who.o wizlist.o

all: dawn ../resolver

# Build the main Dawn binary
dawn: $(O_FILES) com_time.o
	-rm -f ../dawn
	$(CPP) $(L_FLAGS) -o ../dawn $(O_FILES) com_time.o $(LIBS)

com_time.o: com_time.cpp
	$(CPP) -c $(C_FLAGS) com_time.cpp -o com_time.o

# Build the resolver binary directly into parent directory
../resolver: extras/resolver.cpp
	$(CPP) $(L_FLAGS) -o ../resolver extras/resolver.cpp $(LIBS)

resolver: ../resolver

clean:
	rm -f *.o

cleanall: clean
	rm -f ../dawn
	rm -f ../resolver

rebuild: clean dawn

%.o: %.cpp dawn.h
	$(CPP) -c $(C_FLAGS) $< -o $@