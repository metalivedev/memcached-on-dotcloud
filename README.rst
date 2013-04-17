Memcached On dotCloud
=====================

This recipe provides memcached for dotCloud.
While it will allow you to use memcached with your dotCloud app, it has
three caveats:

#. There is no support for authentication. This version of memcached itself `does
   not support authentication anyway <http://code.google.com/p/memcached/wiki/FAQ#How_does_memcached%27s_authentication_mechanisms_work?>`_,
   so this should not be a big surprise.
#. Scaling is not officially supported. You may be able to get it to work with a few tricks.

If this didn't deter you from using memcached on dotCloud, then read ahead!


How It Works
------------

It uses the ``custom`` service type, which allows custom package install.
It also uses the all-new "custom TCP port" feature to expose the memcached
port.


How To Use It (Standalone)
--------------------------

Just use our (un)patented Clone-And-DotCloud-Push method::

  $ git clone git://github.com/jpetazzo/memcached-on-dotcloud.git
  $ cd memcached-on-dotcloud
  $ dotcloud create -f memcached
  $ dotcloud push

At the end of the push, run ``dotcloud info memcached`` to see
the connection parameters::

  -   name: memcached
      url: tcp://memcached-myusername.dotcloud.com:12345

 

How To Use It (In Your App)
---------------------------

Add the ``dotcloud.yml`` supplied here to your own ``dotcloud.yml``.
Push as usual, and use ``dotcloud info`` at the end of the push to
see the host and port number to use to connect to your memcached
service. Enjoy!

TODO
----
Add SASL support for authentication: https://code.google.com/p/memcached/wiki/SASLHowto
