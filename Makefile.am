cfgdir		 = $(datadir)/vyatta-cfg/templates
opdir		 = $(datadir)/vyatta-op/templates
share_perl5dir	 = $(datarootdir)/perl5
libudevdir	 = /lib/udev
etcudevdir	 = /etc/udev
initddir	 = /etc/init.d

bin_SCRIPTS =
sbin_SCRIPTS =
sysconf_DATA =

# bin_SCRIPTS += scripts/progress-indicator
# sbin_SCRIPTS += scripts/rl-system.init

# noinst_DATA = test_bootfile

# share_perl5_DATA = scripts/keepalived/VyattaKeepalived.pm

# sysconf_DATA += sysconf/logrotate_messages


# libudev_SCRIPTS	 = scripts/vyatta_net_name
# etcudev_DATA	 = sysconf/vyatta-net.rules

# initd_SCRIPTS	 = etc/init.d/vyatta-udev

cpiop = find  . ! -regex '\(.*~\|.*\.bak\|.*\.swp\|.*\#.*\#\)' -print0 | \
  cpio -0pd

install-exec-hook:
	mkdir -p $(DESTDIR)$(cfgdir)
	cd templates-cfg; $(cpiop) $(DESTDIR)$(cfgdir)
	mkdir -p $(DESTDIR)$(opdir)
	cd templates-op; $(cpiop) $(DESTDIR)$(opdir)
	mkdir -p $(DESTDIR)/etc/ppp/ip-up.d
	cp sysconf/0002vyatta-pppoe $(DESTDIR)/etc/ppp/ip-up.d
	chmod 755 $(DESTDIR)/etc/ppp/ip-up.d/0002vyatta-pppoe
	mkdir -p $(DESTDIR)/opt/vyatta/etc
	cp sysconf/pppoe-provider-template $(DESTDIR)/opt/vyatta/etc
	mkdir -p $(DESTDIR)/etc
	cd etc ; $(cpiop) $(DESTDIR)/etc



