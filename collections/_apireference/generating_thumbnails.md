---
title: Generating Thumbnails
position: 18
request: /v1/create_token
main_message: This route is responsible for generating thumbnails. There are two ways of thumbnails creation in Qencode API:<ul><li>Generate individual thumbnail by capturing the specific time range on a timeline (specified in % of overall video length)</li><br><li>Create a general thumbnail based on the interval value between each thumbnail that is specified in seconds.<br> In this case the <a href="https://www.w3.org/TR/webvtt1/" target="_blank">WebVTT</a> file is being generated seamlessly.</li></ul>
request_examples:
  - code_block: |2-
      {
        "output": "thumbnail",
        "time": "0.15",
        "width": "920",
        "height": "500",
        "destination": "",
        "user_tag": "15_920x500"
      }

    language: curl
  
  - code_block: |2-
      curl https://api.qencode.com/v1/start_encode2 \
        -d task_token=b49e034d198262f1d5d15ed9f3cb8ee1 \
        -d query='{"query": {
        "source": "https://qa.qencode.com/static/test_mini.mp4",
        "format": [
             {
                    "output": "mp4",
                    "destination": {
                      "url":"s3://nyc3.digitaloceanspaces.com/qencode3/test/test_mini.mp4",
                      "key":"abcde12345",
                      "secret":"abcde12345",
                      "permissions": "public-read"
                    },
                     "framerate": "29.97",
                     "keyframe": "25",
                     "file_extension": "mp4",
                     "size": "360x240",
                     "start_time": "10",
                     "duration": "20"
                   },
                   {
                     "output": "thumbnail",
                     "time": "0.15",
                     "width": "320",
                     "height": "240",
                     "destination": {
                       "url":"s3://nyc3.digitaloceanspaces.com/qencode3/test/thumb/15_320x240.png",
                       "key":"abcde12345",
                       "secret":"abcde12345",
                       "permissions": "public-read"
                      },
                     "user_tag": "15_320x240"
                    },
                   {
                     "output": "thumbnail",
                     "time": "0.50",
                     "width": "320",
                     "height": "240",
                     "destination": {
                       "url":"s3://nyc3.digitaloceanspaces.com/qencode3/test/thumb/50_320x240.png",
                       "key":"abcde12345",
                       "secret":"abcde12345",
                       "permissions": "public-read"
                      },
                     "user_tag": "50_320x240"
                    }
                  ]
                }
              }

    language: curl

response_examples:
  - code_block: |2-
      {"error":0,"upload_url":"https:\/\/storage.qencode.com\/v1\/upload_file","task_token":"471272a512d76c22665db9dcee893409"}
    language: json
---
