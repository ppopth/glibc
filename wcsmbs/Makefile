# Copyright (C) 1995-2023 Free Software Foundation, Inc.
# This file is part of the GNU C Library.

# The GNU C Library is free software; you can redistribute it and/or
# modify it under the terms of the GNU Lesser General Public
# License as published by the Free Software Foundation; either
# version 2.1 of the License, or (at your option) any later version.

# The GNU C Library is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
# Lesser General Public License for more details.

# You should have received a copy of the GNU Lesser General Public
# License along with the GNU C Library; if not, see
# <https://www.gnu.org/licenses/>.

#
#	Sub-makefile for wcsmbs portion of the library.
#
subdir	:= wcsmbs

include ../Makeconfig

headers	:= wchar.h bits/wchar.h bits/wchar2.h bits/wchar2-decl.h \
	   bits/wchar-ldbl.h uchar.h bits/types/__mbstate_t.h \
	   bits/types/mbstate_t.h bits/types/wint_t.h

routines := wcscat wcschr wcscmp wcscpy wcscspn wcsdup wcslen wcsncat \
	    wcsncmp wcsncpy wcspbrk wcsrchr wcsspn wcstok wcsstr wmemchr \
	    wmemcmp wmemcpy wmemmove wmemset wcpcpy wcpncpy wmempcpy \
	    btowc wctob mbsinit \
	    mbrlen mbrtowc wcrtomb mbsrtowcs wcsrtombs \
	    mbsnrtowcs wcsnrtombs wcsnlen wcschrnul \
	    wcstol wcstoul wcstoll wcstoull wcstod wcstold wcstof \
	    wcstol_l wcstoul_l wcstoll_l wcstoull_l \
	    wcstod_l wcstold_l wcstof_l \
	    wcstod_nan wcstold_nan wcstof_nan \
	    wcscoll wcsxfrm \
	    wcwidth wcswidth \
	    wcscoll_l wcsxfrm_l \
	    wcscasecmp wcsncase wcscasecmp_l wcsncase_l \
	    wcsmbsload mbsrtowcs_l \
	    isoc99_wscanf isoc99_vwscanf isoc99_fwscanf isoc99_vfwscanf \
	    isoc99_swscanf isoc99_vswscanf \
	    mbrtoc8 c8rtomb mbrtoc16 c16rtomb mbrtoc32 c32rtomb

strop-tests :=  wcscmp wcsncmp wmemcmp wcslen wcschr wcsrchr wcscpy wcsnlen \
		wcpcpy wcsncpy wcpncpy wcscat wcsncat wcschrnul wcsspn wcspbrk \
		wcscspn wmemchr wmemset
tests := tst-wcstof wcsmbs-tst1 tst-wcsnlen tst-btowc tst-mbrtowc \
	 tst-wcrtomb tst-wcpncpy tst-mbsrtowcs tst-wchar-h tst-mbrtowc2 \
	 tst-c16c32-1 wcsatcliff tst-wcstol-locale tst-wcstod-nan-locale \
	 tst-wcstod-round test-char-types tst-fgetwc-after-eof \
	 tst-wcstod-nan-sign tst-c16-surrogate tst-c32-state \
	 test-mbrtoc8 test-c8rtomb \
	 $(addprefix test-,$(strop-tests)) tst-mbstowcs \
	 tst-wprintf-binary \
	 tst-wcstol-binary-c11 \
	 tst-wcstol-binary-c2x \
	 tst-wcstol-binary-gnu11 \
	 tst-wcstol-binary-gnu2x

include ../Rules

ifeq ($(run-built-tests),yes)
LOCALES := de_DE.ISO-8859-1 de_DE.UTF-8 en_US.ANSI_X3.4-1968 hr_HR.ISO-8859-2 \
	   ja_JP.EUC-JP zh_TW.EUC-TW tr_TR.UTF-8 tr_TR.ISO-8859-9 zh_HK.BIG5-HKSCS
include ../gen-locales.mk

$(objpfx)tst-btowc.out: $(gen-locales)
$(objpfx)tst-c16c32-1.out: $(gen-locales)
$(objpfx)tst-mbrtowc.out: $(gen-locales)
$(objpfx)tst-mbrtowc2.out: $(gen-locales)
$(objpfx)tst-wcrtomb.out: $(gen-locales)
$(objpfx)wcsmbs-tst1.out: $(gen-locales)
$(objpfx)tst-wcstol-locale.out: $(gen-locales)
$(objpfx)tst-wcstod-nan-locale.out: $(gen-locales)
$(objpfx)tst-c16-surrogate.out: $(gen-locales)
$(objpfx)tst-c32-state.out: $(gen-locales)
$(objpfx)test-c8rtomb.out: $(gen-locales)
$(objpfx)test-mbrtoc8.out: $(gen-locales)
endif

$(objpfx)tst-wcstod-round: $(libm)

CFLAGS-wcwidth.c += -I../wctype
CFLAGS-wcswidth.c += -I../wctype

strtox-CFLAGS = -I../include
CFLAGS-wcstol.c += $(strtox-CFLAGS) $(config-cflags-wno-ignored-attributes)
CFLAGS-wcstoul.c += $(strtox-CFLAGS) $(config-cflags-wno-ignored-attributes)
CFLAGS-wcstoll.c += $(strtox-CFLAGS)
CFLAGS-wcstoull.c += $(strtox-CFLAGS)
CFLAGS-wcstod.c += $(strtox-CFLAGS) $(config-cflags-wno-ignored-attributes)
CFLAGS-wcstold.c += $(strtox-CFLAGS) $(config-cflags-wno-ignored-attributes)
CFLAGS-wcstof128.c += $(strtox-CFLAGS)
CFLAGS-wcstof.c += $(strtox-CFLAGS) $(config-cflags-wno-ignored-attributes)
CFLAGS-wcstol_l.c += $(strtox-CFLAGS)
CFLAGS-wcstoul_l.c += $(strtox-CFLAGS)
CFLAGS-wcstoll_l.c += $(strtox-CFLAGS)
CFLAGS-wcstoull_l.c += $(strtox-CFLAGS)
CFLAGS-wcstod_l.c += $(strtox-CFLAGS) $(config-cflags-wno-ignored-attributes)
CFLAGS-wcstold_l.c += $(strtox-CFLAGS) $(config-cflags-wno-ignored-attributes)
CFLAGS-wcstof128_l.c += $(strtox-CFLAGS)
CFLAGS-wcstof_l.c += $(strtox-CFLAGS) $(config-cflags-wno-ignored-attributes)
CPPFLAGS-tst-wchar-h.c += -D_FORTIFY_SOURCE=2

CFLAGS-wcschr.c += $(config-cflags-wno-ignored-attributes)
CFLAGS-wmemchr.c += $(config-cflags-wno-ignored-attributes)
CFLAGS-wmemset.c += $(config-cflags-wno-ignored-attributes)
CFLAGS-mbrtowc.c += $(config-cflags-wno-ignored-attributes)
CFLAGS-wcrtomb.c += $(config-cflags-wno-ignored-attributes)
CFLAGS-wcstoll.c += $(config-cflags-wno-ignored-attributes)
CFLAGS-wcstoull.c += $(config-cflags-wno-ignored-attributes)

CFLAGS-isoc99_wscanf.c += -fexceptions
CFLAGS-isoc99_fwscanf.c += -fexceptions
CFLAGS-isoc99_vwscanf.c += -fexceptions
CFLAGS-isoc99_vfwscanf.c += -fexceptions

CPPFLAGS += $(libio-mtsafe)

# We need to find the default version of strtold_l in stdlib.
CPPFLAGS-wcstold_l.c += -I../stdlib

$(objpfx)tst-wcstod-nan-locale: $(libm)
$(objpfx)tst-wcstod-nan-sign: $(libm)

# Some versions of GCC supported for building glibc do not support -std=c2x
# or -std=gnu2x, so the tests for those versions use -std=c11 and -std=gnu11
# and then _ISOC2X_SOURCE is defined in the test as needed.
CFLAGS-tst-wcstol-binary-c11.c += -std=c11
CFLAGS-tst-wcstol-binary-c2x.c += -std=c11
CFLAGS-tst-wcstol-binary-gnu11.c += -std=gnu11
CFLAGS-tst-wcstol-binary-gnu2x.c += -std=gnu11
