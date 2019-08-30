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

$parameter = [
    'id'=> $channelId,
    'part'=> 'contentDetails',
    'key'=> $API_Key
];
$channel_URL = $API_Url . 'channels?' . http_build_query($parameter);
$json_details = json_decode(file_get_contents($channel_URL), true);

$playlist=$json_details['items'][0]['contentDetails']['relatedPlaylists']['uploads'];

$parameter = [
    'part'=> 'snippet',
    'playlistId' => $playlist,
    'maxResults'=> $maxResults,
    'key'=> $API_Key
];
$channel_URL = $API_Url . 'playlistItems?' . http_build_query($parameter);
$json_details = json_decode(file_get_contents($channel_URL), true);


$my_videos = [];
foreach($json_details['items'] as $video){
	$my_videos[] = array('v_id'=>$video['snippet']['resourceId']['videoId'], 'v_link'=>'https://www.youtube.com/watch?v='.$video['snippet']['resourceId']['videoId'] , 'v_name'=>$video['snippet']['title'], 'v_date'=>$video['snippet']['publishedAt'], 'v_description'=>$video['snippet']['description'], 'v_thumbnail'=>$video['snippet']['thumbnails']['high']['url'], 'v_channel'=>$video['snippet']['channelId']);
}

foreach($my_videos as $video){
    if(isset($video)){
        // Looping through the videos -
        //
        // Video ID - $video['v_id']
        // Video Link - $video['v_link']
        // Video Name - $video['v_name']
        // Channel Name - $video['v_channel']
        // Video Publish Date - $video['v_date']
        // Video Description - $video['v_description']
        // Video Thumbnail Link - $video['v_thumbnail']

        // --------------------------------------------

        // Do Anything

        // --------------------------------------------

    }
}
```
