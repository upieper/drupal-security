K) Regular Maintenance
======================

.. highlight:: bash

No security plan is foolproof.  You need regular backups to ensure that you can
restore your system quickly if required.  With both the database and file system
it is important to have both local and remote backups.  You want the local
backup because that allows you to quickly restore the site if there is a
problem.  You want a remote backup in case of total system failure.  There are
many ways to setup and configure this.  Some helpful backup solutions include:

.. hlist::
   :columns: 4

   - `Bacula <http://www.bacula.org/>`_
   - `rsync <https://rsync.samba.org/>`_/`rsnapshot <http://www.rsnapshot.org/>`_
   - `mysqldump <https://dev.mysql.com/doc/refman/5.1/en/mysqldump.html>`_
   - `xtrabackup <http://www.percona.com/doc/percona-xtrabackup>`_

Remember that a backup is only good if it can be restored.  It's a best practice
to make use of `RAID drives`_, but RAID should be used as a failsafe and not
considered a backup strategy.  Backups should be stored regularly locally, but
there also need to be regular, long-term backups stored off-site.  Make sure to
evaluate your backup procedures and test your restores to verify that they are
working effectively.  Drupal.org releases `security updates`_ on Wednesdays when
needed which are broadcast by an email list, `RSS feeds`_ and `Twitter`_.
Subscribe to the security newsletter for updates (you will need a Drupal.org
account and the instructions are on the sidebar of the previous link).  It is
also useful to check the Status page and Watchdog pages in your Drupal site.

`SELinux provides auditing services`_ which are worth monitoring.  You should be
watching your server logs, particularly your Apache error log::

  $ tail -f /var/log/httpd/error_log
  $ grep 'login.php' /var/log/httpd/error_log
  $ egrep -i "denied|error|warn" /var/log/httpd/error_log

Security best practices are constantly changing.  OWASP has released their `Top
10 for 2013`_ and it is somewhat similar to the 2010 list.  The Top 10 for 2010
was leveraged to look at `how it applies to Drupal`_.  This needs to be updated,
and reviewed, particularly if you are writing any custom code.  It's a simple
idea, but it can be good to search `Google for test data`_ that might have been
left in development or exposed in an upgrade.  Anything in a draft mode should
never be exposed to the Internet.

`Acquia's Insights`_ provides a useful tool to get regular insights on how to
improve your website.  Their security section will be able to do a quick review
of your website to check on a number of security related issues.  They also
address performance, best practices, SEO and code analysis.  With the `Acquia
Network Connector`_ module, this can be easily and securely done on any website
accessible to the Internet.  Their dashboard provides an easy way for you to
regularly monitor important elements of your site.

`Qualys`_ and `Rapid7`_ both offer a number of other security monitoring and
risk assessment services.  These are included in Acquia's hosting.

.. _RAID drives: https://en.wikipedia.org/wiki/RAID
.. _security updates: https://drupal.org/security
.. _RSS feeds: https://drupal.org/security/psa/rss.xml
.. _Twitter: https://twitter.com/drupalsecurity
.. _SELinux provides auditing services: http://drupalwatchdog.com/volume-2/issue-2/using-apache-and-selinux-together
.. _Top 10 for 2013: https://www.owasp.org/index.php/Top_10_2013-Introduction
.. _how it applies to Drupal: http://www.cameronandwilding.com/blog/pablo/10-most-critical-drupal-security-risks
.. _Google for test data: https://www.google.com/search?q=site:healthcare.gov%20intext:%22test%22
.. _Acquia's Insights: https://www.acquia.com/products-services/acquia-network/cloud-services/insight
.. _Acquia Network Connector: https://drupal.org/project/acquia_connector
.. _Qualys: https://www.qualys.com/
.. _Rapid7: http://www.rapid7.com/
