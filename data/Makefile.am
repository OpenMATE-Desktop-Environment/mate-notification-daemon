icon16dir = $(datadir)/icons/hicolor/16x16/apps
icon22dir = $(datadir)/icons/hicolor/22x22/apps
icon24dir = $(datadir)/icons/hicolor/24x24/apps
icon32dir = $(datadir)/icons/hicolor/32x32/apps
icon48dir = $(datadir)/icons/hicolor/48x48/apps
iconscalabledir = $(datadir)/icons/hicolor/scalable/apps

icon16_DATA = icons/16x16/notification-properties.png
icon22_DATA = icons/22x22/notification-properties.png
icon24_DATA = icons/24x24/notification-properties.png
icon32_DATA = icons/32x32/notification-properties.png
icon48_DATA = icons/48x48/notification-properties.png
iconscalable_DATA = icons/scalable/notification-properties.svg


servicedir   = $(DBUS_SERVICES_DIR)
service_DATA = org.freedesktop.Notifications.service

schemasdir       = $(GCONF_SCHEMA_FILE_DIR)
schemas_in_files = notification-daemon.schemas.in
schemas_DATA     = $(schemas_in_files:.schemas.in=.schemas)

@INTLTOOL_SCHEMAS_RULE@

if GCONF_SCHEMAS_INSTALL
install-data-local:
	GCONF_CONFIG_SOURCE=$(GCONF_SCHEMA_CONFIG_SOURCE) $(GCONFTOOL) --makefile-install-rule $(schemas_DATA)
else
install-data-local:
endif

EXTRA_DIST = \
	$(schemas_in_files) \
	$(service_DATA) \
	$(icon16_DATA) \
	$(icon22_DATA) \
	$(icon24_DATA) \
	$(icon32_DATA) \
	$(icon48_DATA) \
	$(iconscalable_DATA)

CLEANFILES = $(schemas_DATA)


gtk_update_icon_cache = gtk-update-icon-cache -f -t $(datadir)/icons/hicolor

install-data-hook: update-icon-cache
uninstall-hook: update-icon-cache
update-icon-cache:
	@-if test -z "$(DESTDIR)"; then \
		echo "Updating Gtk icon cache."; \
		$(gtk_update_icon_cache); \
	else \
		echo "*** Icon cache not updated.  After (un)install, run this:"; \
		echo "***   $(gtk_update_icon_cache)"; \
	fi

-include $(top_srcdir)/git.mk
