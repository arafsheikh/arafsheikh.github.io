---
layout:	post
title: Updating an Android app via Github
date: 2015-08-24 00:17:45
---

Yesterday I was working on one of my Android apps which was to be distributed within a closed group. This meant I couldn't update my app via the Google Play Store. Researching a bit I came across [`Evolve`](https://blog.vivekpanyam.com/evolve-seamlessly-deploy-android-apps-to-users), which seemed too complicated for my small project. So I came up with a simple solution:

- Upload the `apk` file and a text file containing the `versionCode` of the app to a remote location
- Query for the `versionCode` file from within the app
- If the remote app's version code is greater than locally installed app's then trigger an update.

Any remote server which gives you a pemalink link for your files will do. My blog is hosted on Github, so that was the obvious choice for me. Once both the files are uploaded then comes the coding part.

To fetch the text file containing the `versionCode` from the remote server:

```java
public static void fetchRemoteAppVersion() throws IOException {

        // URL of the text file
        URL url = new URL("http://sheikharaf.me/data/version.txt");

        // Initialize streams
        URLConnection con = url.openConnection();
        InputStream is = con.getInputStream();

        BufferedReader br = new BufferedReader(new InputStreamReader(is));

        // Traverse the line and store it in a variable
        String line = null;
        if ((line = br.readLine()) != null) {
        	String remote_version = line;
        }

    }
```

Once we have the version code of the remote app then we can compare it with the version code of the local version of the app. `BuildConfig.VERSION_CODE` returns the local `versionCode` of the app (in Android Studio). If it is less than the remote version code then we initiate an update intent.

```java
Intent updateIntent = new Intent(Intent.ACTION_VIEW,
                Uri.parse("http://sheikharaf.me/data/app-release.apk")); // URL of apk
```

This update mechanism can be put inside a service which queries for a new version at regular intervals and notifies the user if an update is available.

Cheers!