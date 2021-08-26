<!--
N.B.: This README was automatically generated by https://github.com/YunoHost/apps/tree/master/tools/README-generator
It shall NOT be edited by hand.
-->

# PyInventory for YunoHost

[![Integration level](https://dash.yunohost.org/integration/pyinventory.svg)](https://dash.yunohost.org/appci/app/pyinventory) ![](https://ci-apps.yunohost.org/ci/badges/pyinventory.status.svg) ![](https://ci-apps.yunohost.org/ci/badges/pyinventory.maintain.svg)  
[![Install PyInventory with YunoHost](https://install-app.yunohost.org/install-with-yunohost.svg)](https://install-app.yunohost.org/?app=pyinventory)

*[Lire ce readme en français.](./README_fr.md)*

> *This package allows you to install PyInventory quickly and simply on a YunoHost server.
If you don't have YunoHost, please consult [the guide](https://yunohost.org/#/install) to learn how to install it.*

## Overview

Web based management to catalog things including state and location etc.

**Shipped version:** 0.9.2~ynh1



## Screenshots

![](./doc/screenshots/screenshot3.png)
![](./doc/screenshots/screenshot2.png)
![](./doc/screenshots/screenshot1.png)

## Disclaimers / important information

* Any known limitations, constrains or stuff not working, such as (but not limited to):
    * requiring a full dedicated domain ?
    * architectures not supported ?
    * not-working single-sign on or LDAP integration ?
    * the app requires an important amount of RAM / disk / .. to install or to work properly
    * etc...

* Other infos that people should be aware of, such as:
    * any specific step to perform after installing (such as manually finishing the install, specific admin credentials, ...)
    * how to configure / administrate the application if it ain't obvious
    * upgrade process / specificities / things to be aware of ?
    * security considerations ?

## Settings and upgrades

Almost everything related to PyInventory's configuration is handled in a `"../conf/settings.py"` file.
You can edit the file `/opt/yunohost/pyinventory/local_settings.py` to enable or disable features.

Test sending emails:

```bash
ssh admin@yourdomain.tld
root@yunohost:~# cd /opt/yunohost/pyinventory/
root@yunohost:/opt/yunohost/pyinventory# source venv/bin/activate
(venv) root@yunohost:/opt/yunohost/pyinventory# ./manage.py sendtestemail --admins
```

Background info: Error mails are send to all [settings.ADMINS](https://docs.djangoproject.com/en/2.2/ref/settings/#std:setting-ADMINS). By default the YunoHost admin is inserted here.
To check current ADMINS run:

```bash
(venv) root@yunohost:/opt/yunohost/pyinventory# ./manage.py sendtestemail --admins
```

If you prefere to send error emails to a extrnal email address, just do something like this:

```bash
echo "ADMINS = (('Your Name', 'example@domain.tld'),)" >> /opt/yunohost/pyinventory/local_settings.py
```

To check the effective settings, run this:
```bash
(venv) root@yunohost:/opt/yunohost/pyinventory# ./manage.py diffsettings
```

## SSO authentication

[SSOwat](https://github.com/YunoHost/SSOwat) is fully supported via [django_ynh](https://github.com/YunoHost-Apps/django_ynh):

* First user (`$YNH_APP_ARG_ADMIN`) will be created as Django's super user
* All new users will be created as normal users
* Login via SSO is fully supported
* User Email, First / Last name will be updated from SSO data

## Documentation and resources

* Upstream app code repository: https://github.com/jedie/PyInventory
* YunoHost documentation for this app: https://yunohost.org/app_pyinventory
* Report a bug: https://github.com/YunoHost-Apps/pyinventory_ynh/issues

## Developer info

Please send your pull request to the [testing branch](https://github.com/YunoHost-Apps/pyinventory_ynh/tree/testing).

To try the testing branch, please proceed like that.
```
sudo yunohost app install https://github.com/YunoHost-Apps/pyinventory_ynh/tree/testing --debug
or
sudo yunohost app upgrade pyinventory -u https://github.com/YunoHost-Apps/pyinventory_ynh/tree/testing --debug
```

**More info regarding app packaging:** https://yunohost.org/packaging_apps