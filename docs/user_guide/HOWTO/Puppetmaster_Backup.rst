.. _ug-howto-back-up-the-puppet-master:

HOWTO Back up the Puppet Master
===============================

This section details the steps required to back up the Puppet master.

.. NOTE::

   A default SIMP installation can use Git as a rudimentary method to back up
   the Puppet master. If a different method is preferred, the user must install
   and configure it first.

#. Backup **/etc/puppetlabs/puppet/ssl**
#. Backup **/etc/puppetlabs/puppet**
#. Backup **/var/simp**
#. Backup **\`puppet config --section master print vardir\`/simp**
#. *Optional:* Backup **/var/www**


**Simple Full Backup Command**

.. code-block:: bash

   # tar --selinux --xattrs -czpvf simp_backup-$(date +%Y-%m-%d).tar.gz /etc/puppetlabs /var/simp `puppet config --section master print vardir`/simp /var/www /var/simp

**Simple Full Restore Command**

.. code-block:: bash

   # WARNING: This will overwrite your current system files!
   tar --selinux --xattrs -C / -xzpvf simp_backup-<date>.tar.gz

.. NOTE::

   This will not back up the data in the LDAP Server.  That must be done
   separately.
