---
title: Adding logo/watermark
position: 13
request: /v1/create_token
main_message: This route is used for adding logo or watermark to an output video. An object that describes logo/watermark should be inserted into the <span class="q6-blue-text">“format”</span> element.
attributes:
  - attribute: token
    required: required
    message: b49e034d198262f1d5d15ed9f3cb8ee1

request_examples:
  - code_block: |2-
      "format": [
       {
        "output": "mp4",
         ...
          "logo": {
            "source": "https://yourserver.com/watermark.png",
            "x": 10,
            "y": 10
          }
        }
      ]
    language: curl

response_examples:
  - code_block: |2-
      {"error":0,"upload_url":"https:\/\/storage.qencode.com\/v1\/upload_file","task_token":"471272a512d76c22665db9dcee893409"}

    language: json
---