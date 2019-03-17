# salebot [![License](https://img.shields.io/badge/license-GPLv3-blue.svg)](/LICENSE)

**THIS FORK IS A WORK IN PROGRESS — DON'T TAKE ANYTHING FOR GRANTED**

**salebot** is an anti-vandalism bot for Wikipedia

Salebot follows recent changes on IRC, detects the most obvious cases of 
vandalism, and attempts to revert them.
It tries to sort out editors between likely vandals and good-faith editors,
using a scoring system. Trusted users are no longer watched, so Salebot
concentrates on new editors.

Salebot runs on the French and Portuguese Wikipedias.

## Installation on Debian Stretch

The following commands must be run as root:

```sh
git clone https://github.com/Arkanosis/salebot.git /opt/salebot
useradd -r salebot
cp /opt/salebot/contribs/systemd/salebot.service /etc/systemd/system
mkdir /etc/salebot
cp /opt/salebot/config/samples/salebot.conf.sample /etc/salebot/salebot.conf
apt install libpoe-perl libpoe-component-irc-perl liblog-log4perl-perl libclass-dbi-perl libregexp-ipv6-perl libmediawiki-api-perl libtext-unaccent-perl libnet-dns-perl libtext-diff-perl
mkdir -p /usr/local/share/perl5/Net
curl 'http://www.cpan.org/authors/id/B/BO/BORISZ/Net-DNSBLLookup-0.05.tar.gz' | tar xz -C /tmp Net-DNSBLLookup-0.05/lib
mv /tmp/Net-DNSBLLookup-0.05/lib/Net/* /usr/local/share/perl5/Net
```

Edit the configuration in `/etc/salebot/salebot.conf`.`

## Usage

Starting salebot is as easy as:

```sh
sudo systemctl start salebot
```

So is stopping it:

```sh
sudo systemctl stop salebot
```

To have salebot run after a reboot:

```sh
sudo systemctl enable salebot
```

To check is salebot is running as expected:

```sh
sudo systemctl status salebot
```

To read salebot logs:

```sh
sudo journalctl -u salebot
```

## Contributing and reporting bugs

Contributions are welcome through [GitHub pull requests](https://github.com/kimonberlin/salebot/pulls).

Please report bugs and feature requests on [GitHub issues](https://github.com/kimonberlin/salebot/issues).

## License

salebot is copyright (C) 2007-2019 Kimon Berlin and licensed under the GPLv3.
