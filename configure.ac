# configure.in - Top-level configure.in for Sympa
# RCS Identication ; $Revision: 8595 $ ; $Date: 2013-02-05 15:57:24 +0100 (mar 05 fév 2013) $ 
#
# Sympa - SYsteme de Multi-Postage Automatique
# Copyright (c) 1997, 1998, 1999, 2000, 2001 Comite Reseau des Universites
# Copyright (c) 1997,1998, 1999 Institut Pasteur & Christophe Wolfhugel
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA.

AC_PREREQ(2.60)
AC_INIT(sympa, 6.1.17, sympa-authors@cru.fr)
AM_INIT_AUTOMAKE([foreign -Wall -Werror])
m4_ifdef([AM_SILENT_RULES], [AM_SILENT_RULES([yes])])
AM_PO_SUBDIRS

AC_PREFIX_DEFAULT(/home/sympa)

## first initialises parameters to the standard Sympa filesystem organization
# $prefix variable initialisation seems to be tricky
if test "$prefix" = "NONE"; then
   prefix=$ac_default_prefix
fi

## allow user to select FHS-compliant installation
AC_ARG_ENABLE(
	fhs,
	AS_HELP_STRING(
	[--enable-fhs],
	[use standard FHS files and directories locations and naming (default is no)]
	),
	[fhs=$enableval]
)

if test "$fhs" = "yes"; then
    # only define custom variables
    initdir=$sysconfdir/rc.d/init.d
    piddir=$localstatedir/run/sympa
    lockdir=$localstatedir/lock/subsys
    modulesdir=$datadir/sympa/lib
    scriptdir=$datadir/sympa/bin
    defaultdir=$datadir/sympa/default
    mailtemplatedir=$defaultdir/mail_tt2
    webtemplatedir=$defaultdir/web_tt2
    execcgidir=$libdir/sympa/cgi
    expldir=$localstatedir/lib/sympa/list_data
    staticdir=$localstatedir/lib/sympa/static_content
    spooldir=$localstatedir/spool/sympa
    arcdir=$localstatedir/lib/sympa/arc
    bouncedir=$localstatedir/lib/sympa/bounce
    confdir=$sysconfdir
else
    # redefine default values for some standard variables,
    # but only if no value was given
    if test "$sbindir" = '${exec_prefix}/sbin'; then
       sbindir=$prefix/bin
    fi
    if test "$libexecdir" = '${exec_prefix}/libexec'; then
	libexecdir=$prefix/bin
    fi
    if test "$localstatedir" = '${prefix}/var'; then
	localstatedir=/var
    fi
    if test "$localedir" = '${datarootdir}/locale'; then
	localedir=$prefix/locale
    fi

    # define custom variables
    initdir=/etc/rc.d/init.d
    piddir=$prefix
    lockdir=$localstatedir/lock/subsys
    modulesdir=$prefix/bin
    scriptdir=$prefix/bin
    defaultdir=$prefix/default
    mailtemplatedir=$defaultdir/mail_tt2
    webtemplatedir=$defaultdir/web_tt2
    execcgidir=$prefix/bin
    expldir=$prefix/list_data
    spooldir=$prefix/spool
    staticdir=$prefix/static_content
    arcdir=$prefix/arc
    bouncedir=$prefix/bounce
    confdir=/etc
fi
 
# substitute custom variables
AC_SUBST(initdir)
AC_SUBST(piddir)
AC_SUBST(lockdir)
AC_SUBST(modulesdir)
AC_SUBST(scriptdir)
AC_SUBST(defaultdir)
AC_SUBST(mailtemplatedir)
AC_SUBST(webtemplatedir)
AC_SUBST(execcgidir)
AC_SUBST(expldir)
AC_SUBST(spooldir)
AC_SUBST(staticdir)
AC_SUBST(arcdir)
AC_SUBST(bouncedir)
AC_SUBST(localedir)
AC_SUBST(confdir)
AC_SUBST(docdir)

# allow user to redefine some of them
AC_ARG_WITH(
    confdir,
    AS_HELP_STRING(
	[--with-confdir=DIR],
	[sympa main configuration files (sympa.conf and wwsympa.conf) @<:@SYSCONFDIR@:>@]
    ),
    [
	confdir="$withval"
    ]
)

AC_ARG_WITH(
    etcdir,
    AS_HELP_STRING(
	[--with-etcdir=DIR],
	[obsolete option, use --sysconfdir instead]
    ),
    [
	AC_MSG_WARN([obsolete --with-etcdir option used])
	sysconfdir="$withval"
    ]
)

AC_ARG_WITH(
    bindir,
    AS_HELP_STRING(
	[--with-bindir=DIR],
	[obsolete option, those binaries are now installed in libexecdir]
    ),
    [AC_MSG_WARN([obsolete --with-bindir option used])]
)

AC_ARG_WITH(
    sbindir,
    AS_HELP_STRING(
	[--with-sbindir=DIR],
	[obsolete option, use --sbindir instead]
    ),
    [
	AC_MSG_WARN([obsolete --with-sbindir option used])
	sbindir="$withval"
    ]
)

AC_ARG_WITH(
    libexecdir,
    AS_HELP_STRING(
	[--with-libexecdir=DIR],
	[obsolete option, use --libexecdir instead]
    ),
    [
	AC_MSG_WARN([obsolete --with-libexecdir option used])
	libexecdir="$withval"
    ]
)

AC_ARG_WITH(
    cgidir,
    AS_HELP_STRING(
	[--with-cgidir=DIR],
	[CGI scripts @<:@LIBDIR/sympa/cgi@:>@]
    ),
    [execcgidir="$withval"]
)

AC_ARG_WITH(
    datadir,
    AS_HELP_STRING(
	[--with-datadir=DIR]
	[obsolete option, use --datadir instead]
    ),
    [
	AC_MSG_WARN([obsolete --with-datadir option used])
	datadir="$withval"
    ]
)

AC_ARG_WITH(
    libdir,
    AS_HELP_STRING(
	[--with-libdir=DIR]
	[obsolete option, perl modules are now installed with data]
    ),
    [
	AC_MSG_WARN([obsolete --with-libdir option used])
    ]
)

AC_ARG_WITH(
    localedir,
    AS_HELP_STRING(
	[--with-localedir=DIR],
	[Internationalization catalogues directory @<:@LOCALSTATEDIR/locale@:>@]
    ),
    [
     localedir="$withval"
    ]
)

AC_ARG_WITH(
    mandir,
    AS_HELP_STRING(
	[--with-mandir=DIR],
	[obsolete option, use --mandir instead]
    ),
    [
     AC_MSG_WARN([obsolete --with-mandir option used])
     mandir="$withval"
     ]
)

AC_ARG_WITH(
    docdir,
    AS_HELP_STRING(
	[--with-docdir=DIR],
	[documentations]
    ),
    [
	docdir="$withval"
    ]
)

AC_ARG_WITH(
    sampledir,
    AS_HELP_STRING(
	[--with-sampledir=DIR],
	[obsolete option, samples are now installed with documentation]
    ),
    [
	AC_MSG_WARN([obsolete --with-sampledir option used])
    ]
)

AC_ARG_WITH(
    expldir,
    AS_HELP_STRING(
	[--with-expldir=DIR],
	[list data directory @<:@PREFIX/list_data@:>@]
    ),
    [expldir="$withval"]
)

AC_ARG_WITH(
    spooldir,
    AS_HELP_STRING(
	[--with-spooldir=DIR],
	[application spool directory @<:@PREFIX/spool@:>@]
    ),
    [spooldir="$withval"]
)

AC_ARG_WITH(
    initdir,
    AS_HELP_STRING(
	[--with-initdir=DIR],
	[install System V init script @<:@SYSCONFDIR/rc.d/init.d@:>@]
    ),
    [initdir="$withval"]
)

AC_ARG_WITH(
    lockdir,
    AS_HELP_STRING(
	[--with-lockdir=DIR],
	[lock files @<:@LOCALSTATEDIR/lock/subsys@:>@]
    ),
    [lockdir="$withval"]
)

AC_ARG_WITH(
    piddir,
    AS_HELP_STRING(
	[--with-piddir=DIR],
	[.pid files @<:@LOCALSTATEDIR/run@:>@]
    ),
    [piddir="$withval"]
)

AC_ARG_WITH(
    modulesdir,
    AS_HELP_STRING(
	[--with-modulesdir=DIR],
	[Perl modules file installed with Sympa @<:@PREFIX/bin@:>@]
    ),
    [modulesdir="$withval"]
)

AC_ARG_WITH(
    defaultdir,
    AS_HELP_STRING(
	[--with-defaultdir=DIR],
	[default configuration files (scenarios and templates also) @<:@PREFIX/default@:>@]
    ),
    [defaultdir="$withval"]
)

AC_ARG_WITH(
    scriptdir,
    AS_HELP_STRING(
	[--with-scriptdir=DIR],
	[application scripts @<:@PREFIX/bin@:>@]
    ),
    [scriptdir="$withval"]
)

AC_ARG_WITH(
    staticdir,
    AS_HELP_STRING(
	[--with-staticdir=DIR],
	[static data @<:@PREFIX/static_content@:>@]
    ),
    [staticdir="$withval"]
)

CONFIG=$confdir/sympa.conf
AC_SUBST(CONFIG)
WWSCONFIG=$confdir/wwsympa.conf
AC_SUBST(WWSCONFIG)

AC_PROG_CC
# needed for using per-target flags
AM_PROG_CC_C_O
AC_PATH_PROGS([SED], [sed gsed])
#AC_PROG_SED
AC_PROG_LN_S

AC_ARG_WITH(
    [perl],
    AS_HELP_STRING(
	[--with-perl=FULLPATH],
        [set full path to Perl interpreter]
    ),
    [PERL="$withval"]
)
if test -n "$PERL"; then
    # user-supplied value
    AC_MSG_CHECKING([user-supplied perl interpreter])
    if test -f "$PERL"; then
	:
    else
	AC_MSG_RESULT([non-existing])
	AC_MSG_ERROR([invalid value $PERL for perl interpreter])
    fi
    if test -x "$PERL"; then
	:
    else
	AC_MSG_RESULT([non-executable])
	AC_MSG_ERROR([invalid value $PERL for perl interpreter])
    fi
    AC_MSG_RESULT([$PERL])
else
    # check in PATH
    AC_PATH_PROG(PERL, perl)
    if test -z "$PERL"; then
	AC_MSG_ERROR([perl required])
    fi
fi

AC_PATH_PROG(POD2MAN, pod2man)
if test -z "$POD2MAN"; then
    AC_MSG_ERROR([pod2man required])
fi

USER=sympa
AC_ARG_WITH(
    [user],
    AS_HELP_STRING(
	[--with-user=LOGIN],
	[set sympa user name @<:@sympa@:>@]
    ),
    [USER="$withval"]
)
AC_SUBST(USER)

GROUP=sympa
AC_ARG_WITH(
    [group],
    AS_HELP_STRING(
	[--with-group=LOGIN],
	[set sympa group name @<:@sympa@:>@]
    ),
    [GROUP="$withval"]
)
AC_SUBST(GROUP)

SENDMAIL_ALIASES=/etc/mail/sympa_aliases
AC_ARG_WITH(
    [sendmail_aliases],
    AS_HELP_STRING(
	[--with-sendmail_aliases=ALIASFILE],
	[aliases file to store Sympa mail aliases @<:@/etc/mail/sympa_aliases@:>@]
    ),
    [SENDMAIL_ALIASES="$withval"]
)
AC_SUBST(SENDMAIL_ALIASES)

## The postfix virtual file we use. Better use a seperate one for sympa.
## Of course an extra alias file must be generated with proper permissions
## (owner sympa, write access for sympa, no write access for anyone else)
## and declared in main.cf!
VIRTUAL_ALIASES=/etc/mail/sympa_virtual
AC_ARG_WITH(
    [virtual_aliases],
    AS_HELP_STRING(
	[--with-virtual_aliases=ALIASFILE],
	[postfix virtual file to be used by Sympa @<:@/etc/mail/sympa_virtual@:>@]
    ),
    [VIRTUAL_ALIASES="$withval"]
)
AC_SUBST(VIRTUAL_ALIASES)

AC_ARG_WITH(
    [newaliases],
    AS_HELP_STRING(
	[--with-newaliases=FULLPATH],
	[path to newaliases command @<:@/usr/bin/newaliases@:>@]
    ),
    [NEWALIASES="$withval"]
)
if test -n "$NEWALIASES"; then
    # user-supplied value
    AC_MSG_CHECKING([user-supplied newaliases command])
    if test -f "$NEWALIASES"; then
	:
    else
	AC_MSG_RESULT([non-existing])
	AC_MSG_ERROR([invalid value $NEWALIASES for newaliases command])
    fi
    if test -x "$NEWALIASES"; then
	:
    else
	AC_MSG_RESULT([non-executable])
	AC_MSG_ERROR([invalid value $NEWALIASES for newaliases command])
    fi
    AC_MSG_RESULT([$NEWALIASES])
else
    # default value
    NEWALIASES=/usr/bin/newaliases
fi
AC_SUBST(NEWALIASES)

NEWALIASES_ARG=
AC_ARG_WITH(
    [newaliases_arg],
    AS_HELP_STRING(
	[--with-newaliases_arg=ARGS],
	[arguments to newaliases command @<:@NONE@:>@]
    ),
    [NEWALIASES_ARG="$withval"]
)
AC_SUBST(NEWALIASES_ARG)

AC_ARG_WITH(
    [postmap],
    AS_HELP_STRING(
	[--with-postmap=FULLPATH],
	[path to postfix postmap command @<:@/usr/sbin/postmap@:>@]
    ),
    [POSTMAP="$withval"]
)
if test -n "$POSTMAP"; then
    # user-supplied value
    AC_MSG_CHECKING([user-supplied postmap command])
    if test -f "$POSTMAP"; then
	:
    else
	AC_MSG_RESULT([non-existing])
	AC_MSG_ERROR([invalid value $POSTMAP for postmap command])
    fi
    if test -x "$POSTMAP"; then
	:
    else
	AC_MSG_RESULT([non-executable])
	AC_MSG_ERROR([invalid value $POSTMAP for postmap command])
    fi
    AC_MSG_RESULT([$POSTMAP])
else
    # default value
    POSTMAP=/usr/sbin/postmap
fi
AC_SUBST(POSTMAP)

POSTMAP_ARG=${VIRTUAL_ALIASES}
AC_ARG_WITH(
    [postmap_arg],
    AS_HELP_STRING(
	[--with-postmap_arg=ARGS],
	[set arguments to postfix postmap command @<:@VIRTUAL_ALIASES@:>@]
    ),
    [POSTMAP_ARG="$withval"]
)
AC_SUBST(POSTMAP_ARG)

AC_CONFIG_FILES([
    Makefile
    src/Makefile
    src/etc/Makefile
    src/etc/script/Makefile
    src/lib/Makefile
    soap/Makefile
    doc/Makefile
    doc/man8/Makefile
    doc/sample/Makefile
    web_tt2/Makefile
    wwsympa/Makefile
    wwsympa/icons/Makefile
    mail_tt2/Makefile
    po/Makefile.in
    po-wwsympa/Makefile.in
    sympa.spec
])
AC_OUTPUT
