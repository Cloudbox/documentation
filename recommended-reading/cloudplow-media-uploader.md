# Cloudplow \(Media Uploader\)

* [Intro](https://github.com/Cloudbox/Cloudbox/wiki/Cloudplow#intro)
* [Config](https://github.com/Cloudbox/Cloudbox/wiki/Cloudplow#config)
* [CLI](https://github.com/Cloudbox/Cloudbox/wiki/Cloudplow#cli)

## Intro

[Cloudplow](https://github.com/l3uddz/cloudplow) \(CP\) is a script created by [l3uddz](https://github.com/l3uddz) that has one primary purpose as related to Cloudbox:

1. Uploader to Rclone remote: Files are moved off local storage. With support for multiple uploaders \(i.e. remote/folder pairings\).

### Remote Uploader Function

As setup for Cloudbox, Cloudplow uploads all the content in `/mnt/local/Media/` \(see [Paths](https://github.com/Cloudbox/Cloudbox/wiki/Basics%3A-Cloudbox-Paths#clouplow)\) to your cloud storage provider \(e.g. Google Drive\), after the folder reaches a `200` GB size threshold, when checked every `30` minutes.

_Note: The size threshold and the check interval can be changed via steps mentioned on this page._Google Drive Daily Upload Limit \(click to expand\)

## Config

### Default config.json file

See [Config: Cloudplow](https://github.com/Cloudbox/Cloudbox/wiki/Config%3A-Cloudplow).

### Location

```text
/opt/cloudplow/config.json
```

Note: Config changes require a restart: `sudo systemctl restart cloudplow`.

### Editing

Edit in your favorite code editor \(with json highlighting\) or even a unix editor like nano.

```text
nano /opt/cloudplow/config.json
```

Note: The cloudplow config file is a JSON file. JSON files have a particular format and syntax. If you are unfamiliar with JSON formatting and syntax, don't edit this file until you have gained that familiarity. Here's a [random YouTube video](https://www.youtube.com/watch?v=GpOO5iKzOmY) that will give you a ten-minute overview.

### Modify Upload Threshold and Interval

```text
    "uploader": {
        "google": {
            "check_interval": 30,
            "exclude_open_files": false,
            "max_size_gb": 200,
            "opened_excludes": [
                "/downloads/"
            ],
            "size_excludes": [
                "downloads/*"
            ]
        }
```

`"check_interval":` How often \(in minutes\) Cloudplow checks the size of `/mnt/local/Media`.

`"max_size_gb":` Max size \(in GB\) Cloudplow allows `/mnt/local/Media` to get before starting an upload task.

* Note: `max_size_gb` is rounded up, so it is advised to have it minimum `2GB` or else it would attempt upload at each interval. Explanation below.
  * `1GB` is basically anything in there.
  * `2GB` is at least 1GB of data.

### Plex Integration

Cloudplow can throttle Rclone uploads during active, playing Plex streams \(paused streams are ignored\).

```text
  "plex": {
      "enabled": false,
      "url": "https://plex.domain.com",
      "token": "",
      "poll_interval": 60,
      "max_streams_before_throttle": 1,
      "rclone": {
          "throttle_speeds": {
              "0": "1000M",
              "1": "50M",
              "2": "40M",
              "3": "30M",
              "4": "20M",
              "5": "10M"
          },
          "url": "http://localhost:7949"
      }
  }
```

`enabled` - Change `false` to `true` to enable.

`url` - Your Plex URL.

`token` - Your [Plex Access Token](https://github.com/Cloudbox/Cloudbox/wiki/Plex-Access-Token).

`poll_interval` - How often \(in seconds\) Plex is checked for active streams.

`max_streams_before_throttle` - How many playing streams are allowed before enabling throttling.

`rclone`

* `url` - Leave as default.
* `throttle_speeds` - Categorized option to configure upload speeds for various stream counts \(where `5` represents 5 or more streams\). `M` is MB/s.
  * Format:

    ```text
    "STREAM COUNT": "THROTTLED UPLOAD SPEED",
    ```

### Pushover Notifications

See [here](https://github.com/Cloudbox/Cloudbox/wiki/Pushover#cloudplow).

### Restart

Restart Cloudplow to apply the changes to the config.

```text
sudo systemctl restart cloudplow
```

## CLI

You can run a manual Cloudplow task from anywhere by just using the `cloudplow` command.

### Manual Upload

To start uploading right away, regardless of what the folder size is:

```text
cloudplow upload
```

