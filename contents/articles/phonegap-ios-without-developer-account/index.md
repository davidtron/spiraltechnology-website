---
title: Install phone gap apps on iPhone without developer account
author: david
date: 2014-01-10
template: article.jade
---


1. Download nodes
http://nodejs.org/download/
2. Install phonegap
	$ sudo npm install -g phonegap

3. phonegap create my-app
cd my-app
phone gap build ios




How to build and install phone gap apps on jailbroken iOS 7 devices


1. Create a self signed certificate

 - open the Keychain Access application
 - select Keychain Access > Certificate Assistant > Create A Certificate …  
 - On the first page fill in the following
	Name: iPhone Developer
	Identify Type: Self Signed Root
	Certification Type: Code Signing
	Select “Let me override defaults” and press continue, it will say "You are about to create a self-signed certificate." 
        press continue


 - On the second page fill in the following
	Serial number: 1
	Validity period : 3650
        press continue

 - On the third page remove your email address.
 - Keep pressing continue until you reach the Specify location page, press create.

2. Open the terminal. For Xcode 5.02 these paths are valid but might need to be updated for newer versions. 

 > cd /Applications/Xcode.app/Contents/Developer/Platforms/iPhoneOS.platform

 - create a backup of Info.plist and change it into xml
 > sudo cp -p Info.plist Info.plist.orig
 > sudo plutil -convert xml1 ./Info.plist

$ # replace each occurrence of CiPhoneOSCodeSignContext with XCCodeSignContext in Info.plist
$ sudo sed -i .bkup 's/XCiPhoneOSCodeSignContext/XCCodeSignContext/g' ./Info.plist





http://mhassan.me/2013/02/15/using-xcode-without-provisioning-profile/
