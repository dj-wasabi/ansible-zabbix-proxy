#ansible-zabbix-server Release

Below an overview of all changes in the releases.

Version (Release date)

1.0.0   (2017-09-10)

  * Changed from ini to yml style

0.5.0   (2017-07-17)

  * Renaming docker-py to docker #10
  * [!] fix misspelling with property ListenIP #9 (By pull request: lebe-dev (Thanks!))
  * Add Amazon Linux support #7 (By pull request: kostyrev (Thanks!))
  * Add HistoryIndexCacheSize for zabbix 3.2 #6 (By pull request: kostyrev (Thanks!))
  * Molecule test #5
  * Fix bugs with LoadModule & add sqlite3 support #2 (By pull request: splitice (Thanks!))
  * Zabbix proxy 3.0 fixes #1 (By pull request: zbal (Thanks!))

0.4.0   (2016-08-24)

  * ?

0.3.0   (2016-02-08)

  * Added test-kitchen tests
  * Small bug fix for installation on RedHat/Debian

0.2.0   (2016-02-04)

  * Added travis-ci test.

0.1.0   (2015-02-01)

   * Updated readme
   * added double quotes on names
   * added var zabbix_repo
   * added var for database creation and load file

0.0.1   (2014-10-31)

  * Initial Creation
