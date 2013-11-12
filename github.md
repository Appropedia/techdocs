# Appropedia github

We have set up a github organization as "Appropedia", which can be found at http://github.com/Appropedia

If you are doing tech work for Appropedia, you should probably get yourself added as an "owner" of this
organization.  Any current owner can add you here:
https://github.com/organizations/Appropedia/teams/564556

## techdocs repo

A repo has been created for technical documentation, at http://github.com/Appropedia/techdocs.  This is
intended for techies working on Appropedia to take notes on what they've done, to make things easier for
those who come after.

This repo has been cloned on the VPS account, under doc/, using the HTTPS cloning method.  To update docs
direct from the VPS:

    cd doc/
	vi somefile.md
	
	# see your changes
	git status

	# add any new files you created
	git add somefile.md

	# commit your changes
	git commit -a -m "Added tips on frobnicating the widgets"

	# push the changes up to github
	git push origin master
	# you will have to enter your github username/password at this point

Assuming you have rights to the repo, you can also edit the doc files direct on Github.  Go to the
specific file, eg. https://github.com/Appropedia/techdocs/blob/master/README.md, then click the "Edit"
button. Easy.

