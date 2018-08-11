# library-to-bintray
## The guide to building an Android Library, push it to Bintray and then JCenter and sent to Android Arsenal..


## Build and upload library to Bintray
- Step 1:
Sign up an Open Source account on bintray by this link: [Create Account](https://bintray.com/signup/oss).

- Step 2:
Add these lines at the bottom of local.properties
```
bintray.user=tntkhang #replace by your Bintray username
bintray.apikey=0000xxx000xxx000xxxx000xxxx00xxxx000 #replace by your api key
```

- Step 3:
In the Project contain the library you want to push to Bintray, add these line in the dependencise of build.gradle in project level. 
```
classpath 'com.jfrog.bintray.gradle:gradle-bintray-plugin:1.7.3'
classpath 'com.github.dcendents:android-maven-gradle-plugin:1.5'
```

- Step 4:
In the build.gradle of the library below 
```
apply plugin "com.android.library"
```
add those lines
```
ext {
    bintrayRepo = 'maven'
    bintrayName = 'my-library-helper'   // Replace by your library name, has to be same as your library module name

    publishedGroupId = 'com.github.tntkhang'
    libraryName = 'my-library-helper'  //  Replace by your library name, has to be same as your library module name
    artifact = 'my-library-helper'     // Replace by your library name, has to be same as your library module name

    libraryDescription = 'This is description about this library'

    // Your github repo link
    siteUrl = 'https://github.com/tntkhang/my-library-helper' // Replace by your url
    gitUrl = 'https://github.com/tntkhang/my-library-helper.git' // Replace by your url
    githubRepository= 'tntkhang/my-library-helper' // Replace by your url

    libraryVersion = '1.0.0' // Increase whenever you update library version

    developerId = 'tntkhang' // Replace by your name
    developerName = 'KhangTran' // Replace by your name
    developerEmail = 'tntkhang@gmail.com' // Replace by your email

    licenseName = 'The MIT License'
    licenseUrl = 'https://opensource.org/licenses/MIT'
    allLicenses = ["MIT"]
}
```

- Step 5:
Place it at the end of the file
```
apply from: 'https://raw.githubusercontent.com/tntkhang/library-to-bintray/master/install.gradle'
apply from: 'https://raw.githubusercontent.com/tntkhang/library-to-bintray/master/bintray.gradle'
```

- Step 6:
Open ternimal and run command:
```
gradlew clean build install bintrayUpload
```

## Add uploaded library to JCenter
- Step 1: Create an account in OSS Sonatype: [Create Account](https://issues.sonatype.org/secure/Signup!default.jspa).
- Step 2: Add OSS Sonatype account into Bintray: Go to [Bintray Setting](https://bintray.com/profile/edit) -> Account -> input your OSS Sonatype Account
- Step 3: On the library page in Bintray click on "Add to JCenter" button

## Sent the library to Android Arsenal
Go to this Android Arsenal [contact page](https://android-arsenal.com/contact) input library detail and click Suggest to them.
