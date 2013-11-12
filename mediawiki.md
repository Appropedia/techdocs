# Appropedia Mediawiki notes

## Upgrading

### Download all the things!

* Mediawiki: http://www.mediawiki.org/wiki/Download
* Semantic Mediawiki: http://semantic-mediawiki.org/wiki/Help:Download

The best way to download is to use the shell and:

    cd src/
	wget http://direct.download.link.blah.blah
	tar -xzvf mediawiki-blah-blah.tar.gz

You should also download the latest versions of all the extensions we use.  Look in the wiki's
LocalSettings.php and/or the extensions/ directory and/or the src/ directory to get a sense of what that
will involve -- noting that LocalSettings.php is the definitive listing of what's actually in use at any
given time.  

For each extension, find it on http://mediawiki.org/ and download the latest version into src/ and unzip
it.

### Make backups

Make a database backup and a backup of the wiki directory. Dump them in backups/ for safekeeping.

### Upgrade Mediawiki

Instructions here: http://www.mediawiki.org/wiki/Manual:Upgrading

### Upgrade extensions

Note: Semantic Mediawiki is just an extension, for the purposes of this exercise.

For the most part, you should be able to just copy stuff from src/ into the wiki's extensions/ directory.
However, I recommend you do this one extension at a time, carefully, checking that each one works as you
do it.
