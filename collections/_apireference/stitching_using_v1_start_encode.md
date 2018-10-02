---
title: Stitching videos with /v1/start_encode
position: 14
request: /v1/start_encode2
main_message: This route is for stitching videos using /v1/start_encode method. The key thing here is using the <span class="q6-blue-text">“stitch”</span> parameter for <b>/v1/start_encode</b> method instead of a regular <span class="q6-blue-text">“uri”</span> and a <span class="q6-blue-text">“source”</span> query attribute for the <b>/v1/start_encode2</b> method. The same <b>JSON</b> array is used for both methods. Specify URLs for input videos to "stitch" array elements.
attributes:
  - attribute: token
    required: required
    message: b49e034d198262f1d5d15ed9f3cb8ee1

json_example:
    title: URLs' Stitching Examples formatted as a regular JSON and as an object.
    json: |2-
      [
        "https://yourserver.com/video1.mp4",
        "https://yourserver.com/video2.mp4",
        "https://yourserver.com/video3.mkv"
      ]
      --------
      [
        {
          "url": "https://yourserver.com/video1.mp4"
        }, 
        {
          "url": "https://yourserver.com/video2.mp4", 
          "start_time": "120.0", 
          "duration": "60.57"
        }
      ]

request_examples:
  - code_block: |2-
      curl https://api.qencode.com/v1/start_encode2 \
        -d task_token=b49e034d198262f1d5d15ed9f3cb8ee1 \
        -d stitch='[
            {"url" : "https://yourserver.com/video1.mp4"},
            {
             "url" : "https://yourserver.com/video2.mp4", 
             "start_time": "120.0", 
             "duration": "60.57"
            }
          ]’
        -d profiles=5a2a846a26e88
    language: curl

response_examples:
  - code_block: |2-
      {"error":0,"upload_url":"https:\/\/storage.qencode.com\/v1\/upload_file","task_token":"471272a512d76c22665db9dcee893409"}
    language: json
---