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

### Before starting

Navigate to mediawiki folder, open LocalSettings.php file and add this line:

    $wgReadOnly = 'Maintenance';

Make a database backup and a backup of the wiki directory. Dump them in backups/ for safekeeping.

### Upgrade Mediawiki

Instructions here: http://www.mediawiki.org/wiki/Manual:Upgrading

Clone latest mediawiki core into temp directory, eg: /temp/core

    cd /tmp && git clone https://gerrit.wikimedia.org/r/p/mediawiki/core.git
    
Navigate to current mediawiki directory and delete these folders:
* tests
* serialized
* resources
* mw-config
* maintenance
* languages
* includes
* docs
* cache

Move all files from /tmp/code into current meidawiki directory (overwriting)

Execute update script:

    cd /current/meidawiki/dir && php maintenance/update.php --quick
    
Note: If script produce errors, please follow steps below and run it again.

### Upgrade SMW

Before upgrading, read
http://semantic-mediawiki.org/wiki/Help:Installation#Upgrading_existing_installations
as there may be special steps you need to follow if there are major
changes between versions.

Navigate to mediawiki directory
Run composer update:

    php composer.phar update
    
Run update script:

    php maintenance/update.php --quick

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
