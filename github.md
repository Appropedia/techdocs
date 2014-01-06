# Appropedia github

We have set up a github organization as "Appropedia", which can be found at http://github.com/Appropedia

If you are doing tech work for Appropedia, you should probably get yourself added as an "owner" of this
organization.  Any current owner can add you here:
https://github.com/organizations/Appropedia/teams/564556

## techdocs repo

A repo has been created for technical documentation, at
http://github.com/Appropedia/techdocs.  This is intended for techies
working on Appropedia to take notes on what they've done, to make things
easier for those who come after.

This repo has been cloned on the VPS account, under doc/, using the
HTTPS cloning method.  You're probably best off editing the docs from
there, and pushing them up regularly.

You might be wondering why we don't just keep these docs on the wiki
itself.  Well, what if the wiki is down?  This means you still have the
necessary information to get it up and running again.

### Configuration

Whoever's mostly doing work on the VPS, you should set up the git config to use your name/email when
committing.

    git config --global user.name "Your Name"
	git config --global user.email you@example.com

(If multiple people are doing work around the same time, this will get messy, and a better solution will
need to be found. But it'll work for now while there's just one person working here, i.e. me.)

### To update docs direct from the VPS

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

