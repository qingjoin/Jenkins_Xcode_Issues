#jenkins 集成 Xcode 常见错误


###FATAL: Failed to mkdirs: /Users/XXX....
###java.io.IOException: Failed to mkdirs: /Users/XXX...

***command*** #chmod -R 777./   





###"Code Sign error: There are no valid certificate/private key pairs in the default keychain"
Solution: Copy your iPhone developer certificate from "login" keychain to "System" keychain.
Detailed steps:
  open the "Keychain Access" application, click the login tab, right click the certificate like "iPhone Developer: your_name (XXXXXXX)", choose copy, then click the "System" tab, right click mouse, choose "Paste 2 items"; you might need to do the same thing with the certificate like "iPhone Distribution: your_name".
After doing this, you will get the second error.





### "Code Sign error: Provisioning profile 'xxxxx-xxxx-xxxx-xxxxx' can't be found"
Solution: Copy the provision profile to Jenkins user folder.
The provision profile is under in the folder
/YourUserName/Library/MobileDevice/Provisioning Profiles,
for example in my machine, the provision profile files are under /Users/steve/Library/MobileDevice/Provisioning Profiles
In the mac, the Jenkins will be in /Users/Shared/Jenkins, create the following folder:
/Users/Shared/Jenkins/Library/MobileDevice/Provisioning Profile,  then copy the .mobileprovision file to this folder.


http://code-dojo.blogspot.co.uk/2012/09/fix-ios-code-signing-issue-when-using.html