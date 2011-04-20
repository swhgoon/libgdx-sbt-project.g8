# libgdx sbt project

A [g8](http://github.com/n8han/giter8) template to get up and running with Scala and [libgdx](http://code.google.com/p/libgdx/) in a matter of seconds.

## Setting up a new project

To use this template, you will need to install g8 first.
Read g8's [readme](http://github.com/n8han/giter8#readme) for more information.

Then, in your favorite shell, type the command:

    $ g8 ajhager/libgdx-sbt-project

This will prompt you for a few parameters. Type in the options you would like to change, or just press enter to accept the default. For example, if I wanted to create the next greatest Asteroids clone:

    package [my.game.pkg]: com.ajhager.hageroids
    name [Game]: Hageroids
    android_api_level [11]:
    desktop_backend [lwjgl]:
    scala_version [2.8.1]:
    sbt_version [0.7.5]:

You can see that I created a new package, com.ajhager.hageroids, for my new game Hageroids. I just pressed enter to accept the lastest android api level, scala version, and sbt versions, as well as the lwjgl backend. Finally, you just need to update your project with the needed libraries:

    $ cd hageroids
    $ sbt update

This will download scala, sbt, and the libgdx nightly build. Soon you will be able to choose any version of libgdx you'd like. For now, every time you update in the main directory, the bleeding edge libraries will be fetched and installed for your project.

## Where to go from here

Your project now has four folders inside it, which house one parent project and 3 subprojects. The project folder contains the configuration for the building and maintenance of the others.

### Common
You will put all your custom game code under the Common project at common/src/main/scala and your game data at common/src/main/resources.

### Desktop
The only thing you should need to modify in the Desktop project is the starting resolution of the app in desktop/src/main/scala/Main.scala. While in the main directory, you can manipulate the desktop project using sbt by selecting it as the current project. To run your game, type the command:

    $ sbt "project Desktop" run

Or, if you already have sbt running:

    > project Desktop
    Set current project to Desktop
    > run

### Android
The Android project contains the AndroidManifest and various resources needed for your application. You shouldn't need to modify anything in this project, but have a look around if you need finer control over your settings. 

To get started, you wil once again need to make sure you are using the Android project. You will also need to make sure adb is running and recognizes your emulator device:

    $ adb devices

Then you can package and run your game:

    $ sbt "project Android" package start-emulator

At the moment, the Android project is only setup to work with testing on the emulator. Very soon you will be able to sign and deploy your game for an actual device.

## Credits
This g8 template is based on the project generated by [n8han](http://github.com/n8han)'s [android-app](https://github.com/n8han/android-app.g8) and uses [jberkel](http://github.com/jberkel)'s [android-plugin](https://github.com/jberkel/android-plugin).

## Todo
 * Add sbt options for choosing between libgdx nightlies and stable
 * Add one step desktop packaging and deployment
 * Add webstart project and deployment
 * Add android package signing
