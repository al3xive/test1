---
title: Interval-based Thumbnails
position: 19
request: /v1/create_token
main_message: This method is responsible for creating an interval-based thumbnails. The example below demonstrates creation of 320x240 thumbnails at every 30 seconds of a video's timeline. Thumbnails and WebVTT file will be saved into the directory specified in the “url” attribute of “destination” object.

request_examples: 
  - code_block: |2-
      {
        "output" : "thumbnails",
        "destination": {
          "url":"s3://nyc3.digitaloceanspaces.com/qencode3/test/thumb/bbb/",
          "key":"abcde12345",
          "secret":"abcde12345",
          "permissions": "public-read"
        },
        "interval": 30,
        "width" : 320,
        "height" : 240
      }

    language: curl
  
  - code_block: |2-
      curl https://api.qencode.com/v1/start_encode2 \
        -d task_token=b49e034d198262f1d5d15ed9f3cb8ee1 \
        -d query='{"query": {
            "source": "https://nyc3.digitaloceanspaces.com/qencode/bbb_sunflower_1080p_60fps_normal_339mb.mp4",
            "format": [
              {
                "output": "mp4",
                "destination": {
                  "url":"s3://nyc3.digitaloceanspaces.com/qencode3/test/bbb.mp4",
                  "key":"abcde12345",
                  "secret":"abcde12345",
                  "permissions": "public-read"
                },
                "file_extension": "mp4",
                "size": "320x240",
                "duration": 60
              },
              {
               "output" : "thumbnails",
               "destination": {
                  "url":"s3://nyc3.digitaloceanspaces.com/qencode3/test/thumb/bbb/",
                  "key":"abcde12345",
                  "secret":"abcde12345",
                  "permissions": "public-read"
                },
                "interval": 30,
                "width" : 320,
                "height" : 240
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