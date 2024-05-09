User Info
====


Server Access 
----
Here are the addess to both servers. If you enter 5 times incorrect password within 30 mins, your IP will be blocked for 10 mins.

Server IP:

::

  ssh <user name>@192.168.137.231


**Login Authentication:**
The first time you log in to the server, you will be prompted to change your password. After changing your password, you will see a link similar to the one below. You need to copy and paste this into your web browser:

::

https://<api>.duosecurity.com/frame/portal/v4/enroll?code=<key>

Please follow the instructions on the web to complete the authentication. Have your smartphone ready for this step. After you have registered, log in to the server again. You will be asked for authentication with your app. You can simply type `1` and push the green button prompt on the mobile app.

User Storage
----
The server was equipped with a total storage of 7 TB (3TB NVMe SSD + 4T SATA SSD), 5.3TB was avaiable to share bewteen all users. The user accounts are located under the ``/home`` path configured. The overview and the mount path as below:



::
  
  Filesystem             Size  Used Avail Use% Mounted on
  /dev/mapper/rhel-home  5.4T   52G  5.3T   1% /home


.. warning::
To maximize the usage and performance, we do NOT have Quota_ and RAID_ configuration on the server. Therefore, the recommended approach is to have your test/experimental dataset on the server but large database and headvy processing outputs to the NAS_ where has a RAID_ and large storage (36TB in total). 

User Permission
----

**NAS access:**

The current configuration disabled the direct access from users to the NAS path. NAS access can be acquired from the administrator. You will find a soft link folder under your own ``/home/<user name>`` path.

**Python:**

Python on the server is provided via ``pyenv`` with version from 3.6-3.11. Installing packages via ``pip`` is allowed with virtual environment only. A personal/customized python environment can be managed by ``virtualenv``. For example:

.. code-block:: console

  pyenv virtualenv 3.7 <custom name of environment>
  pyenv activate <custom name of environment>

.. warning::

Do not install conda on the server. If you have complicated dependencies please use Docker or setup it in your own virtual environment.


**Neuroimaging software:**

Popular neuroimaging software such as FSL, freesurfer, etc are loaded in Docker via image of Neurodesk.

**Matlab:**

Matlab setup was elaborated in the inrternal manual.


Data Backup
----

Currently, the NAS_ does not enable the auto sychronization for the server. This is planed.



.. _NAS: https://www.synology.com/en-uk/company/news/article/DS920plus
.. _Anaconda: https://www.anaconda.com/
.. _RAID: https://de.wikipedia.org/wiki/RAID
.. Quota: https://linux.die.net/man/1/quota
.. Neurodesk: https://www.neurodesk.org/docs/getting-started/neurodesktop/linux/
