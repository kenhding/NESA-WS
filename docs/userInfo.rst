User Info
====


Server Access 
----
Here are the addess to both servers. If you enter 5 times incorrect password within 30 mins, your IP will be blocked for 10 mins.

Server IP:

::

  ssh <user name>@192.168.137.231



User Storage
----
The server was equipped with a total storage of 7 TB(3TB NVMe SSD + 4T SATA SSD), 5.3TB was avaiable to share bewteen all users. The user accounts are located under the ``/home`` path configured. The overview and the mount path as below:



::
  
  Filesystem             Size  Used Avail Use% Mounted on
  /dev/mapper/rhel-home  5.4T   52G  5.3T   1% /home


.. warning::
To maximize the usage and performance, we do NOT have [Quota](https://linux.die.net/man/1/quota) and [RAID](https://de.wikipedia.org/wiki/RAID) configuration on the server. Therefore, the recommended approach is to have your test/experimental dataset on the server but large database and headvy processing outputs to the [NAS](https://www.synology.com/en-uk/company/news/article/DS920plus) where has a RAID and large storage (36TB in total). 

User Permission
----

**NAS access:**

The current configuration disabled the direct access from users to the NAS path. NAS access can be acquired from the administrator. You will find a soft link folder under your own ``/home/<user name>`` path.

**Python:**

Python on the server is provided via ``pyenv``. A personal/customized python environment can be managed by ``virtualenv``. For example:

.. code-block:: console

pyenv virtualenv 3.10

>>> import lumache
>>> lumache.get_random_ingredients()
['shells', 'gorgonzola', 'parsley']



Virtual environment steps can be found on `Mogon WIKI <https://mogonwiki.zdv.uni-mainz.de/dokuwiki/start:development:scripting_languages:python?s[]=virtual>`_  

..warning::
 Installing packages via ``pip`` is allowed with virtual environment only.



.. warning::
To maximize the usage and performance, we do NOT have [Quota](https://linux.die.net/man/1/quota) and [RAID](https://de.wikipedia.org/wiki/RAID) configuration on the server. Therefore, the recommended approach is to have your test/experimental dataset on the server but large database and headvy processing outputs to the [NAS](https://www.synology.com/en-uk/company/news/article/DS920plus) where has a RAID and large storage (36TB in total). 


**Software:**

Popular neuroimaging software such as FSL, freesurfer, etc are loaded in Docker, the data processing are tested already, you can also create your software environment without disturbing the default one. In case new software is needed, please call the hotline 7849. 

**Matlab:**

Matlab path file is usually saved in ``pathdef.m``, users do not have permission to modify it. The first time you add your path, Matlab will ask you to create a local ``pathdef.m`` for yourself without bothering others. Toolbox is also recommended to install locally under your account.


Data Backup
----

The NAS_ is performing differential backup every first day of each month for both servers. Data stored in the directory ``/home``  ``/media`` (Server1) and ``/mnt`` (Server2) will be synchronized. 



.. _NAS: https://shop.westerndigital.com/de-at/products/network-attached-storage/wd-my-cloud-pro-series-pr4100#WDBNFA0000NBK-EESN
.. _Anaconda: https://www.anaconda.com/
.. _RAID: https://en.wikipedia.org/wiki/RAID
