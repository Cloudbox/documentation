# Emby

1. [Introduction](extras-emby.md#1-introduction)
2. [URL](extras-emby.md#2-url)
3. [Initial Setup](extras-emby.md#3-initial-setup)
   1. [Domain](extras-emby.md#i-domain)
   2. [Install](extras-emby.md#ii-install)
4. [Setup Wizard](extras-emby.md#4-setup-wizard)
5. [Settings](extras-emby.md#5-settings)
   1. [Users](extras-emby.md#i-users)
   2. [Transcoding](extras-emby.md#ii-transcoding)
   3. [Libraries](extras-emby.md#iii-libraries)
      * [Add Movie Library](extras-emby.md#add-movie-library)
      * [Add TV Shows Library](extras-emby.md#add-tv-shows-library)
6. [API Key](extras-emby.md#6-api-key)

## 1. Introduction

[Emby](https://emby.media) is a media server designed to organize, play, and stream audio and video to a variety of devices

![](https://i.imgur.com/P3TkSfV.jpg)

## 2. URL

* To access Emby, visit [https://emby.\_yourdomain.com\_](https://emby._yourdomain.com_)

## 3. Initial Setup

### i. Domain

* See [Adding a Subdomain](../more-information/adding-a-subdomain.md) for details on how to add the subdomain `emby` to your DNS provider.
* _Note: You can skip this step if you are using_ [_Cloudflare_](../prerequisites/prerequisites-cloudflare.md) _with Cloudbox._

### ii. Install

* Run the following commands:

  ```bash
  cb install emby
  ```

## 4. Setup Wizard

1. Visit [https://emby.\_yourdomain.com\_](https://emby._yourdomain.com_).
2. Select your **preferred display language**. Click **Next**.

   ![](https://i.imgur.com/mbRLNED.png)

3. **Type** the following and click **Next**:

   * **Your first name:** _your name_
   * **Emby connect username or email address**: _your_ [_Emby Connect username_](https://emby.media/connect) \(important\)

   ![](https://i.imgur.com/IdAHjqP.png)

4. Confirm the message by clicking **Got It**.

   ![](https://i.imgur.com/RvXgVck.png)

5. **Confirm** the link in your email.

   ![](https://i.imgur.com/Ah8LCBQ.png)

   ![](https://i.imgur.com/8kB6UVI.png)

6. Skip the adding of the libraries. Click **Next**.

   ![](https://i.imgur.com/76WN7KQ.png)

7. Select your **Preferred Metadata Language** and **Country** \(_`English` and `United States` are recommended_\) and click **Next**.

   ![](https://i.imgur.com/YPFIbfH.png)

8. Check **Allow remote connections to this Emby Server**. Uncheck **Enable automatic port mapping**. Click **Next**.

   ![](https://i.imgur.com/fD1AknT.png)

9. **Check** to accept the terms. Click **Next**.

   ![](https://i.imgur.com/KEhZYFa.png)

10. Click **Finish**.

    ![](https://i.imgur.com/ZJ1m6dZ.png)

11. You will now be taken to the **Dashboard** view.

## 5. Settings

### i. Users

1. Go to **Settings**.
2. Go to **Users**.

   ![](https://i.imgur.com/a1zdnRz.png)

3. Click the **Password** tab at the top.
4. Type in your password in **New password** and **New password confirm**. Click **Save**.

   ![](https://i.imgur.com/PUTS7AX.png)

5. Click **Save** again.

   ![](https://i.imgur.com/XG8A70a.png)

### ii. Transcoding

1. Go to **Settings**.
2. Go to **Transcoding**.

   ![](https://i.imgur.com/MFZxd88.png)

3. Under **Enable hardware acceleration when available**, select **Advanced**.

   ![](https://i.imgur.com/iReeH6e.png)

4. Under **Preferred Hardware Encoders**, go down to **H.264 \(AVC\)**, and select **VAAPI H.264** \(_for Intel CPUs with Intel Quick Sync Video enabled_\).

   ![](https://i.imgur.com/FM7kODJ.png)

5. Under **Transcoding temporary path**, type in or choose `/transcode`.

   ![](https://i.imgur.com/b9jRVSm.png)

6. Click **Save**.

### iii. Libraries

In this section, we will add two libraries: one for Movies and one for TV Shows.

#### Add Movie Library

1. Go to **Settings**.
2. Go to **Library**.

   ![](https://i.imgur.com/Reixrpp.png)

3. Click **Add Media Library**.
4. Under **Content type**, select **Movies**.

   ![](https://i.imgur.com/Afwb8oH.png)

   ![](https://i.imgur.com/MUqjrm5.png)

5. Click **+** next to **Folders**.
6. Type in or choose `/data/Movies`. Click **OK**.

   _Note: These_ [_paths_](../basics/basics-cloudbox-paths.md) _are for the standard library setup. If you have_ [_customized_](../advanced-configuration/customizing-plex-libraries-1.md) _it, use those paths instead._

   ![](https://i.imgur.com/UiXspBL.png)

7. Click **OK** once more.

   ![](https://i.imgur.com/gjOtiSy.png)

#### Add TV Shows Library

1. Go to **Settings**.
2. Go to **Library**.

   ![](https://i.imgur.com/Reixrpp.png)

3. Click **Add Media Library**.
4. Under **Content type**, select **TV shows**.

   ![](https://i.imgur.com/Afwb8oH.png)

   ![](https://i.imgur.com/ThVUSyI.png)

5. Click **+** next to **Folders**.
6. Type in or choose `/data/TV`. Click **OK**.

   _Note: These_ [_paths_](../basics/basics-cloudbox-paths.md) _are for the standard library setup. If you have_ [_customized_](../advanced-configuration/customizing-plex-libraries-1.md) _it, use those paths instead._



   ![](https://i.imgur.com/shR8IZB.png)

7. Click **OK** once more.

   ![](https://i.imgur.com/gI0jAIq.png)

## 6. API Key

Instructions below will guide you through creating an API Key for a specific app.

1. Click the **Settings** icon.

   ![](https://i.imgur.com/ooc9sCL.png)

2. Under **Expert**, click **Advanced**.

   ![](https://i.imgur.com/dslwDdM.png)

3. Click the **Security** tab at the top.

   ![](https://i.imgur.com/Zd1XW28.png)

4. Under **Api Keys** click **+**.

   ![](https://i.imgur.com/hcmabil.png)

5. Fill in an **App name** \(e.g. Ombi\) and click **OK**.

   ![](https://i.imgur.com/CSonhIf.png)

6. And now have created an **Api Key** for your app.

   ![](https://i.imgur.com/Ixi686z.png)

