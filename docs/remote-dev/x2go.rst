=========================
 Remote desktop via X2GO
=========================

`x2go <https://wiki.x2go.org/>`__ allows you to run a browser (or any other application on x-server) on a remote server

Deploying X2GO server
=====================

* Connect to your server
* `install x2go server <https://wiki.x2go.org/doku.php/doc:installation:x2goserver>`_ :


.. code-block:: sh

 sudo add-apt-repository ppa:x2go/stable && \
 sudo apt-get update && \
 sudo apt-get install -y x2goserver x2goserver-xsession

* install desktop environment you prefer, e.g. LXDE:

.. code-block:: sh

 sudo apt-get install lubuntu-desktop
 # choose lightdm

* Install browser `Pale Moon <http://linux.palemoon.org>`_

.. code-block:: sh

 # http://linux.palemoon.org
 sudo sh -c "echo 'deb http://download.opensuse.org/repositories/home:/stevenpusser/xUbuntu_18.04/ /' > /etc/apt/sources.list.d/home:stevenpusser.list"
 wget -nv https://download.opensuse.org/repositories/home:stevenpusser/xUbuntu_18.04/Release.key -O Release.key
 sudo apt-key add - < Release.key
 sudo apt-get update
 sudo apt-get install palemoon

X2GO Client
===========

* install ``x2goclient``

  Ubuntu:

  .. code-block:: sh

      sudo add-apt-repository ppa:x2go/stable && \
      sudo apt-get update && \
      sudo apt-get install x2goclient

  References:

  * https://www.howtoforge.com/tutorial/x2go-server-ubuntu-14-04/
  * http://wiki.x2go.org/doku.php/doc:installation:x2goclient

* Run client:

.. code-block:: sh

   x2goclient


* create a new session with the settings below and connect to it (we assume that you have user named "noroot" with ssh keys configured):

::

 Host : YOUHOST
 Port : 22
 Session type: LXDE
 [x] Try auto Login
 Input / Output: Use Whole Display
 Username: noroot

Firefox usage
=============

You may need to disable ``xrender`` settings in ``about:config`` and `Disable hardware acceleration in Firefox <https://support.mozilla.org/en-US/kb/hardware-acceleration-and-windowblinds-crash>`__. For more information see:

* https://lists.x2go.org/pipermail/x2go-user/2016-August/003914.html
* https://bugzilla.mozilla.org/show_bug.cgi?id=1263222
