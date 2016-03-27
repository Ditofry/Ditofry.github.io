---
layout: post
title:  "GoPro Protocol"
categories: gopro api c++ protocal
---

# Overview
GoPro Hero3 and Hero4 devices will spawn their own public wireless network.  One may
connect to a GoPro via this network, and having done so retrieve the device's hardware data,
status data, and media. It is also possible to send commands to the GoPro and control
it via this protocol, which has been implemented in **[under-development]**

### Connecting to GoPro Device
`http:://<10.5.5.9>/gp/`
and it's possible that the port must be `8080`

By default GoPros make themselves available at `10.5.5.9` (why? Default gateway via router or default for GoPro...) Theoretically this could change depending on device and routing structure, and indeed would have to change in the case of multiple GoPro devices living on the network.

### Media Storage
Photos and Video are stored at: `http:://<10.5.5.9>/gp/Videos`
Streaming data found in `http:://<10.5.5.9>/gp/live/`

### Command Usage
`http:://<10.5.5.9>/gp/gpControl/command/<group>?p=<id>`

Where `<group>` is a class of commands and `<id>` is an integer identifier of
the specific command to be executed

### Streaming
Start `http://10.5.5.9/gp/gpControl/execute?p1=gpStream&c1=start`

Restart `http://10.5.5.9/gp/gpControl/execute?p1=gpStream&c1=restart`

Stop `http://10.5.5.9/gp/gpControl/execute?p1=gpStream&c1=stop`

**Note: to collect streamed data one will need to send a "keep alive" signal every 10 seconds while piping**

### Settings
##To change:##
`http:://<10.5.5.9>/gp/gpControl/setting/<group_id>/<setting_id>`

#### Settings table


| Group Description         | Setting Description      | group_id | setting_id |
| :-------------            | :-------------           | :------- |:---------- |
| Framerate                 | 120fps                   | 3        | 0          |
| Framerate                 | 90fps                    | 3        | 3          |
| Framerate                 | 60fps                    | 3        | 5          |
| Framerate                 | 48fps                    | 3        | 7          |
| Framerate                 | 30fps                    | 3        | 8          |
| Framerate                 | 24fps                    | 3        | 10         |
|                           |                          |          |            |
| Resolutions               | 4k                       | 2        | 1          |
| Resolutions               | 4k Superview             | 2        | 2          |
| Resolutions               | 2.7k                     | 2        | 4          |
| Resolutions               | 2.7k Superview           | 2        | 5          |
| Resolutions               | 2.7k 4:3                 | 2        | 6          |
| Resolutions               | 1440p                    | 2        | 7          |
| Resolutions               | 1080p SuperView          | 2        | 8          |
| Resolutions               | 1080p                    | 2        | 9          |
| Resolutions               | 960p                     | 2        | 10         |
| Resolutions               | 720p Superview           | 2        | 11         |
| Resolutions               | 720p                     | 2        | 12         |
| Resolutions               | WVGA                     | 2        | 13         |
