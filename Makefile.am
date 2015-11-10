cfgdir		 = $(datadir)/vyatta-cfg/templates
opdir		 = $(datadir)/vyatta-op/templates
share_perl5dir	 = $(datarootdir)/perl5

sysconf_DATA =

cpiop = find  . ! -regex '\(.*~\|.*\.bak\|.*\.swp\|.*\#.*\#\)' -print0 | \
  cpio -0pd

install-exec-hook:
	mkdir -p $(DESTDIR)$(cfgdir)
	cd templates-cfg; $(cpiop) $(DESTDIR)$(cfgdir)
	mkdir -p $(DESTDIR)$(opdir)
	cd templates-op; $(cpiop) $(DESTDIR)$(opdir)
	mkdir -p $(DESTDIR)/etc/ppp/ip-pre-up.d
	cp sysconf/rename-pppoe $(DESTDIR)/etc/ppp/ip-pre-up.d/0002rename-pppoe
	chmod 755 $(DESTDIR)/etc/ppp/ip-pre-up.d/0002rename-pppoe
	mkdir -p $(DESTDIR)/opt/vyatta/etc
	cp sysconf/pppoe-provider-template $(DESTDIR)/opt/vyatta/etc
	mkdir -p $(DESTDIR)/opt/vyatta/etc/ppp/templates
	cp ppp-templates/* $(DESTDIR)/opt/vyatta/etc/ppp/templates/
	chmod +x $(DESTDIR)/opt/vyatta/etc/ppp/templates/*
