i2p-reseeder
============

[I2P](https://geti2p.net) Reseeder written in Python (WSGI).

It can run under all webservers supporting WSGI.

It also contains a built in webserver used for testing.


## Dependencies ##

It depends on [Werkzeug](https://pypi.python.org/pypi/Werkzeug)
(The Python WSGI Utility Library).

Run `apt-get install python-werkzeug` or `pip install werkzeug`.

This is tested with Python 2.7 and Werkzeug 0.9.4.


## INSTALL ##

* Install all dependencies `apt-get install python-werkzeug libapache2-mod-wsgi apache2`
* Create a SSL certificate (If you use openssl you can do; `openssl req -x509 -newkey rsa:4096 -keyout key.pem -out cert.pem -days 3650`)
* Edit apache or nginx to use wsgi.py
* Copy the prod.dist file to prod.conf and edit it so it matches your environment
* Download the code

Example
```
cd /var/www/
git clone https://github.com/mikalv/i2p-reseeder.git us.reseed.i2p2.no
```

* Make sure required apache modules is enabled `a2enmod wsgi ssl`
* Restart apache `service apache2 restart`
* Test your reseed server with a I2P router, check for errors in the log

### Permissions ###

Webserver needs access to the netDb files.

This works for me:

    cd /home/i2p/.i2p
    chgrp -R www-data netDb
    chmod -R g+rX netDb
    find netDb/ -type d | xargs chmod g+s
