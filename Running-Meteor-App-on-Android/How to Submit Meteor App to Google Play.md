# Submit your application to Google Play

1. create meteor application with in-app purchase button
2. install cordova plugin:

		meteor add cordova:cc.fovea.cordova.purchase

3. Get the Billing Key from Services and API section on Google Play Developer Console
4. Configure 'mobile-config.js' file with the following:

		App.info({
		  name: 'MyApp',
		  description: 'An Android app built with Meteor',
		  version: '0.0.1'
		});

		App.icons({
		  // Android
		  "android_ldpi": "resources/icons/icon-36x36.png",
		  "android_mdpi": "resources/icons/icon-48x48.png",
		  "android_hdpi": "resources/icons/icon-72x72.png",
		  "android_xhdpi": "resources/icons/icon-96x96.png"
		});

		App.configurePlugin("cc.fovea.cordova.purchase", {
		  BILLING_KEY : "MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAiwDp2adKmZhvSnli1qH9WJ/L51Az8AvOlzeobHyDsdqwoWfpch6ZwoyP4pK9YTi3v4foWJuRE/H0G4Uo9hRmsXIMzOfJ3+SVFxFqItNFD6Y/qPj8g7cLhfw6c/t7ljXGw7O2nhxV4B2SgLnz5lQzqAiZ60TbXfPuL4vP3mVCx4oZklnzd1rZXnRyR+F4T2bbNOlBxW/F4gUJG5g76GVd7OPv3MWvLYS9SjjpyJdEzpzErb7YZ19oMAC0VYxiaLoPmhEx8E2NtGtiYMn+8X/F1lZCjaSTnMcRsEYn61arWQyF5LJ0vNTYcnnZoT1ys/qv3pkE9V0WGLwgtXubG0HMrQIDAQAB"
		});

5. You can deploy the app on 'your-app-name.meteor.com' before building it, like so:

		meteor deploy your-desired-app-hostname.meteor.com
		meteor build ~/build-output-directory --server=your-desired-app-hostname.meteor.com

or build it locally by pointing the server to your IP, like this:

		meteor build ~/build-output-directory --server=http://your-ip-address

6. Go to the build output directory folder and find the apk file. By default, it is located at:
		
		/home/ricardo/builds/android/project/build/outputs/apk

7. To sign your app for production, you'll need a private key. This key lets you publish and update your app. If you haven't made a key for this app, run:

		cd /home/ricardo/builds/android/project/build/outputs/apk
		keytool -genkey -alias 'your-app-name' -keyalg RSA -keysize 2048 -validity 10000

And answer the questions that will appear like first and last name, organization name, city, state, and country, then enter yes. You will need to enter key password for <you-app-name>, or if it's the same as the keystore password, just press Enter.

**Note: Ensure that you have secure backups of your keystore (~/.keystore). If you publish an app to Google Play and then lose the key with which you signed your app, you will not be able to publish any updates to your app, since you must always sign all versions of your app with the same key.

8. Now, you can sign your app:

		cd ~/home/ricardo/builds/android/project/build/outputs/apk
		jarsigner -verbose -sigalg SHA1withRSA -digestalg SHA1 'unaligned.apk' 'your-app-name'
		/home/ricardo/builds/android/project/build/outputs/apk/build-tools/23.0.2/zipalign 4 'unaligned.apk' 'your-app-name.apk'

9. Then you need to submit a zipaligned app to google play. You can do this like so:

		cd ~/home/ricardo/builds/android/project/build/outputs/apk
		~/Android/Sdk/build-tools/23.0.2/zipalign 4 'name-of-unsigned-apk.apk' 'your-app-name.apk'

10. Submit the apk to Google Play.

