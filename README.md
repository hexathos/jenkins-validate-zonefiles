jenkins-validate-zonefiles
==========================

This is a build.xml file for jenkins. It demands on: Getting bind - zonefiles (e.g. via git), installed bind utils and rsync. 
It also requires a ssh setup for the jenkinsuser, giving IdentityFile and saved hostkeys.

In my example, I am using a custom script "UpdateBind", which produces an include file for bind, getting zonenames from filenames (just removing .dns) and reloading bind.

The validatezonefiles target uses apply, for a fileset, which includes the zonefiles (**/*.dns). It calls named-checkzone if there is no error, it will deploy the zonefiles via rsync, and reloading remote bind server. 

There is much space for improvements ;-)
