ThinkUp on OpenShift
=========================
ThinkUp is a free, open source web application that captures all your activity on social networks like Twitter, Facebook and Google+.

With ThinkUp, you can store your social activity in a database that you control, making it easy to search, sort, analyze, publish and display activity from your network. All you need is a web server that can run a PHP application.

More information can be found on the official thinkup website at http://thinkupapp.com/

Running on OpenShift
--------------------

Create an account at http://openshift.redhat.com/

Create a PHP application

	rhc-create-app -a thinkup -t php-5.3 -l $USERNAME

Add mysql support to your application
    
	rhc-ctl-app -a thinkup -e add-mysql-5.1 -l $USERNAME

Make a note of the username, password, and host name as you will need to use these to complete the Piwik installation on OpenShift

Add this upstream thinkup quickstart repo

	cd thinkup/php
	rm -rf *
	git remote add upstream -m master git://github.com/lucasmingarro/ThinkUp-openshift-quickstart.git
	git pull -s recursive -X theirs upstream master

Then push the repo upstream to OpenShift

	git push

That's it, you can now checkout your application at:

	http://thinkup-$yournamespace.rhcloud.com/install

