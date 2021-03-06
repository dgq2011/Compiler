#_ makefile
# Copyright (C) 1984-1994 by Symantec
# Copyright (c) 2000-2012 by Digital Mars
# Written by Walter Bright
# All Rights Reserved
#       for C/C++ compiler parser and preprocessor (SCPP, SPP and HTOD)

# Suffixes:
#       n       WIN32 EXE
#       nd      WIN32 DLL

# Paths:

DMCDIR=\dm
DMDDIR=e:\dmd2.074

CBX=.
NTDLLSHELL=ntdllshell
TK=tk
INCLUDE=-I$(TK);$(NTDLLSHELL)\include;$(DMCDIR)\include
LIBNT=$(DMCDIR)\lib
SNN=$(LIBNT)\snn
# Where scp command copies to
SCPDIR=..\backup
SCPDIR=walter@mercury:dm

# Options:
#       TARGET          one of SCPP, SPP, HTOD for C, C++, Preprocessor
#       XFLG            other compiler switches
#       OPT             optimization switches
#       DEBUG           debug switches
#       NTDLL           dll switches
#       PREC            precompiled header switches
#       LFLAGS          flags to DOS linker
#       LINKN           linker to use for target

TARGET=

###### Flags for C++ compiler
XFLG=
OPT=
DEBUG=-gl
NTDLL=-WD
PREC=-H -HP32 -HItotal.h -HO
CFLAGS=$(INCLUDE) $(XFLG) $(OPT) $(DEBUG) -6 -D$(TARGET) -r -cpp

###### Flags for D compiler

# Additive flags for building Windows DLL
DDLLFLAGS=
# Additive flags for optimization
DOPT=-O -release -inline
# Additive flags for debug build
DDEBUG=
DFLAGS=-betterC -noboundscheck -mv=dmd.backend=. -mv=tk=tk -version=$(TARGET) $(DDLLFLAGS) $(DOPT) $(DDEBUG)

###### Flags for linking

BASE=
#LFLAGS=/map/co
LFLAGS=/map/e/f/packcode/noe;

##### Tools

# D compiler
DMD=$(DMDDIR)\windows\bin\dmd
# C++ compiler
CC=dmc
# Make program
MAKE=make
# Librarian
LIB=lib
# Delete file(s)
DEL=del
# Make directory
MD=mkdir
# Remove directory
RD=rmdir
# File copy
CP=cp
# De-tabify
DETAB=detab
# Convert line endings to Unix
TOLF=tolf
# Zip
ZIP=zip32
# Copy to another directory
SCP=$(CP)
SCP=\putty\pscp -i c:\.ssh\colossus.ppk

LINKN=$(DMCDIR)\bin\link /de


# Makerules:
.c.obj:
        $(CC) -c $(CFLAGS) $(PREC) $*

.asm.obj:
        $(CC) -c $(CFLAGS) $*

################ DUMMY #########################

noparameter:
        echo no parameter


################ RELEASES #########################

release:
        make clean
        make scppn
        make clean
        make sppn
        make clean
        make scppnd
        make clean
        make sppnd
        make clean
        make htodn
        make clean

################ NT COMMAND LINE RELEASE #########################

scppn:
#       make TARGET=SCPP OPT=-o "DEBUG=-gt -g -DSTATIC= -Nc" LFLAGS=/noi/noe/map scppn.exe
#       make TARGET=SCPP OPT=-o "DEBUG=-g -DSTATIC= -Nc" LFLAGS=/noi/noe/map/co scppn.exe
        make TARGET=SCPP OPT=-o "DEBUG= -DSTATIC= -Nc" LFLAGS=/noi/noe/map scppn.exe

sppn:
        make TARGET=SPP  OPT=-o+space DEBUG= LFLAGS=/noi/noe/map sppn.exe

htodn:
        make TARGET=HTOD XFLG=-DSCPP OPT=-o "DEBUG= -DSTATIC= -Nc" LFLAGS=/noi/noe/map htodn.exe

htod:
        make TARGET=HTOD XFLG=-DSCPP OPT=-o "DEBUG= -DSTATIC= -Nc" LFLAGS=/noi/noe/map htod.exe

################ NT COMMAND LINE DEBUG #########################

debcppn:
        make TARGET=SCPP OPT= "DEBUG=-D -g -DMEM_DEBUG" \
            DDEBUG=-debug LFLAGS=/noi/noe/co/m scppn.exe

debppn:
        make TARGET=SPP  OPT= "DEBUG=-D -g -DMEM_DEBUG" \
	    DDEBUG=-debug LFLAGS=/noi/noe/co/m sppn.exe

debhtodn:
        make TARGET=HTOD XFLG=-DSCPP  OPT= "DEBUG=-D -g -DMEM_DEBUG" \
	    DDEBUG=-debug LFLAGS=/noi/noe/co/m htodn.exe

################ NT DLL RELEASE #########################

scppnd:
        make TARGET=SCPP OPT=-o+space "XFLG=$(NTDLL)" DEBUG= DDEBUG=-debug LFLAGS=/noi/noe/map BASE=18087936 DDLLFLAGS=-version=_WINDLL scppnd.dll
#       make TARGET=SCPP OPT=-o+space "XFLG=$(NTDLL)" DEBUG=-g DDEBUG=-debug LFLAGS=/noi/noe/map/co BASE=18087936 DDLLFLAGS=-version=_WINDLL scppnd.dll

sppnd:
        make TARGET=SPP  OPT=-o+space "XFLG=$(NTDLL)" DEBUG= DDEBUG=-debug LFLAGS=/noi/noe/map BASE=21430272 DDLLFLAGS=-version=_WINDLL sppnd.dll

################ NT DLL DEBUG #########################

debcppnd:
        make TARGET=SCPP OPT= "DEBUG=-g -D -DMEM_DEBUG -DTERMCODE" "XFLG=$(NTDLL)" \
	    DDEBUG=-debug LFLAGS=/noi/noe/map/co DDLLFLAGS=-version=_WINDLL scppnd.dll

debppnd:
        make TARGET=SPP  OPT=-o+space "XFLG=$(NTDLL)" \
	    DDEBUG=-debug LFLAGS=/noi/noe/map/co DDLLFLAGS=-version=_WINDLL sppnd.dll

#########################################

OBJ1a=dblklst.obj blockopt.obj dcpp.obj debug.obj ee.obj el.obj denum.obj err.obj rawstring.obj
OBJ1b=evalu8.obj poptelem.obj eh.obj exp.obj dexp2.obj dfile.obj filename.obj func.obj adl.obj
OBJ1c=dgetcmd.obj ini.obj dinit.obj loadline.obj dmsc.obj precomp.obj dmcdll.obj
OBJ1d=nspace.obj dnwc.obj os.obj out.obj dph.obj ppexp.obj dpragma.obj pseudo.obj
OBJ1e=dstruct.obj symbol.obj dtemplate.obj tk.obj xtoken.obj type.obj dt.obj dth.obj phstring.obj
OBJ1f=var.obj nteh.obj rtlsym.obj rtti.obj dscope.obj tdbx.obj dutil.obj html.obj
OBJ1g=unialpha.obj entity.obj aa.obj ti_achar.obj ti_pvoid.obj backconfig.obj dinline.obj oper.obj parser.obj dtoken.obj

OBJ2a= cgcod.obj cod1.obj cod2.obj cod3.obj cod4.obj cod5.obj cg87.obj cgxmm.obj code.obj
OBJ2b= cg.obj cgelem.obj cgcs.obj cgcv.obj tytostr.obj cgen.obj cgreg.obj compress.obj
OBJ2c= cgobj.obj cgsched.obj objrecor.obj diasm.obj ptrntab.obj newman.obj dwarf.obj stubobj.obj
OBJ2d= go.obj gloop.obj gother.obj gflow.obj gdag.obj glocal.obj gsroa.obj pdata.obj cv8.obj
OBJ2e= errmsgs2.obj outbuf.obj bcomplex.obj htod.obj dspeller.obj utf.obj divcoeff.obj dvec.obj dlist.obj filespec.obj

ALLOBJS= $(OBJ1a) $(OBJ1b) $(OBJ1c) $(OBJ1d) $(OBJ1e) $(OBJ1f) $(OBJ1g) \
         $(OBJ2a) $(OBJ2b) $(OBJ2c) $(OBJ2d) $(OBJ2e)

#########################################

$(TARGET)n.exe : $(ALLOBJS) $(TARGET)n.lnk $(TARGET)n.def
        $(LINKN) @$*.lnk

$(TARGET)nd.dll : $(ALLOBJS) $(TARGET)nd.lnk $(TARGET)nd.def
        $(LINKN) @$*.lnk


#########################################

$(TARGET)n.def : makefile
        echo NAME $(TARGET)                     >  $*.def
        echo SUBSYSTEM CONSOLE                  >> $*.def
        echo EXETYPE NT                         >> $*.def
        echo CODE SHARED EXECUTE                >> $*.def
        echo STUB '$(LIBNT)\NTSTUB.EXE'         >> $*.def
        echo INCLUDE $(TARGET)n.tra             >> $*.def

$(TARGET)nd.def : makefile
        echo LIBRARY "$*.dll"                           > $*.def
        echo DESCRIPTION '$(TARGET) as a DLL'           >> $*.def
        echo EXETYPE NT                                 >> $*.def
        echo SUBSYSTEM WINDOWS                          >> $*.def
        echo CODE SHARED EXECUTE                        >> $*.def
        echo DATA WRITE                                 >> $*.def
        echo EXPORTS                                    >> $*.def
        echo   _$(TARGET)Version=_DllVersion@0  @1      >> $*.def
        echo   _$(TARGET)Entry=_DllEntry@12     @2      >> $*.def
        echo   _NetSpawnVersion=_NetSpawnVersion@0 @3   >> $*.def
        #echo   _NetSpawnVersion@0              @4      >> $*.def

########################################

$(TARGET)n.lnk : makefile
        echo $(OBJ1a)+                          >  $*.lnk
        echo $(OBJ1b)+                          >> $*.lnk
        echo $(OBJ1c)+                          >> $*.lnk
        echo $(OBJ1d)+                          >> $*.lnk
        echo $(OBJ1e)+                          >> $*.lnk
        echo $(OBJ1f)+                          >> $*.lnk
        echo $(OBJ1g)+                          >> $*.lnk
        echo $(OBJ2a)+                          >> $*.lnk
        echo $(OBJ2b)+                          >> $*.lnk
        echo $(OBJ2c)+                          >> $*.lnk
        echo $(OBJ2d)+                          >> $*.lnk
        echo $(OBJ2e)$(LFLAGS)                  >> $*.lnk
        echo $*                                 >> $*.lnk
        echo $*                                 >> $*.lnk
        echo tdb+                               >> $*.lnk
        echo $(SNN)+                            >> $*.lnk
        echo $(LIBNT)\kernel32+                 >> $*.lnk
        echo $(LIBNT)\user32                    >> $*.lnk
        echo $*.def;                            >> $*.lnk

$(TARGET)nd.lnk : makefile
        echo $(NTDLLSHELL)\lib\netsploc+        >  $*.lnk
        echo $(OBJ1a)+                          >> $*.lnk
        echo $(OBJ1b)+                          >> $*.lnk
        echo $(OBJ1c)+                          >> $*.lnk
        echo $(OBJ1d)+                          >> $*.lnk
        echo $(OBJ1e)+                          >> $*.lnk
        echo $(OBJ1f)+                          >> $*.lnk
        echo $(OBJ1g)+                          >> $*.lnk
        echo $(OBJ2a)+                          >> $*.lnk
        echo $(OBJ2b)+                          >> $*.lnk
        echo $(OBJ2c)+                          >> $*.lnk
        echo $(OBJ2d)+                          >> $*.lnk
        echo $(OBJ2e)$(LFLAGS)/base:$(BASE)     >> $*.lnk
        echo $*.dll                             >> $*.lnk
        echo $*                                 >> $*.lnk
        echo $(NTDLLSHELL)\lib\spwnlnd+         >> $*.lnk
        echo tdb+                               >> $*.lnk
        echo $(SNN)+                            >> $*.lnk
        echo $(LIBNT)\kernel32+                 >> $*.lnk
        echo $(LIBNT)\user32                    >> $*.lnk
        echo $*.def;                            >> $*.lnk

####################################################

test.obj : test.c

##################### INCLUDE MACROS #####################

CCH= cc.h cdef.h ty.h outbuf.h $(TK)\mem.h $(TK)\list.h $(TK)\vec.h
TOTALH=$(CCH) total.sym

##################### GENERATED SOURCE #####################

elxxx.c cdxxx.c optab.c debtab.c fltables.c tytab.c : \
        cdef.h cc.h oper.h ty.h optabgen.c
        $(CC) -cpp optabgen -I$(TK)
        optabgen

msgs2.d msgs2.h msgs2.c : msgsx.exe
        msgsx

msgsx.exe : msgsx.c
        dmc msgsx -D$(TARGET)

##################### ZIP ################################

RELEASE= sc.exe scppn.exe sppn.exe scd.dll scppnd.dll sppnd.dll

# Front end only
FRONTDSRC= ppexp.d unialpha.d entity.d html.d html.di cpp.di dmcdll.di nspace.d dinit.d \
	ini.d denum.d dinline.d loadline.d parser.d scopeh.d dtoken.d adl.d utf.di utf.d \
	objrecor.d tytostr.d filename.d precomp.d pseudo.d rtti.d eh.d exp.d \
	dstruct.d func.d dcpp.d dtemplate.d dexp2.d castab.d dgetcmd.d htod.d \
	dnwc.d dblklst.d dph.d dpragma.d phstring.di phstring.d xtoken.d rawstring.di rawstring.d \
	dscope.d dmsc.d dutil.d diasm.d dfile.d dspeller.di dspeller.d err.d page.di stubobj.d \
	poptelem.d

HTODSRC= ppexp.d unialpha.d entity.d cpp.di dmcdll.di nspace.d dinit.d \
	ini.d denum.d dinline.d loadline.d parser.d scopeh.d dtoken.d adl.d utf.d \
	objrecor.d tytostr.d filename.d precomp.d pseudo.d rtti.d eh.d exp.d \
	dstruct.d func.d dcpp.d dtemplate.d dexp2.d dgetcmd.d htod.d \
	dnwc.d dblklst.d dph.d dpragma.d phstring.d xtoken.d rawstring.d \
	dscope.d dmsc.d dutil.d diasm.d dfile.d err.d page.di stubobj.d \
	poptelem.d

FRONTSRC= allocast.h cpp.h dmcdll.h html.h parser.h scdll.h scope.h\
	tdb.h total.h \
	\
        errmsgs2.c tdbx.c \
        msgsx.c \
        trace.c dmcdll.c \
        tk.c

# Back end
BACKDSRC= bcomplex.d cc.d cdef.d cgcv.d code.c code.d code_x86.d cv4.d \
        dt.d dwarf.d dwarf2.d el.d exh.d global.d iasm.d mach.d md5.d \
        mscoff.d obj.d oper.d outbuf.d rtlsym.d ty.d type.d xmm.d \
	divcoeff.d dvec.d dlist.d filespec.d

BACKSRC= aa.h cdef.h cc.h oper.h ty.h \
	global.h code.h code_x86.h code_stub.h \
	type.h dt.h cgcv.h cv4.h \
	el.h iasm.h rtlsym.h dwarf.h dwarf2.h exh.h go.h \
	melf.h mach.h md5.h mscoff.h bcomplex.h obj.h \
	outbuf.h token.h tassert.h tinfo.h varstats.h xmm.h \
	\
	optabgen.c platform_stub.c \
	bcomplex.c blockopt.c cg.c cg87.c cgxmm.c \
	cgcod.c cgcs.c cgcv.c cgelem.c cgen.c cgobj.c \
	cgreg.c var.c compress.c \
	cgsched.c cod1.c cod2.c cod3.c cod4.c cod5.c \
	code.c symbol.c debug.c dt.c ee.c el.c \
	evalu8.c go.c gflow.c gdag.c gsroa.c \
	gother.c glocal.c gloop.c newman.c \
	nteh.c os.c out.c outbuf.c ptrntab.c rtlsym.c \
	type.c \
	elfobj.c \
	dwarf.c machobj.c \
	strtold.c aa.c ti_achar.c \
	md5.c ti_pvoid.c ph2.c util2.c \
	mscoffobj.c pdata.c cv8.c backconfig.c \
	divcoeff.d dwarfeh.c varstats.c \
	backend.txt

SRC= $(FRONTSRC) $(FRONTDSRC) $(BACKSRC) $(BACKDSRC)

TKSRC= $(TK)\mem.h $(TK)\list.h $(TK)\vec.h $(TK)\filespec.h \
        $(TK)\mem.c $(TK)\filespec.c \
        $(TK)\mem.di

SHELLSRC= $(NTDLLSHELL)\include\dllrun.h $(NTDLLSHELL)\include\network.h \
        $(NTDLLSHELL)\include\nsidde.h $(NTDLLSHELL)\include\netspawn.h

LIBSRC= $(NTDLLSHELL)\lib\spwnlnd.lib $(NTDLLSHELL)\lib\netsploc.obj

BUILDSRC= sppn.tra sccn.tra htodn.tra scppn.tra makefile posix.mak

LICENSE= license.txt gpl.txt

VERSION=857

htod.exe : $(HTODSRC) msgs2.d dspeller.obj castab.d
	$(DMD) $(DFLAGS) $(HTODSRC) msgs2.d dspeller.obj -J.

zip:
        del dm$(VERSION).zip
        zip32 -u dm$(VERSION) $(RELEASE)

zipsrc:
        del dm$(VERSION)src.zip
        zip32 -u dm$(VERSION)src $(SRC) tdb.lib $(LICENSE) backend.txt
        zip32 -u dm$(VERSION)src $(TKSRC)
        zip32 -u dm$(VERSION)src $(SHELLSRC)
        zip32 -u dm$(VERSION)src $(LIBSRC)
        zip32 -u dm$(VERSION)src $(BUILDSRC)

detab:
        detab $(SRC) $(TKSRC) $(SHELLSRC)

tolf:
        tolf $(SRC) $(TKSRC) $(SHELLSRC) $(BUILDSRC) $(LICENSE)

install:
        cp $(SRC) $(BUILDSRC) tdb.lib $(LICENSE) \dm\src\dmc
        cp $(TKSRC) \dm\src\dmc\tk
        cp $(SHELLSRC) \dm\src\dmc\ntdllshell\include
        cp $(LIBSRC) \dm\src\dmc\ntdllshell\lib

installbin:
        cp scppn.exe sppn.exe scppnd.dll sppnd.dll htodn.exe \dm\bin

git: detab tolf $(BUILDSRC)
        $(SCP) $(SRC) $(BUILDSRC) tdb.lib $(LICENSE) $(SCPDIR)/Compiler/dm/src/dmc/
        $(SCP) $(TKSRC) $(SCPDIR)/Compiler/dm/src/dmc/tk
        $(SCP) $(SHELLSRC) $(SCPDIR)/Compiler/dm/src/dmc/ntdllshell/include
        $(SCP) $(LIBSRC) $(SCPDIR)/Compiler/dm/src/dmc/ntdllshell/lib

gitback: detab tolf $(BACKSRC)
        $(SCP) $(BACKSRC) walter@mercury:forks/dmd/src/backend/


##################### SPECIAL BUILDS #####################

total.sym : $(CCH) token.h parser.h el.h scope.h global.h obj.h type.h oper.h cpp.h dmcdll.h \
 $(TK)\filespec.h dt.h msgs2.h bcomplex.h total.h
        $(CC) -c $(CFLAGS) -HFtotal.sym total.h

os.obj : os.c
        $(CC) -c $(CFLAGS) os.c

strtold.obj : strtold.c
        $(CC) -c -o strtold.c

adl.obj : adl.d
        $(DMD) -c $(DFLAGS) adl.d

dblklst.obj : dblklst.d
        $(DMD) -c $(DFLAGS) dblklst.d

dcpp.obj : dcpp.d
        $(DMD) -c $(DFLAGS) dcpp.d

denum.obj : denum.d
        $(DMD) -c $(DFLAGS) denum.d

err.obj : err.d
        $(DMD) -c $(DFLAGS) err.d

dexp2.obj : dexp2.d castab.d
        $(DMD) -c $(DFLAGS) -J. dexp2.d

dfile.obj : dfile.d
        $(DMD) -c $(DFLAGS) -J. dfile.d

dgetcmd.obj : dgetcmd.d
        $(DMD) -c $(DFLAGS) dgetcmd.d

diasm.obj : diasm.d
        $(DMD) -c $(DFLAGS) diasm.d

dmsc.obj : dmsc.d
        $(DMD) -c $(DFLAGS) dmsc.d

dnwc.obj : dnwc.d
        $(DMD) -c $(DFLAGS) dnwc.d

dph.obj : dph.d page.di
        $(DMD) -c $(DFLAGS) dph.d

dpragma.obj : dpragma.d
        $(DMD) -c $(DFLAGS) dpragma.d

dscope.obj : dscope.d
        $(DMD) -c $(DFLAGS) dscope.d

dspeller.obj : dspeller.d
        $(DMD) -c $(DFLAGS) dspeller.d

dtemplate.obj : dtemplate.d
        $(DMD) -c $(DFLAGS) dtemplate.d

filespec.obj : filespec.d
        $(DMD) -c $(DFLAGS) filespec.d

func.obj : func.d
        $(DMD) -c $(DFLAGS) func.d

ini.obj : ini.d
        $(DMD) -c $(DFLAGS) ini.d

dinit.obj : dinit.d
        $(DMD) -c $(DFLAGS) dinit.d

nspace.obj : nspace.d
        $(DMD) -c $(DFLAGS) nspace.d

divcoeff.obj : divcoeff.d
        $(DMD) -c $(DFLAGS) divcoeff.d

dvec.obj : dvec.d
        $(DMD) -c $(DFLAGS) dvec.d

loadline.obj : loadline.d msgs2.d
        $(DMD) -c $(DFLAGS) loadline.d

dinline.obj : dinline.d
        $(DMD) -c $(DFLAGS) dinline.d

html.obj : html.d
        $(DMD) -c $(DFLAGS) html.d

htod.obj : htod.d
        $(DMD) -c $(DFLAGS) htod.d

oper.obj : oper.d
        $(DMD) -c $(DFLAGS) oper.d

parser.obj : parser.d
        $(DMD) -c $(DFLAGS) parser.d

poptelem.obj : poptelem.d
        $(DMD) -c $(DFLAGS) poptelem.d

precomp.obj : precomp.d
        $(DMD) -c $(DFLAGS) precomp.d

dlist.obj : dlist.d
        $(DMD) -c $(DFLAGS) dlist.d

dstruct.obj : dstruct.d
        $(DMD) -c $(DFLAGS) dstruct.d

dth.obj : dt.d
        $(DMD) -c $(DFLAGS) dt.d -ofdth.obj

dtoken.obj : dtoken.d
        $(DMD) -c $(DFLAGS) dtoken.d

xtoken.obj : xtoken.d
        $(DMD) -c $(DFLAGS) xtoken.d

dutil.obj : dutil.d
        $(DMD) -c $(DFLAGS) dutil.d

eh.obj : eh.d
        $(DMD) -c $(DFLAGS) eh.d

entity.obj : entity.d
        $(DMD) -c $(DFLAGS) entity.d

exp.obj : exp.d
        $(DMD) -c $(DFLAGS) exp.d

filename.obj : filename.d
        $(DMD) -c $(DFLAGS) filename.d

objrecor.obj : objrecor.d
        $(DMD) -c $(DFLAGS) objrecor.d

phstring.obj : phstring.d
        $(DMD) -c $(DFLAGS) phstring.d

ppexp.obj : ppexp.d
        $(DMD) -c $(DFLAGS) ppexp.d

pseudo.obj : pseudo.d
        $(DMD) -c $(DFLAGS) pseudo.d

rawstring.obj : rawstring.d
        $(DMD) -c $(DFLAGS) rawstring.d

rtti.obj : rtti.d
        $(DMD) -c $(DFLAGS) rtti.d

stubobj.obj : stubobj.d
        $(DMD) -c $(DFLAGS) stubobj.d

tytostr.obj : tytostr.d
        $(DMD) -c $(DFLAGS) tytostr.d

unialpha.obj : unialpha.d
        $(DMD) -c $(DFLAGS) unialpha.d

utf.obj : utf.d
        $(DMD) -c $(DFLAGS) utf.d

################# Source file dependencies ###############

DEP=total.sym msgs2.h msgs2.c elxxx.c cdxxx.c optab.c debtab.c fltables.c tytab.c

aa.obj : aa.h tinfo.h aa.c
backconfig.obj : $(DEP) $(backconfig.dep) backconfig.c
bcomplex.obj : bcomplex.h bcomplex.c
blockopt.obj : $(DEP) $(blockopt.dep) blockopt.c
cg.obj : $(DEP) $(cg.dep) cg.c
cgcs.obj : $(DEP) $(cgcs.dep) cgcs.c
cgobj.obj : $(DEP) $(cgobj.dep) cgobj.c
cgreg.obj : $(DEP) $(cgreg.dep) cgreg.c
cod1.obj : $(DEP) $(cod1.dep) cod1.c
cod2.obj : $(DEP) $(cod2.dep) cod2.c
cod3.obj : $(DEP) $(cod3.dep) cod3.c
cod4.obj : $(DEP) $(cod4.dep) cod4.c
cod5.obj : $(DEP) $(cod5.dep) cod5.c
code.obj : $(DEP) $(code.dep) code.c
compressj.obj : $(DEP) $(compress.dep) compress.c
cv8.obj : $(DEP) $(cv8.dep) cv8.c
debug.obj : $(DEP) $(debug.dep) debug.c
dt.obj : $(DEP) $(dt.dep) dt.c
dwarf.obj : $(DEP) $(dwarf.dep) dwarf.h dwarf.c
dwarfeh.obj : $(DEP) $(dwarfeh.dep) dwarf.h dwarfeh.c
ee.obj : $(DEP) $(ee.dep) ee.c
el.obj : $(DEP) $(el.dep) el.c
errmsgs2.obj : $(DEP) $(errmsgs2.dep) errmsgs2.c msgs2.c
evalu8.obj : $(DEP) $(evalu8.dep) evalu8.c
glocal.obj : $(DEP) $(glocal.dep) glocal.c
gloop.obj : $(DEP) $(gloop.dep) gloop.c
nteh.obj : $(DEP) $(nteh.dep) nteh.c
out.obj : $(DEP) $(out.dep) out.c
pdata.obj : $(DEP) $(pdata.dep) pdata.c
ptrntab.obj : $(DEP) $(ptrntab.dep) iasm.h ptrntab.c
ti_achar.obj : tinfo.h ti_achar.c
ti_pvoid.obj : tinfo.h ti_pvoid.c
tk.obj : $(DEP) $(tk.dep) tk.c
type.obj : $(DEP) $(type.dep) type.c
cgcv.obj : $(DEP) $(cgcv.dep) cgcv.c
cgelem.obj : $(DEP) $(cgelem.dep) cgelem.c
gdag.obj : $(DEP) $(gdag.dep) gdag.c
dmcdll.obj : $(DEP) $(dmcdll.dep) dmcdll.c
gother.obj : $(DEP) $(gother.dep) gother.c
gsroa.obj : $(DEP) $(gsroa.dep) gsroa.c
go.obj : $(DEP) $(go.dep) go.c
gflow.obj : $(DEP) $(gflow.dep) gflow.c
cgcod.obj : $(DEP) $(cgcod.dep) cgcod.c
cgen.obj : $(DEP) $(cgen.dep) cgen.c
rtlsym.obj : $(DEP) $(rtlsym.dep) rtlsym.c
symbol.obj : $(DEP) $(symbol.dep) symbol.c
cg87.obj : $(DEP) $(cg87.dep) cg87.c
cgxmm.obj : $(DEP) xmm.h $(cgxmm.dep) cgxmm.c
outbuf.obj : $(DEP) $(outbuf.dep) outbuf.c
newman.obj : $(DEP) $(newman.dep) newman.c
tdbx.obj : $(DEP) $(tdbx.dep) tdbx.c
var.obj : $(DEP) $(var.dep) var.c

################### Utilities ################

clean:
        del *.obj
        del *.lnk
        del *.sym
        del *.dep
        del *.def
#       del *.bak
        del msgsx.exe
        del optabgen.exe
        del *.map
        del *.tmp
        del *.lst
        del *.exp
        del *.dbg
        del *.res
        del msgs.c msgs2.d msgs2.h msgs2.c elxxx.c cdxxx.c optab.c debtab.c fltables.c tytab.c

###################################
