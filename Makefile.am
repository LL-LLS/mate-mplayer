## Process this file with automake to produce Makefile.in
## Created by Anjuta

SUBDIRS = src po icons

mate_mplayerdocdir = ${docdir}
mate_mplayerdoc_DATA = \
	README\
	COPYING\
	AUTHORS\
	ChangeLog\
	INSTALL\
	NEWS \
	DOCS/keyboard_shortcuts.txt \
	DOCS/tech/dbus.txt \
	DOCS/tech/plugin-interaction.txt

desktopdir = ${prefix}/share/applications
desktop_DATA = mate-mplayer.desktop

prefappdir = ${prefix}/share/mate-control-center/default-apps
prefapp_DATA = mate-mplayer.xml


manpagedir = @mandir@/man1
manpage_DATA = mate-mplayer.1

EXTRA_DIST = \
	autogen.sh \
	$(mate_mplayerdoc_DATA) \
	$(desktop_DATA) \
	$(manpage_DATA) \
	$(prefapp_DATA) \
	$(gsettings_SCHEMAS) \
	config.h.in

# Copy all the spec files. Of cource, only one is actually used.
dist-hook:
	for specfile in *.spec; do \
		if test -f $$specfile; then \
			cp -p $$specfile $(distdir); \
		fi \
	done

gtk_update_icon_cache = gtk-update-icon-cache -f -t $(datadir)/icons/hicolor

update-icon-cache:
	@-if test -z "$(DESTDIR)"; then \
		$(gtk_update_icon_cache); \
	fi

install-data-hook: update-icon-cache

gsettings_ENUM_NAMESPACE = org.mate.mate-mplayer.preferences
gsettings_ENUM_FILES = $(top_srcdir)/src/*.h
gsettings_SCHEMAS = org.mate.mate-mplayer.preferences.gschema.xml org.mate.gecko-mediaplayer.preferences.gschema.xml

@GSETTINGS_RULES@

