---
title: Generating WebVTT for thumbnails
position: 20
request: query
main_message: There are two ways for generating thumbnail images for videos. WebVTT is a plain text format, part of the HTML5 standard. When used for thumbnails, the VTT files contain links to the actual thumbnail images, which can be in .JPG, .PNG or .GIF format.
attributes:
  - attribute: query
    required: required
    message: Source & Format are required

json_example:
    title: Example of JSON object for query with output format "thumbnails" for creating WebVTT file
    json: |2-
      {"query": {
          "source": "https://example.com/your_video.mp4",
          "format": [
            {
              "output": "mp4",
              ...
            },
             {
                "output" : "thumbnails",
                "destination": {
                  "url":"s3://s3-eu-west-2.amazonaws.com/bucket/...",
                  "key":"your_access_key",
                  "secret":"your_access_secret",
                  "permissions" : "public-read" //optional field
                },
                "interval": 30, //in seconds
                "width" : 320,
                "height" : 240
              }
          ]
        }
      }

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
      {
        “status_url” : “https://master-ed4971d0bd8811e481e104012ff1f701.qencode.com/v1/status”
      }
    language: json
---