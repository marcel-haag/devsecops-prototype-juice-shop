# devsecops-prototype-juice-shop
Prototype implementation of an open-source DevSecOps reference model based on OWASP Juice Shop.



OWASP Juice Shop is probably the most modern and sophisticated insecure web application! It can be used in security
trainings, awareness demos, CTFs and as a guinea pig for security tools! Juice Shop encompasses vulnerabilities from the
entire
[OWASP Top Ten](https://owasp.org/www-project-top-ten) along with many other security flaws found in real-world
applications!

For a detailed introduction, full list of features and architecture overview please visit the official project page:
<https://owasp-juice.shop>

## Table of contents

- [Setup](#setup)
    - [From Sources](#from-sources)
    - [Packaged Distributions](#packaged-distributions)
    - [Docker Container](#docker-container)
    - [Vagrant](#vagrant)
- [Demo](#demo)
- [Documentation](#documentation)
    - [lorem](#lorem)
- [Donations](#donations)
- [Contributors](#contributors)
- [Licensing](#licensing)

## Setup

> You can find some less common installation variations as well as instructions to run Juice Shop on a variety of cloud computing providers in
> [the _Running OWASP Juice Shop_ documentation](https://pwning.owasp-juice.shop/companion-guide/latest/part1/running.html).

### From Sources

![GitHub repo size](https://img.shields.io/github/repo-size/juice-shop/juice-shop.svg)

1. Install [node.js](#nodejs-version-compatibility)
2. Run `git clone https://github.com/juice-shop/juice-shop.git --depth 1` (or
   clone [your own fork](https://github.com/juice-shop/juice-shop/fork)
   of the repository)
3. Go into the cloned folder with `cd juice-shop`
4. Run `npm install` (only has to be done before first start or when you change the source code)
5. Run `npm start`
6. Browse to <http://localhost:3000>

### Packaged Distributions

[![GitHub release](https://img.shields.io/github/downloads/juice-shop/juice-shop/total.svg)](https://github.com/juice-shop/juice-shop/releases/latest)
[![SourceForge](https://img.shields.io/sourceforge/dm/juice-shop?label=sourceforge%20downloads)](https://sourceforge.net/projects/juice-shop/)
[![SourceForge](https://img.shields.io/sourceforge/dt/juice-shop?label=sourceforge%20downloads)](https://sourceforge.net/projects/juice-shop/)

1. Install a 64bit [node.js](#nodejs-version-compatibility) on your Windows, MacOS or Linux machine
2. Download `juice-shop-<version>_<node-version>_<os>_x64.zip` (or
   `.tgz`) attached to
   [latest release](https://github.com/juice-shop/juice-shop/releases/latest)
3. Unpack and `cd` into the unpacked folder
4. Run `npm start`
5. Browse to <http://localhost:3000>

> Each packaged distribution includes some binaries for `sqlite3` and
> `libxmljs2` bound to the OS and node.js version which `npm install` was
> executed on.

### Docker Container

[![Docker Pulls](https://img.shields.io/docker/pulls/bkimminich/juice-shop.svg)](https://hub.docker.com/r/bkimminich/juice-shop)
![Docker Stars](https://img.shields.io/docker/stars/bkimminich/juice-shop.svg)
[![](https://images.microbadger.com/badges/image/bkimminich/juice-shop.svg)](https://microbadger.com/images/bkimminich/juice-shop
"Get your own image badge on microbadger.com")
[![](https://images.microbadger.com/badges/version/bkimminich/juice-shop.svg)](https://microbadger.com/images/bkimminich/juice-shop
"Get your own version badge on microbadger.com")

1. Install [Docker](https://www.docker.com)
2. Run `docker pull bkimminich/juice-shop`
3. Run `docker run --rm -p 127.0.0.1:3000:3000 bkimminich/juice-shop`
4. Browse to <http://localhost:3000> (on macOS and Windows browse to
   <http://192.168.99.100:3000> if you are using docker-machine instead of the native docker installation)

### Vagrant

1. Install [Vagrant](https://www.vagrantup.com/downloads.html) and
   [Virtualbox](https://www.virtualbox.org/wiki/Downloads)
2. Run `git clone https://github.com/juice-shop/juice-shop.git` (or
   clone [your own fork](https://github.com/juice-shop/juice-shop/fork)
   of the repository)
3. Run `cd vagrant && vagrant up`
4. Browse to [192.168.56.110](http://192.168.56.110)

## Demo

Feel free to have a look at the latest version of OWASP Juice Shop:
<http://demo.owasp-juice.shop>

> This is a deployment-test and sneak-peek instance only! You are __not
> supposed__ to use this instance for your own hacking endeavours! No
> guaranteed uptime! Guaranteed stern looks if you break it!

## Documentation

### lorem
lorem

## Donations

[![](https://img.shields.io/badge/support-owasp%20juice%20shop-blue)](https://owasp.org/donate/?reponame=www-project-juice-shop&title=OWASP+Juice+Shop)

The OWASP Foundation gratefully accepts donations via Stripe. Projects such as Juice Shop can then request reimbursement
for expenses from the Foundation. If you'd like to express your support of the Juice Shop project, please make sure to
tick the "Publicly list me as a supporter of OWASP Juice Shop" checkbox on the donation form. You can find our more
about donations and how they are used here:

<https://pwning.owasp-juice.shop/companion-guide/latest/part3/donations.html>

## Contributors

The OWASP Juice Shop Project Leaders are:

- [Björn Kimminich](https://github.com/bkimminich) aka `bkimminich` [![Keybase PGP](https://img.shields.io/keybase/pgp/bkimminich)](https://keybase.io/bkimminich)
- [Jannik Hollenbach](https://github.com/J12934) aka `J12934`

For a list of all contributors to the OWASP Juice Shop please visit our
[HALL_OF_FAME.md](HALL_OF_FAME.md).

## Licensing

[![license](https://img.shields.io/github/license/juice-shop/juice-shop.svg)](LICENSE)

This program is free software: you can redistribute it and/or modify it under the terms of the [MIT license](LICENSE).
OWASP Juice Shop and any contributions are Copyright © by Bjoern Kimminich & the OWASP Juice Shop contributors
2014-2026.