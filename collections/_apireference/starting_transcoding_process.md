---
title: Starting Transcoding Process
position: 6
request: /v1/start_encode
main_message: This route is responsible for starting transcoding for an already uploaded file.
attributes:
  - attribute: task_token
    required: required
    message: Task token returned with <b style="color:#41c186;">create_task</b> method.
  - attribute: uri | stitch
    required: required
    message: Either <span class="q6-blue-text">uri</span> or <span class="q6-blue-text">stitch</span> param should be specified.<br> The <span class="q6-blue-text">uri</span> is responsible for defining a single video's URI, whether it's a video URL or ID returned with <b style="color:#41c186;">upload_file</b> method.<br> Use the <span class="q6-blue-text">stitch</span> param in order to combine several input videos into a single one. Stitch should be a json-list of URLs or video-objects. Specify <span class="q6-blue-text">start_time</span> and <span class="q6-blue-text">duration</span> while using an object form. Check the examples below.<br><code>["https://youserver.com/video1.mp4"<br>"https://youserver.com/video1.mp4",<br>"https://youserver.com/video2.mkv",<br>{"url":"https://yourserver.com/video3.mp4", "start_time":"100.0", "duration":"60.0"}]</code><br> The same video URL can be specified several times in a stitch array (e.g. to stitch different clips from the same video). In this case the original video will be downloaded only at once.
  - attribute: profiles
    required: required
    message: Comma-separated list of transcoding profile IDs.
  - attribute: transfer_method
    required: optional
    message: Transfer method ID
  - attribute: payload
    required: optional
    message: Any string with length of 1000 characters (max).<br> It might become handy if you need to pass your website's ID or any JSON object.
  - attribute: start_time
    required: optional
    message: Specifies the start time (in seconds) to begin video transcoding from. 
  - attribute: duration
    required: optional
    message: Specifies video fragment's duration (in seconds) to be transcoded.
  - attribute: output_path_variables
    required: optional
    message: JSON-encoded string that contains a dictionary (key-value pairs) of params for video or image output path/directory.<br> This refers to the Output path values specified in the transcoding profile for video or image settings. It can contain placeholders defined in curly braces, e.g. {myfilename} or {video_id}, where the actual values for them will be populated from <span class="q6-blue-text">output_path_variables</span> dictionary.<br> Check the examples below.<br><code>"Output path for video setting:"<br>output/mp4/{scene_id}/1080/video.mp4<br>"output_path_variables:"<br>{"scene_id":"12345"}<br> "Resulting video path:"<br>/output/mp4/12345/1080/video.mp4</code><br>Please note, that {uuid} and {index} values are generated by transcoding system though if specified in <span class="q6-blue-text">output_path_variables</span> it will override the system's values.

request_examples:
  - code_block: |2-
      curl https://api.qencode.com/v1/start_encode \
        -d task_token=63adfb01d408081b10440682f3a64114 \
        -d uri="https://qa.qencode.com/static/test_mini.mp4" \
        -d start_time=10 \
        -d duration=20 \
        -d profiles=5a2a846a26e88,5a2a846a28604 \
        -d transfer_method=5aa2875489681 \
        -d payload="12345" \
        -d output_path_variables='{"category":"test_videos","video_name":"12345"}'

    language: curl

response_examples:
  - code_block: |-
      {"error":0,"status_url":"https:\/\/api.qencode.com\/v1\/status"}

    language: json
---