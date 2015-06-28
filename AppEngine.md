<h1>Work with Google App Engine</h1>

If you are unfamiliar with Google App Engine (GAE), but know something about cloud computing, read [What is Google App Engine?](https://developers.google.com/appengine/docs/whatisgoogleappengine) If you're completely new to cloud computing as well, a more user-friendly introduction to the cloud and GAE can be found in this [Introduction to Google App Engine](https://developers.google.com/academy/apis/cloud/appengine/intro/).

You do not need to be a GAE expert to work with Course Builder. There are just a few things you should be familiar with while developing your course. Much of this is discussed on other pages. We summarize it  here.

This page discusses using GAE as it relates to Course Builder. For information on working with it to deploy your course and to modify it after deployment, see [Deploy to Google App Engine for the First Time or Subsequent Deployments to Google App Engine](DeployAgain.md).

**Note:** Several of these pages refer to a "shell or command prompt". If you're unsure what that means, see [What's a "shell or command prompt"?](http://code.google.com/p/gcb-x-03141590/wiki/FAQ#What%27s_a_%22shell_or_command_prompt%22?)



## Important: Quotas and billing ##
The use of GAE for your course may incur some costs. Currently, each GAE application can consume a certain level of computing resources for free, controlled by a set of [limits](https://developers.google.com/appengine/docs/quotas). If you need resources above these free limits, you can switch to a paid app to set a daily resource budget.

It's difficult to predict in advance the costs for your course since it will depend on how much load you you put on GAE (see [Billing and Budgeting Resources](https://developers.google.com/appengine/docs/billing) and [Quotas](https://developers.google.com/appengine/docs/quotas) for details). It is likely that any significantly sized course _will_ incur costs. For example, a small course with a small number of student-GAE interactions may be perpetually on GAE's free quota. Remember that any customizations that you make may increase the load and therefore the GAE costs.


Remember that you can begin development and testing of your course at no charge, by using the downloaded development server (from the [Google App Engine SDK](https://code.google.com/p/course-builder/wiki/AppEngine#Download_and_install_App_Engine)) and the free quota initially provided by GAE for deployed applications. That free quota is fairly limited and is unlikely to support a sizable course enrollment.

Also note that you can control your cost by setting a [maximum daily budget](https://developers.google.com/appengine/docs/billing#Setting_a_Daily_Budget), which will cap your costs (and your quota) per day.  However, doing so may lead to your course becoming unavailable for the remainder of any day that your application exceeds its budget.


## View the GAE Admin Console on your local machine ##
When GAE starts Course Builder on your local machine, it also starts an associated Admin Console. If your app is available at `http://localhost:/8080`, its Admin Console is at `http://localhost:8080/_ah/admin`.

From the console, you can see and modify the content of your local data store.

<img src='http://wiki.course-builder.googlecode.com/git/images/admin-console.png' height='231' width='327' />

We suggest you do your development after deploying to GAE and view the Admin Console from its servers directly. Seeing the Admin Console from your local machine is merely for safe exploration.

### Restart local server and reload all data ###

To clear and reload all data,  you need to stop your development server, restart it clearing out the old data, reload the new data, and then tell GAE to start using the new data..

  1. Stopping your development server depends on how you started it:
    * If you started your server **from the Launcher**, go to the Launcher application and quit it.
    * If you started your server **from a command prompt on a PC**, bring up the Windows Task Manager and on the **Applications** tab, search for the task that looks like `Command Prompt - dev_appserver.py .` Select that task and click on **End Task**.
    * If you started  your server **from a shell on Mac, Linux, or other POSIX-compliant system**:<br><br>  <code>ps x | grep dev_appserver   # Find the process number</code><br><br><font color='green'> <code>30849 s000  S      0:00.85 /Library/Frameworks/Python.framework/Versions/2.7/Resources/Python.app/Contents/MacOS/Python /usr/local/bin/dev_appserver.py .</code> </font><br><font color='green'> <code>30856 s000  R+     0:00.01 grep dev_appserver</code> </font><br> <br><code>kill 30849</code>
</li></ul><ol><li>You can either start your development server from the Launcher or the command line. In either case, you must be sure to clear out the old data:<br>
<ul><li>To start from the Launcher:<br>
<ul><li>Double-click on the name of the application to get the <b>Settings</b> dialog box.<br>
</li><li>In the <b>Launch Settings</b> area, choose <b>Clear datastore on launch</b>. <br> (This is a sticky setting. Once you set it, every time you relaunch the application, GAE clears the data store.)<br>
</li><li>Click on <b>Update</b>.<br>
</li><li>Back in the Launcher, click on <b>Run</b> to restart the application.<br>
</li></ul></li><li>To start from the command line:<br><br>  <code>cd </code><i><b><code>APPPATH</code></b></i><br>  <code>dev_appserver.py --clear_datastore .</code> <br><br>where <i><b><code>APPPATH</code></b></i> is the directory containing your app. <i>Note that the period at the end of that command is necessary.</i></li></ul></li></ol>

<h2>Official GAE documentation</h2>

There's a lot of <a href='https://developers.google.com/appengine/docs/python/config/appconfig#Required_Elements'>official documentation</a> for GAE.<br>
<br>
<table><thead><th> <a href='https://groups.google.com/forum/?fromgroups#!categories/course-builder-forum/customize-and-deploy-course-builder-code'>Ask questions in the forum</a> </th></thead><tbody>