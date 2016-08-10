# PhishingReporter

### This is still very much in development

Report phishing emails and have the notification sent to your security team. A button is created in Outlook using the Microsoft Junk Reporting Add-in and Powershell for deployment across an enterprise. This is not my idea, I have taken inspiration from http://www.nerdosaur.com/network-security/add-a-report-phishing-button-in-outlook and hacked it to fit what I need. For step by Step instructions, see the blog post linked above.

This does not work on 64 bit installs of office. There is a 64 bit version of the Junk Reporting Add-in but I have not tested it.

I am a novice scripter so take this code with a grain of salt, there very well may be better ways to this, this is my way. If anyone knows of a better way to do this, that's free and simple to setup, please let me know.

##Basic Outline:

1) Download & install the Junk Reporting Add-in. You need to install the Junk Reporting Add-in on any machine you want this Outlook button on. You can download the Junk Reporting Add-in for Office 2007, 2010, 2013, and 2016 (32-bit) here: https://www.microsoft.com/en-us/download/details.aspx?id=18275

2) Edit the `HKLM:SOFTWARE\wow6432node\Microsoft\Junk E-mail Reporting\Addins` BccEmailAddress Registry key to include any email address you would like

3) Add the 'Report Phishing' button to any ribbons you would like (eg, the Home ribbon, Message Ribbon)

4) Copy your customized olkmailread.officeUI and olkexplorer.officeUI files from C:\users\%username%\AppData\Local\Microsoft\Office to every machine you want the Outlook button on. You could also store these files on a network share and create a login script to push these files to the user.

4) Restart Outlook

5) By default when you 'Report' the Phishing Email it will send an email to abuse@messaging.microsoft.com (If you want to avoid this I suggest you either find where in the Add-in code the email is configured and change it, or do what I did, create a rule in your mail filtering application to block those emails on the way out)
