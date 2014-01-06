# Appropedia Mediawiki notes

## Upgrading

### Download all the things!

* Mediawiki: http://www.mediawiki.org/wiki/Download
* Semantic Mediawiki: http://semantic-mediawiki.org/wiki/Help:Download

The best way to download is to use the shell and:

    cd src/
    wget http://direct.download.link.blah.blah
    ar -xzvf mediawiki-blah-blah.tar.gz

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

Note that Mediawiki's recommended upgrade process changed around MW
1.21.  Instead of telling you to un-tar the code directly over your
existing installation, they recommend doing it in a new directory and
then copying lots of files across.  Sadly, their docs are buggy and
incomplete, and this didn't work for us.  Therefore, let's stick with
the old method for now, which is:

    tar xzvf src/mediawiki-X-Y-X.tar.gz -C appropedia.org/ --strip-components=1
    cd appropedia.org/maintenance
    php update.php

If you see an error message about PHP version 5.3, you may need to do:

    /usr/local/bin/php53/bin/php update.php

(However, we'll make an alias for that in our .bashrc so hopefully it
won't be a problem.)

If you are a person from the future, you may want to check the MW
upgrading docs and see if they are improved, and consider doing their
new recommended method.  However, at this stage (MW 1.21, November 2013)
I can't recommend it.

### Upgrade SMW

You should do this via the semantic-bundle package, available at
http://www.mediawiki.org/wiki/Semantic_Bundle

This includes SMW and a bunch of other useful extensions that all work
together.

Before upgrading, read
http://semantic-mediawiki.org/wiki/Help:Installation#Upgrading_existing_installations
as there may be special steps you need to follow if there are major
changes between versions.

If you require a database refresh (as happened when upgrading to version
1.8) you should allow several hours for this to run.  As of 1.8, it took
about 2 hours, but didn't work at first, so consider yourself warned.

To actually install the semantic-bundle:

* Download the bundle into src/
* Install the bundle as follows:

    tar xzvf src/SemanticBundle-blah-blah.tar.gz -C appropedia.org/extensions

(replacing blah-blah with the version/date, of course.)

Note there is no need for --strip-components.  This should just
overwrite a whole bunch of extensions.

### Testing SMW upgrade

The core thing to test is:

* Go to the medical devices portal,
  http://www.appropedia.org/Portal:Medical_Devices, where you should see
  a variety of medical devices listed.

More detail on testing SMW (which you should *definitely* follow) can be
found in testing.md.

### Upgrade extensions

To know which extensions to upgrade, do something like:

    grep require_once appropedia.org/LocalSettings.php | grep -v '^#'

For each extension you'll need to:

* Find that extension's page on http://mediawiki.org/
* Download the latest tarball into src/
* Untar it
* Copy the results over the old extension directory in
  appropedia.org/extensions

Extensions sometimes act odd if there is old cruft left around, however,
so it's often good to remove the old extension directory and
then copy the new one into its place, eg.

    rm -rf ~/appropedia.org/extensions/SomeExtension
    mv src/SomeExtension ~/appropedia.org/extensions

FUTURE WORK: ideally we should update using version control, as
described on the MW extensions pages. We do not yet have this set up,
however.
