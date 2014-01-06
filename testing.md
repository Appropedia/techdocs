# Testing Appropedia

If you've just upgraded Mediawiki or extensions (see mediawiki.md) or
have done other work, you should go through this list to make sure you
haven't broken anything.

Eventually we would like to make an automated regression test for this.
For now, slog through it by hand.

## Mediawiki core

* Go to http://appropedia.org/ -- site should load
* http://www.appropedia.org/Special:Version should show new version
  number
* Login -- expect success
* Edit a page (eg. your user page) -- expect success

## Semantic mediawiki

* Go to the medical devices portal,
  http://www.appropedia.org/Portal:Medical_Devices, where you should see
  a variety of medical devices listed.
* Try creating a device using
  http://www.appropedia.org/Form:Medical_Device (name it "AAA
  test device" or similar).  The form should work and create a page.
* Go to http://www.appropedia.org/Portal:Medical_Devices and click
  "Refresh" to purge the cache.  The new device should now show up under
  the appropriate category.
* http://www.appropedia.org/Special:BrowseData/Medical_Devices?_single
  should show a drill-down interface to query semantic data.

If any of the above doesn't work, here are some possible diagnostic
tests that might help:

* First, test that the most basic semantic functions work as described
  under
  http://semantic-mediawiki.org/wiki/Help:Installation#Testing_your_Installation
* Try a simple query test using http://www.appropedia.org/Special:Ask,
  eg. put [[testproperty::Dummypage]] in the query box, and you should
  see your test page show up in the results.
* Try running Ask on some real data, eg. put [[Medical Device
  Topic::Malaria]] in the query box, and see if real medical devices
  show up.
* If existing pages aren't showing up in SMW queries or Ask results, try
  editing and re-saving those pages to refresh their semantic
  representation in the database.  Note that you'll have to
  refresh/purge a query page (eg. the medical devices portal) before
  changes appear.  If this works, then your database needs repairing.
  You can do this from the SMWAdmin page at
  http://www.appropedia.org/Special:SMWAdmin

## Other extensions

This list is not comprehensive, but is based primarily on regressions
for things we've broken before.  If you break something else, add it to
this list.

* http://www.appropedia.org/Help:Math should display formulae correctly
* Ensure Google Analytics is working: logout, visit any normal (non
  Special:) page, view source, and look for GA script at bottom page
  page (you may find it helpful to search within source for
  "UA-18072726-1" which is Appropedia's analytics ID).

## Local customisations etc

* XML dumps: check that you can download a dump from
  http://www.appropedia.org/Appropedia:Current_dump
