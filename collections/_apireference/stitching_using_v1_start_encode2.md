---
title: Stitching videos with /v1/start_encode2
position: 15
request: /v1/start_encode2
main_message: This route is for stitching videos using /v1/start_encode2 method.
attributes:
  - attribute: token
    required: required
    message: b49e034d198262f1d5d15ed9f3cb8ee1

request_examples:
  - code_block: |2-
      curl https://api.qencode.com/v1/start_encode2 \
      -d task_token=b49e034d198262f1d5d15ed9f3cb8ee1 \
      -d query='{"query": {
        "stitch": [
          {"url" : "https://nyc3.digitaloceanspaces.com/qencode2/stitching/batch3/A4070002.mp4"},
          {"url" : "https://nyc3.digitaloceanspaces.com/qencode2/stitching/batch3/A4070003.mp4", "start_time": "120.0", "duration": "60.57"}
        ],
        "format": [
          {
            "output": "mp4",
            "destination": {
                "url":"s3://s3-eu-west-2.amazonaws.com/qencode-test/stitch/4_clip.mp4",
                "key":"AKIAIKZIPSJ7SDAIWK4A",
                "secret":"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",
                "permissions": "public-read"
             },
            "file_extension": "mp4",
            "size": "640x360",
            "profile": "baseline",
            "level": "41"
            }
          ]
    language: curl

response_examples:
  - code_block: |2-
      {"error":0,"upload_url":"https:\/\/storage.qencode.com\/v1\/upload_file","task_token":"471272a512d76c22665db9dcee893409"}
    language: json
---