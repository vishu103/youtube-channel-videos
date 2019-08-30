# Introduction

This is a simple PHP script you can use to extract the videos of a specific YouTube channel. All you need to do is create a YouTube Data v3 API key and get the channel id of the channel you want to get videos of. You can set the maximum results you want the script to return.

### Information this script will return
1. Video ID
2. Video Link
3. Video Name
4. Channel Name
5. Video Publish Date
6. Video Description
7. Video Thumbnail Link

### Getting the YouTube Data v3 API
1. Go to Google Developer console
2. Create or open a project.
3. Add the YouTube Data v3 API to your project.
4. Generate an API key and copy it.
5. Paste the API key into the script.

```php
// API Key
$API_Key = '___API___'; // Go to Google Developer Console and get an API key

// Channel ID
$channelId = '___CHANNEL_ID___'; // Channel ID you want to get videos of. Example: UCX6OQ3DkcsbYNE6H8uQQuVA (MrBeast)

// Maximum videos you want to get
$maxResults=1;
```
