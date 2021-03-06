# Copyright (C) 1999-2009  Lorenzo Bettini <http://www.lorenzobettini.it>
#  
# This file is free software; as a special exception the author gives
# unlimited permission to copy and/or distribute it, with or without 
# modifications, as long as this notice is preserved.
# 
# This program is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY, to the extent permitted by law; without even the
# implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

STD_STYLE = --style-file $(top_srcdir)/src/default.style
DATADIR_OPTION = --data-dir $(top_srcdir)/src/

SRCHILITEEXE = $(top_builddir)/src/$(PACKAGE)$(EXEEXT)
SRCHILITEPROG = $(SRCHILITEEXE) $(DATADIR_OPTION)
SRCHILITETEXINFO = $(SRCHILITEPROG) -f texinfo --output-dir=$(top_builddir)/doc/ --style-file=$(top_srcdir)/src/texinfo.style

JAVA2HTML_PROG = $(SRCHILITEPROG) -s java -f html 

PROGNAME = $(JAVA2HTML_PROG) $(STD_STYLE) 

CPP2HTML = $(SRCHILITEPROG) -s cpp -f html $(STD_STYLE)

CPP2HTML_WREFS = $(CPP2HTML) --title="Contains references to tags" --gen-references=inline --ctags="ctags --excmd=n --tag-relative=yes -o my_test_ref.tags"

CHANGELOG2HTML = $(SRCHILITEPROG) -s changelog -f html $(STD_STYLE)

FLEX2HTML = $(SRCHILITEPROG) -s flex -f html $(STD_STYLE)

OUTPUT_HERE = --output-dir=$(top_builddir)/doc

info_TEXINFOS = source-highlight.texinfo source-highlight-lib.texinfo
source_highlight_TEXINFOS = $(GENERATEDINFOS) $(DISTRIBUTEDINFOS)
source_highlight_lib_TEXINFOS = $(EXAMPLEINFOS)

SUFFIXES = .txt .txt.texinfo .txt.texinfo.texinfo .lang .lang.texinfo .diff .diff.texinfo .css .css.texinfo .show.texinfo .defaults .defaults.texinfo .cpp .cpp.texinfo

#source-highlight.texinfo: $(GENERATEDINFOS) $(DISTRIBUTEDINFOS)

lang-list.texinfo: $(top_srcdir)/src/lang.map
	$(SRCHILITEEXE) --data-dir=$(top_srcdir)/src/ --lang-list | sed -e 's/@/@@/' > $@

outlang-list.texinfo: $(top_srcdir)/src/outlang.map
	$(SRCHILITEEXE) --data-dir=$(top_srcdir)/src/ --outlang-list | sed -e 's/@/@@/' > $@

test.java.texinfo: $(top_srcdir)/tests/test.java
	$(SRCHILITEEXE) --data-dir=$(top_srcdir)/src/ -f texinfo -i $(top_srcdir)/tests/test.java --style-file=$(top_srcdir)/src/texinfo.style -n > $@

test_lineranges1.java.texinfo: $(top_srcdir)/tests/test.java
	$(SRCHILITEEXE) --data-dir=$(top_srcdir)/src/ -f texinfo -i $(top_srcdir)/tests/test.java --style-file=$(top_srcdir)/src/texinfo.style --line-range="12-18","29-34" -n > $@

test_lineranges2.java.texinfo: $(top_srcdir)/tests/test.java
	$(SRCHILITEEXE) --data-dir=$(top_srcdir)/src/ -f texinfo -i $(top_srcdir)/tests/test.java --style-file=$(top_srcdir)/src/texinfo.style --line-range="12-18","29-34" -n --range-context=2 --range-separator="{... not in range ...}" > $@

test_regexrange1.java.texinfo: $(top_srcdir)/tests/test.java
	$(SRCHILITEEXE) --data-dir=$(top_srcdir)/src/ -f texinfo -i $(top_srcdir)/tests/test.java --style-file=$(top_srcdir)/src/texinfo.style --regex-range="/// [[:alpha:]]+" -n > $@

test_regexrange_main.java.texinfo: $(top_srcdir)/tests/test.java
	$(SRCHILITEEXE) --data-dir=$(top_srcdir)/src/ -f texinfo -i $(top_srcdir)/tests/test.java --style-file=$(top_srcdir)/src/texinfo.style --regex-range="/\* main \*/" -n > $@

test_regexrange_methods.java.texinfo: $(top_srcdir)/tests/test.java
	$(SRCHILITEEXE) --data-dir=$(top_srcdir)/src/ -f texinfo -i $(top_srcdir)/tests/test.java --style-file=$(top_srcdir)/src/texinfo.style --regex-range="/\* [[:alpha:]]+ \*/" -n > $@

test_vardecl.cc.texinfo: $(top_srcdir)/tests/test_vardecl.cc
	$(SRCHILITEEXE) --data-dir=$(top_srcdir)/src/ -f texinfo -i $(top_srcdir)/tests/test_vardecl.cc --style-file=$(srcdir)/highlight_type.style > $@

debug.java.texinfo: $(top_srcdir)/tests/debug.java
	$(SRCHILITEEXE) --data-dir=$(top_srcdir)/src/ -f texinfo -i $(top_srcdir)/tests/debug.java --style-file=$(top_srcdir)/src/texinfo.style -n > $@

cpp.langelems.texinfo: $(top_srcdir)/src/cpp.lang $(top_srcdir)/src/c.lang
	$(SRCHILITEEXE) --data-dir=$(top_srcdir)/src/ --show-lang-elements=$(top_srcdir)/src/cpp.lang > $@

log.langelems.texinfo: $(top_srcdir)/src/log.lang
	$(SRCHILITEEXE) --data-dir=$(top_srcdir)/src/ --show-lang-elements=$(top_srcdir)/src/log.lang > $@

.txt.txt.texinfo:
	$(SRCHILITEEXE) --data-dir=$(top_srcdir)/src/ -f texinfo -i $< --style-file=$(top_srcdir)/src/texinfo.style -o $@

style.defaults.texinfo: $(top_srcdir)/src/style.defaults
	$(SRCHILITEEXE) --data-dir=$(top_srcdir)/src/ -f texinfo -i $(top_srcdir)/src/style.defaults --style-file=$(top_srcdir)/src/texinfo.style -o $@ --lang-def=nohilite.lang

.txt.texinfo.txt.texinfo.texinfo: 
	$(SRCHILITEEXE) --data-dir=$(top_srcdir)/src/ -f texinfo -i $< --style-file=$(top_srcdir)/src/texinfo.style -o $@ --lang-def=nohilite.lang

html_common.outlang.texinfo: $(top_srcdir)/src/html_common.outlang
	$(SRCHILITEEXE) --data-dir=$(top_srcdir)/src/ -f texinfo -i $(top_srcdir)/src/html_common.outlang --style-file=$(top_srcdir)/src/texinfo.style -o $@

javadoc.outlang.texinfo: $(top_srcdir)/src/javadoc.outlang
	$(SRCHILITEEXE) --data-dir=$(top_srcdir)/src/ -f texinfo -i $(top_srcdir)/src/javadoc.outlang --style-file=$(top_srcdir)/src/texinfo.style -o $@

LANG2TEXINFO = $(SRCHILITEEXE) --data-dir=$(top_srcdir)/src/ -f texinfo --style-file=$(top_srcdir)/src/texinfo.style -o $@

test_newlines.lang.texinfo: $(top_srcdir)/tests/test_newlines.lang
	$(LANG2TEXINFO) -i $(top_srcdir)/tests/test_newlines.lang

test_nonewlines.lang.texinfo: $(top_srcdir)/tests/test_nonewlines.lang
	$(LANG2TEXINFO) -i $(top_srcdir)/tests/test_nonewlines.lang

test_string_stop.lang.texinfo: $(top_srcdir)/tests/test_string_stop.lang
	$(LANG2TEXINFO) -i $(top_srcdir)/tests/test_string_stop.lang

langdef.lang.texinfo: $(top_srcdir)/src/langdef.lang
	$(LANG2TEXINFO) -i $(top_srcdir)/src/langdef.lang

style.lang.texinfo: $(top_srcdir)/src/style.lang
	$(LANG2TEXINFO) -i $(top_srcdir)/src/style.lang

cpp.lang.texinfo: $(top_srcdir)/src/cpp.lang
	$(LANG2TEXINFO) -i $(top_srcdir)/src/cpp.lang

c.lang.texinfo: $(top_srcdir)/src/c.lang
	$(LANG2TEXINFO) -i $(top_srcdir)/src/c.lang

csharp.lang.texinfo: $(top_srcdir)/src/csharp.lang
	$(LANG2TEXINFO) -i $(top_srcdir)/src/csharp.lang

c_comment.lang.texinfo: $(top_srcdir)/src/c_comment.lang
	$(LANG2TEXINFO) -i $(top_srcdir)/src/c_comment.lang

clike_vardeclaration.lang.texinfo: $(top_srcdir)/src/clike_vardeclaration.lang
	$(LANG2TEXINFO) -i $(top_srcdir)/src/clike_vardeclaration.lang

c_string.lang.texinfo: $(top_srcdir)/src/c_string.lang
	$(LANG2TEXINFO) -i $(top_srcdir)/src/c_string.lang

symbols.lang.texinfo: $(top_srcdir)/src/symbols.lang
	$(LANG2TEXINFO) -i $(top_srcdir)/src/symbols.lang

function.lang.texinfo: $(top_srcdir)/src/function.lang
	$(LANG2TEXINFO) -i $(top_srcdir)/src/function.lang

diff.lang.texinfo: $(top_srcdir)/src/diff.lang
	$(LANG2TEXINFO) -i $(top_srcdir)/src/diff.lang

extreme_comment.lang.texinfo: $(top_srcdir)/src/extreme_comment.lang
	$(LANG2TEXINFO) -i $(top_srcdir)/src/extreme_comment.lang

extreme_comment2.lang.texinfo: $(top_srcdir)/src/extreme_comment2.lang
	$(LANG2TEXINFO) -i $(top_srcdir)/src/extreme_comment2.lang

extreme_comment3.lang.texinfo: $(top_srcdir)/src/extreme_comment3.lang
	$(LANG2TEXINFO) -i $(top_srcdir)/src/extreme_comment3.lang

extreme_comment4.lang.texinfo: $(top_srcdir)/src/extreme_comment4.lang
	$(LANG2TEXINFO) -i $(top_srcdir)/src/extreme_comment4.lang

.lang.lang.texinfo:
	$(SRCHILITEEXE) --data-dir=$(top_srcdir)/src/ -f texinfo -i $< --style-file=$(top_srcdir)/src/texinfo.style -o $@

default.style.texinfo: $(top_srcdir)/src/default.style
	$(SRCHILITEEXE) --data-dir=$(top_srcdir)/src/ -f texinfo -i $(top_srcdir)/src/default.style --style-file=$(top_srcdir)/src/texinfo.style -o $@

texinfo.style.texinfo: $(top_srcdir)/src/texinfo.style
	$(SRCHILITEEXE) --data-dir=$(top_srcdir)/src/ -f texinfo -i $(top_srcdir)/src/texinfo.style --style-file=$(top_srcdir)/src/texinfo.style -o $@

syslog.style.texinfo: $(top_srcdir)/tests/syslog.style
	$(SRCHILITEEXE) --data-dir=$(top_srcdir)/src/ -f texinfo -i $(top_srcdir)/tests/syslog.style --style-file=$(top_srcdir)/src/texinfo.style -o $@

.diff.diff.texinfo:
	$(SRCHILITEEXE) --data-dir=$(top_srcdir)/src/ -f texinfo -i $< --style-file=$(top_srcdir)/src/texinfo.style -o $@

.cpp.cpp.texinfo:
	$(SRCHILITEEXE) --data-dir=$(top_srcdir)/src/ -f texinfo -i $< --style-file=$(top_srcdir)/src/texinfo.style -o $@

.css.css.texinfo:
	$(SRCHILITEEXE) --data-dir=$(top_srcdir)/src/ -f texinfo -i $< --style-file=$(top_srcdir)/src/texinfo.style -o $@

default.css.texinfo: $(top_srcdir)/src/default.css
	$(SRCHILITEEXE) --data-dir=$(top_srcdir)/src/ -f texinfo -i $(top_srcdir)/src/default.css --style-file=$(top_srcdir)/src/texinfo.style -o $@

test_extreme_comment.cpp.texinfo: $(top_srcdir)/tests/test_extreme_comment.cpp
	$(SRCHILITEEXE) --data-dir=$(top_srcdir)/src/ -f texinfo -i $(top_srcdir)/tests/test_extreme_comment.cpp --style-file=$(top_srcdir)/src/texinfo.style -o $@

test_extreme_comment_wrong.texinfo: $(top_srcdir)/tests/test_extreme_comment.cpp
	$(SRCHILITEEXE) --data-dir=$(top_srcdir)/src/ -f texinfo -i $(top_srcdir)/tests/test_extreme_comment.cpp --style-file=$(top_srcdir)/src/texinfo.style -o $@ --lang-def=extreme_comment.lang

test_extreme_comment_1.texinfo: $(top_srcdir)/tests/test_extreme_comment.cpp
	$(SRCHILITEEXE) --data-dir=$(top_srcdir)/src/ -f texinfo -i $(top_srcdir)/tests/test_extreme_comment.cpp --style-file=$(top_srcdir)/src/texinfo.style -o $@ --lang-def=extreme_comment2.lang

test_extreme_comment_wrong2.texinfo: $(top_srcdir)/tests/test_extreme_comment2.cpp
	$(SRCHILITEEXE) --data-dir=$(top_srcdir)/src/ -f texinfo -i $(top_srcdir)/tests/test_extreme_comment2.cpp --style-file=$(top_srcdir)/src/texinfo.style -o $@ --lang-def=extreme_comment2.lang

test_extreme_comment_2.texinfo: $(top_srcdir)/tests/test_extreme_comment2.cpp
	$(SRCHILITEEXE) --data-dir=$(top_srcdir)/src/ -f texinfo -i $(top_srcdir)/tests/test_extreme_comment2.cpp --style-file=$(top_srcdir)/src/texinfo.style -o $@ --lang-def=extreme_comment3.lang

test_extreme_comment_3.texinfo: $(top_srcdir)/tests/test_extreme_comment3.cpp
	$(SRCHILITEEXE) --data-dir=$(top_srcdir)/src/ -f texinfo -i $(top_srcdir)/tests/test_extreme_comment3.cpp --style-file=$(top_srcdir)/src/texinfo.style -o $@ --lang-def=extreme_comment3.lang

source-highlight-console-main.cpp.texinfo: $(top_srcdir)/lib/examples/source-highlight-console-main.cpp
	$(SRCHILITETEXINFO) $(top_srcdir)/lib/examples/source-highlight-console-main.cpp --regex-range="//> TEXINFO"

debuglistener.cpp.texinfo: $(top_srcdir)/lib/srchilite/debuglistener.cpp
	$(SRCHILITETEXINFO) $(top_srcdir)/lib/srchilite/debuglistener.cpp --regex-range="//> TEXINFO"

infoformatter.h.texinfo: $(top_srcdir)/lib/examples/infoformatter.h
	$(SRCHILITETEXINFO) $(top_srcdir)/lib/examples/infoformatter.h --regex-range="//> TEXINFO"

styleformatter.h.texinfo: $(top_srcdir)/lib/examples/infoformatter.h
	$(SRCHILITETEXINFO) $(top_srcdir)/lib/examples/infoformatter.h --regex-range="//> TEXINFO"

infoformatter-main.cpp.texinfo: $(top_srcdir)/lib/examples/infoformatter-main.cpp
	$(SRCHILITETEXINFO) $(top_srcdir)/lib/examples/infoformatter-main.cpp --regex-range="//> TEXINFO"

styleformatter-main.cpp.texinfo: $(top_srcdir)/lib/examples/styleformatter-main.cpp
	$(SRCHILITETEXINFO) $(top_srcdir)/lib/examples/styleformatter-main.cpp --regex-range="//> TEXINFO"

styleformatter.h.texinfo: $(top_srcdir)/lib/examples/styleformatter.h
	$(SRCHILITETEXINFO) $(top_srcdir)/lib/examples/styleformatter.h --regex-range="//> TEXINFO"

styleformatterfactory.h.texinfo: $(top_srcdir)/lib/examples/styleformatterfactory.h
	$(SRCHILITETEXINFO) $(top_srcdir)/lib/examples/styleformatterfactory.h --regex-range="//> TEXINFO"

.lang.show.texinfo:
	$(SRCHILITEEXE) --show-regex=$< | $(SRCHILITEPROG) -f texinfo --style-file=$(top_srcdir)/src/texinfo.style --lang-def=nohilite.lang > $@
#	$(SRCHILITEEXE) --show-regex=$< > $@
#	sed -itesttmp -e 's/@/@@/g' $@ && rm -f *testtmp

# the following rules have to do only with maintainance of the package
if MAINTAINER_MODE

# help-output.texinfo: $(top_srcdir)/src/lib/cmdline.ggo
#	$(SRCHILITEEXE) --help | sed -e 's/@/@@/' > $@

if NO_GENGETOPT
$(top_srcdir)/doc/help-output.texinfo: $(top_srcdir)/src/cmdline.ggo
	touch $@
else
$(top_srcdir)/doc/help-output.texinfo: $(top_srcdir)/src/cmdline.ggo
	$(GENGETOPT) --show-detailed-help -i $(top_srcdir)/src/cmdline.ggo --set-package="source-highlight" --set-version="" > $@
endif

$(top_srcdir)/doc/test_ref.h.texinfo: $(top_srcdir)/tests/test.h
	$(SRCHILITEEXE) --data-dir=$(top_srcdir)/src/ -f texinfo -i $(top_srcdir)/tests/test.h --style-file=$(top_srcdir)/src/texinfo.style -n --gen-references=postline > $@

# the dependence on config.h is to ensure the correct version number
# in the generated man file
if NO_HELP2MAN
source-highlight.1: $(top_srcdir)/src/cmdline.ggo $(top_builddir)/config.h
	touch $@
else
source-highlight.1: $(top_srcdir)/src/cmdline.ggo $(top_builddir)/config.h
	$(HELP2MAN) -n "convert source code to syntax highlighted document" $(SRCHILITEEXE) > $@
endif

# end of maintainer mode
endif

AM_MAKEINFOHTMLFLAGS=--no-split
# for including generated texinfo files
AM_MAKEINFOFLAGS=-I$(srcdir)

# these are distributed since they might depend on other programs
DISTRIBUTEDINFOS = help-output.texinfo test_ref.h.texinfo 

GENERATEDINFOS = lang-list.texinfo outlang-list.texinfo test.java.texinfo test_lineranges1.java.texinfo test_lineranges2.java.texinfo test_regexrange1.java.texinfo test_regexrange_main.java.texinfo test_regexrange_methods.java.texinfo debug.java.texinfo default.style.texinfo texinfo.style.texinfo syslog.style.texinfo langdef.lang.texinfo style.lang.texinfo cpp.lang.texinfo c.lang.texinfo csharp.lang.texinfo c_comment.lang.texinfo clike_vardeclaration.lang.texinfo c_string.lang.texinfo symbols.lang.texinfo function.lang.texinfo example-u.diff.texinfo example-c.diff.texinfo example-n.diff.texinfo diff.lang.texinfo test_extreme_comment.cpp.texinfo extreme_comment.lang.texinfo test_extreme_comment_wrong.texinfo extreme_comment2.lang.texinfo test_extreme_comment_1.texinfo test_extreme_comment_wrong2.texinfo extreme_comment3.lang.texinfo test_extreme_comment_2.texinfo test_extreme_comment_3.texinfo comment-show.show.texinfo comment-show2.show.texinfo comment-show.lang.texinfo comment-show2.lang.texinfo html_common.outlang.texinfo javadoc.outlang.texinfo cpp.langelems.texinfo log.langelems.texinfo txt2texinfo.txt.texinfo txt2texinfo.txt.texinfo.texinfo css_example.css.texinfo default.css.texinfo style.defaults.texinfo test_string_stop.lang.texinfo strategy_example.lang.texinfo test_vardecl.cc.texinfo test_nonewlines.lang.texinfo test_newlines.lang.texinfo

EXAMPLEINFOS = source-highlight-console-main.cpp.texinfo infoformatter.h.texinfo infoformatter-main.cpp.texinfo debuglistener.cpp.texinfo styleformatter.h.texinfo styleformatterfactory.h.texinfo styleformatter-main.cpp.texinfo instances_example.cpp.texinfo

CSS_FILES = default.css \
Hello.css Hello2.css mono-alt.css mono.css cpp2html.css \
            xhtml.css \
sh_acid.css           sh_golden.css           sh_night.css \
sh_berries-dark.css   sh_greenlcd.css         sh_pablo.css \
sh_berries-light.css  sh_ide-anjuta.css       sh_peachpuff.css \
sh_bipolar.css        sh_ide-codewarrior.css  sh_print.css \
sh_blacknblue.css     sh_ide-devcpp.css       sh_rand01.css \
sh_bright.css         sh_ide-eclipse.css      sh_the.css \
sh_contrast.css       sh_ide-kdev.css         sh_typical.css \
sh_darkblue.css       sh_ide-msvcpp.css       sh_vampire.css \
sh_darkness.css       sh_kwrite.css           sh_vim-dark.css \
sh_desert.css         sh_matlab.css           sh_vim.css \
sh_dull.css           sh_navy.css             sh_whatis.css \
sh_easter.css         sh_nedit.css            sh_whitengrey.css \
sh_emacs.css          sh_neon.css             sh_zellner.css

EXTRA_DIST = colors.html source-highlight.html source-highlight-lib.html \
             Hello.java \
             header.html footer.html \
             gpl.texinfo flex_scanner.ll \
             example-u.diff example-c.diff example-n.diff \
             source-highlight.1 source-highlight-settings.1 check-regexp.1 index.html examples.html \
	     comment-show.lang comment-show2.lang \
	     SimpleClass.java SimpleClass-doc.html UsageExample.java \
	     txt2texinfo.txt \
             $(DISTRIBUTEDINFOS) $(CSS_FILES) \
style_examples_footer.html style_examples_header.html \
css_example.css \
strategy_example.lang \
highlight_type.style \
instances_example.cpp

source_highlightdoc_DATA = colors.html source-highlight.html \
    Hello.java Hello1.html Hello2.html Hello3.html Hello4.html Hello5.html \
    Hello.java.html Hello_h_f.html Hello_lines.html Hello_xhtml.html \
    Hello_xhtml2.html Hello_notfixed.html \
    $(CSS_FILES) \
    source-highlight.cc.html \
    cmdline.h.html \
    flex_scanner.ll.html \
    header.html footer.html \
    langdef.lang.html \
    index.html examples.html \
    SimpleClass.java SimpleClass.html SimpleClass-doc.html \
    UsageExample.java UsageExample.html \
    style_examples.html

source_highlightdata_DATA = $(CSS_FILES)

# man page
man_MANS = source-highlight.1 source-highlight-settings.1 check-regexp.1

# note that $(srcdir) actually points to doc dir

langdef.lang.html: $(top_srcdir)/src/langdef.lang
	$(SRCHILITEPROG) $(STD_STYLE) -i $(top_srcdir)/src/langdef.lang -o langdef.lang.html

source-highlight.cc.html: $(top_srcdir)/src/source-highlight.cc
	$(CPP2HTML) --doc $(OUTPUT_HERE) $(top_srcdir)/src/source-highlight.cc

#ChangeLog.html: $(top_srcdir)/ChangeLog
#	$(CHANGELOG2HTML) --doc $(OUTPUT_HERE) $(top_srcdir)/ChangeLog

flex_scanner.ll.html: $(srcdir)/flex_scanner.ll
	$(FLEX2HTML) --doc $(OUTPUT_HERE) $(srcdir)/flex_scanner.ll

# cmdline.c.html: $(top_srcdir)/src/lib/cmdline.c
#	$(CPP2HTML) --doc $(OUTPUT_HERE) --css="$(srcdir)/cpp2html.css" --header="$(srcdir)/header.html" --footer="$(srcdir)/footer.html" $(top_srcdir)/src/lib/cmdline.c

cmdline.h.html: $(top_srcdir)/src/cmdline.h
	$(CPP2HTML) --doc $(OUTPUT_HERE) --css="$(srcdir)/mono.css" $(top_srcdir)/src/cmdline.h

BUILD_HELLO1 = $(PROGNAME) -i $(srcdir)/Hello.java -o Hello1.html
BUILD_HELLO2 = $(PROGNAME) --input $(srcdir)/Hello.java --output Hello2.html --doc
BUILD_HELLO3 = $(PROGNAME) -i $(srcdir)/Hello.java -o Hello3.html --title "Happy Java with java2html :-)" --tab 3
BUILD_HELLO4 = $(PROGNAME) < $(srcdir)/Hello.java > Hello4.html --title "and what about CSS :-)" --css "Hello.css"
BUILD_HELLO5 = $(PROGNAME) < $(srcdir)/Hello.java > Hello5.html --title "Wooo... this is quite dark ;-D" --css "mono-alt.css"
BUILD_HELLO_HTML = $(PROGNAME) --doc $(OUTPUT_HERE) $(srcdir)/Hello.java
BUILD_HELLO_W_HEADER_FOOTER = $(JAVA2HTML_PROG) --css="cpp2html.css" --doc -i $(srcdir)/Hello.java -o Hello_h_f.html --header="$(srcdir)/header.html" --footer="$(srcdir)/footer.html"
BUILD_HELLO_LINES = $(PROGNAME) --line-number --doc -i $(srcdir)/Hello.java -o Hello_lines.html
BUILD_HELLO_XHTML = $(SRCHILITEPROG) -s java -f xhtml --doc -i $(srcdir)/Hello.java -o Hello_xhtml.html --css $(srcdir)/xhtml.css
BUILD_HELLO_XHTML2 = $(SRCHILITEPROG) -s java -f xhtml --doc -i $(srcdir)/Hello.java -o Hello_xhtml2.html $(STD_STYLE)
BUILD_HELLO_HTMLNOTFIXED = $(SRCHILITEPROG) -s java --outlang-def=$(srcdir)/../src/html_notfixed.outlang -i $(srcdir)/Hello.java -o Hello_notfixed.html

#BUILD_REFS = $(CPP2HTML_WREFS) --ctags-file=my_test_ref.tags --line-number $(srcdir)/test_refs.h $(srcdir)/test_refs.cpp 

SimpleClass.html: $(srcdir)/SimpleClass.java
	$(PROGNAME) --input $(srcdir)/SimpleClass.java --output SimpleClass.html --doc

UsageExample.html: $(srcdir)/UsageExample.java
	$(PROGNAME) --input $(srcdir)/UsageExample.java --output UsageExample.html --doc

Hello1.html: $(srcdir)/Hello.java
	$(BUILD_HELLO1)

Hello2.html: $(srcdir)/Hello.java
	$(BUILD_HELLO2)

Hello3.html: $(srcdir)/Hello.java
	$(BUILD_HELLO3)

Hello4.html: $(srcdir)/Hello.java
	$(BUILD_HELLO4)

Hello5.html: $(srcdir)/Hello.java
	$(BUILD_HELLO5)

Hello.java.html: $(srcdir)/Hello.java
	$(BUILD_HELLO_HTML)

Hello_h_f.html: $(srcdir)/Hello.java header.html footer.html
	$(BUILD_HELLO_W_HEADER_FOOTER)

Hello_lines.html: $(srcdir)/Hello.java
	$(BUILD_HELLO_LINES)

Hello_xhtml.html: $(srcdir)/Hello.java
	$(BUILD_HELLO_XHTML)

Hello_xhtml2.html: $(srcdir)/Hello.java
	$(BUILD_HELLO_XHTML2)

Hello_notfixed.html: $(srcdir)/Hello.java
	$(BUILD_HELLO_HTMLNOTFIXED)

style_examples.html: $(srcdir)/Hello.java
	cat $(srcdir)/style_examples_header.html > style_examples.html
#./gen_style_example.sh default.css >> style_examples.html
	for style in $(CSS_FILES); do \
	  ./gen_style_example.sh $$style >> style_examples.html ; \
	done ; \
	cat $(srcdir)/style_examples_footer.html >> style_examples.html

check:
	$(BUILD_HELLO1)
	$(BUILD_HELLO2)
	$(BUILD_HELLO3)
	$(BUILD_HELLO4)
	$(BUILD_HELLO5)
	$(BUILD_HELLO_HTML)
	$(BUILD_HELLO_W_HEADER_FOOTER)
	$(BUILD_HELLO_LINES)
	$(BUILD_HELLO_XHTML)
	$(BUILD_HELLO_XHTML2)
	$(BUILD_HELLO_HTMLNOTFIXED)

HTML_GENERATED_FILES = Hello1.html Hello2.html Hello3.html Hello4.html \
Hello5.html Hello.java.html Hello_h_f.html source-highlight.cc.html \
cmdline.h.html Hello_lines.html Hello_xhtml.html Hello_xhtml2.html \
flex_scanner.ll.html SimpleClass.html \
UsageExample.html Hello_notfixed.html \
style_examples.html

html-clean:
	rm -f $(HTML_GENERATED_FILES)

texinfo-clean:
	rm -f $(GENERATEDINFOS) $(EXAMPLEINFOS)

DISTCLEANFILES = $(HTML_GENERATED_FILES) langdef.lang.html

MAINTAINERCLEANFILES = $(GENERATEDINFOS) tags 