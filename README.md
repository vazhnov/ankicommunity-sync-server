ankisyncd
=========

A personal Anki sync server (so you can sync against your own server rather than
AnkiWeb). This version has been modified from dsnopek's Anki Sync Server to
remove the REST API, which makes it possible to drop some dependencies.

Installing
----------

1. Install the dependencies:

        $ pip install webob

2. Patch the bundled libanki:

	$ ./patch_libanki.sh

3. Modify ankisyncd.conf according to your needs

4. Create user:

        $ ./ankisyncctl.py adduser <username>

5. Run ankisyncd:

        $ python ./ankisyncd/sync_app.py

Setting up Anki
---------------

To make Anki use ankisyncd as its sync server, create a file (name it something
like ankisyncd.py) containing the code below and put it in ~/Anki/addons.

    import anki.sync

    anki.sync.SYNC_BASE = 'http://127.0.0.1:27701/'
    anki.sync.SYNC_MEDIA_BASE = 'http://127.0.0.1:27701/msync/'

Replace 127.0.0.1 with the IP address or the domain name of your server if
ankisyncd is not running on the same machine as Anki.