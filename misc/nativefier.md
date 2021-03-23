# Nativefier

* [Intro](nativefier.md#intro)
* [NPM](nativefier.md#npm)
* [Docker](nativefier.md#docker)

## Intro

[Nativefier](https://github.com/jiahaog/nativefier#nativefier) is a cross-platform, Electron application \(built on Chromium and Node.js\), that allows you to turn any website into a native OS app. This way you can easily "open" and "close" your Cloudbox apps without the memory footprint of a typical internet browser.

Screenshots \(macOS\):

![](https://i.imgur.com/bHYzgix.png)

![](https://i.imgur.com/QnTjO7e.png)

## NPM

The following steps will guide you through setting up Nativefier on your PC to generate apps.

### 1. Setup Nativefier

1. Install [Node.js](https://nodejs.org/en/download/current)
2. For macOS, install [Xcode](https://developer.apple.com/xcode) and [ImageMagick](https://www.imagemagick.org/script/download.php) [\[1\]](nativefier.md#note1)
   * _Note: This is only needed for automatic website icon to app icon conversion. If you want to skip installing Xcode and ImageMagick, but still want to be able to customize the application icon, you can do so by; first, finding a transparent png of the application \(e.g. google image search `transparent png appname`\), and then, following directions on this_ [_page_](https://support.apple.com/en-us/HT201737).
3. Install Nativefier with this command:

   ```text
   sudo npm install nativefier -g
   ```

### 2. Create Nativefier Desktop Apps

![](https://github.com/jiahaog/nativefier/raw/master/screenshots/walkthrough.gif)

#### Basic Command

```text
nativefier appname.domainname.com
```

#### Some Useful Options

* Give it a name:

  ```text
  --name "App Name"
  ```

* Add Basic HTTP Authentication \(replace `yourusername` and `yourpassword` with your login info:

  ```text
  --basic-auth-username yourusername --basic-auth-password yourpassword
  ```

  Note:

  * If you plan to use this, set your apps to use HTTP Authentication \(i.e. Basic or Browser popup\) vs Forms/Login Page. 
  * Apps that will need changing are: Sonarr, Radarr, NZBGet, NZBHydra, and PlexPy \(TauTulli\). 

* Disable dev tools:

  ```text
  --disable-dev-tools
  ```

* Force a specific icon \(`path/to/icon` can be a local file path or a URL\)

  ```text
  --icon "path/to/icon"
  ```

* Force a zoom at start:

  ```text
  --zoom=<zoomlevel>
  ```

  Example:

  ```text
  --zoom=0.8
  ```

  Note: You can also temporarily change the zoom levels with `ctrl` `+` and `ctrl` `-` in Windows or `command` `+` and `command` `-` in macOS.

* In macOS, to completely quit out of the app when you close the window:

  ```text
  --fast-quit
  ```

#### Some examples you can use:

```text
nativefier --name "Sonarr" "https://sonarr.domain.com"
nativefier --name "Radarr" "https://sonarr.domain.com"
nativefier --name "PlexPy" "https://plexpy.domain.com/home"
nativefier --name "Jackett" "https://jackett.domain.com/Admin/Dashboard"
nativefier --name "Plex Requests" "https://plexrequests.domain.com"
nativefier --name "NZBGet" "https://nzbget.domain.com"
nativefier --name "NZBHydra" "https://nzbhydra.domain.com"
nativefier --name "ruTorrent" "https://rutorrent.domain.com"
```

#### Example for MacOS with HTTP authentication enabled

```text
nativefier --name "Sonarr" --basic-auth-username myusername --basic-auth-password mypassword --fast-quit --disable-dev-tools "https://sonarr.domain.com"
```

#### Example for Windows with HTTP authentication enabled

```text
nativefier --name "Sonarr" --basic-auth-username myusername --basic-auth-password mypassword --disable-dev-tools "https://sonarr.domain.com"
```

### 3. Move the Nativefier App

Copy the app \(e.g. `.app` in MacOS, `.exe` in Windows\) to your desktop or the applications location \(i.e. Applications folder in MacOS, Start Menu in Windows\)

## Docker

You can also use the Docker image to create Nativefier binaries.

#### Docker Run Command

```text
docker run  -v ~/:/target jiahaog/nativefier --name "APP NAME" --platform linux/windows/mac --arch x64 --disable-dev-tools --basic-auth-username USERNAME --basic-auth-password PASSWORD https://APP.domain.ltd /target/
```

#### Examples

NZBHydra2 on Windows

```text
docker run  -v ~/:/target jiahaog/nativefier --name "NZBHydra2" -p windows -a x64 --disable-dev-tools --basic-auth-username myusername --basic-auth-password mypassword https://nzbhydra2.domain.com /target/
```

Ombi on Mac

```text
docker run  -v ~/:/target jiahaog/nativefier --name "Ombi" -p mac -a x64 --disable-dev-tools --basic-auth-username myusername --basic-auth-password mypassword https://ombi.domain.com /target/
```

