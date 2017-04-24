## Synopsis

Short script to keep dnscrypt-proxy running on my OpenWRT router.

## Motivation

I've had some problems recently where dnscrypt-proxy would suddenly would not be running. Possibly related to powerloss and my cable modem getting a new DHCP lease (maybe new IP?) To fix this, I would need to SSH into my OpenWRT router and start the service manually. This is no good.

## Installation

This project consists of two files:

- dnscrypt-proxy-check resides in `/etc/init.d` and should start the script.
- dnscrypt-proxy-keeprunning resides in `/usr/bin` checks if dnscrypt-proxy is running and attempt to restart if necessary.

Put the two files where they belong, `chmox +x` if necessary, and enable the service by doing `/etc/init.d/dnscrypt-proxy-check enable`

## Tests

After installing the files, I tested by doing (roughly) this:

- Start/stop the init script and check whether or not `dnscrypt-proxy-keeprunning` by using `ps`.
- With `dnscrypt-proxy-keeprunning` running, attempt to kill `dnscrypt-proxy` and see that it is started again after some time.