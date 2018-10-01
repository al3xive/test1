---
title: Starting Transcoding Process with Custom Params
position: 10
request: /v1/create_token
main_message: This route is for starting transcoding process with custom parameters.

request_examples:
  - code_block: |2-
      curl https://api.qencode.com/v1/start_encode2 \
         -d task_token=b49e034d198262f1d5d15ed9f3cb8ee1 \
         -d payload="12345" \
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
                   "video_codec_parameters": {
                     "vprofile": "baseline",
                     "level": "31",
                     "coder": "0",
                     "flags2": "-bpyramid+fastpskip-dct8x8",
                     "partitions": "+parti8x8+parti4x4+partp8x8+partb8x8",
                     "directpred": "2",
                     "me_method": "hex"
                   },
                   "start_time": "10",
                   "duration": "20",
                   "audio_bitrate": "64",
                   "audio_sample_rate": "44100",
                   "audio_channels_number": "2"
                 }
               ]
             }
            }

    language: json

response_examples:
  - code_block: |-
      {"error":0,"status_url":"https:\/\/api.qencode.com\/v1\/status"}

    language: json
---