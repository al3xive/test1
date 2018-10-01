---
title: Adding logo/watermark
position: 3
request: /v1/create_token
main_message: This route is for adding logo or watermark to output video. An object describing logo / watermark should be inserted into “format” element.
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

    language: curl
  - code_block: |2-
      {
        "success": false,
        "result": null
      }
    language: curl
---