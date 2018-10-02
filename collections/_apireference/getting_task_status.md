---
title: Getting Task Status
position: 9
request: /v1/status or https://master/v1/status
main_message: This method returns status of one or more transcoding tasks. Response contains status and percent params indicating current task state and progress. Possible values of task status are listed below.
attributes:
  - attribute: /v1/task_tokens
    required: required
    message: A list of task tokens

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
  
response_examples:
  - code_block: |2-
      {
            "error": 0, 
            "statuses": {
                "a2600fc63e4511e8ac870202b56d93e3": {
                    "status": "completed", 
                    "percent": 100, 
                    "error": 0, 
                    "error_description": null, 
                    "images": [
                        {
                            "tag": "image-0-0", 
                            "profile": "5a5db6fa5b8ac", 
                            "user_tag": "320x240/5", 
                            "storage": {
                                "bucket": "qencode-test", 
                                "type": "amazon_s3", 
                                "key": "output/320x240/12345_0.png", 
                                "format": null
                            }, 
                            "url": "https://s3.amazonaws.com/qencode-test/output/320x240/12345_0.png"
                        }, 
                        {
                            "tag": "image-1-0", 
                            "profile": "5a5db6fa5b8ac", 
                            "user_tag": "320x240/15", 
                            "storage": {
                                "bucket": "qencode-test", 
                                "type": "amazon_s3", 
                                "key": "output/320x240/12345_1.png", 
                                "format": null
                            }, 
                            "url": "https://s3.amazonaws.com/qencode-test/output/320x240/12345_1.png"
                        }
                    ], 
                    "videos": [
                        {
                            "tag": "video-0-0", 
                            "profile": "5a5db6fa5b8ac", 
                            "user_tag": "480p", 
                            "storage": {
                                "bucket": "qencode-test", 
                                "type": "amazon_s3", 
                                "key": "Outbound/480/12345.mp4", 
                                "format": "mp4"
                            }, 
                            "url": "https://s3.amazonaws.com/qencode-test/output/480/12345.mp4", 
                            "bitrate": 1692, 
                            "meta": "{\"width\": 854, \"resolution\": 480, \"height\": 480}", 
                            "duration": "0.371511"
                        }
                    ]
                }
            }
        }
    language: json

  - code_block: |2-
      {"error":0,"upload_url":"https:\/\/storage.qencode.com\/v1\/upload_file","task_token":"471272a512d76c22665db9dcee893409"}
    language: json
---
<div style="border: .14vw solid #41c186; border-radius: .4vw; padding: 1vw 1.8vw; font-weight: 300; line-height: 1.6vw;">
    Please note that status method should be called for a master host returned with the start_encode or start_encode2 methods described above.<br> 
    In case master host is down and you get timeouts run this method against api.qencode.com host.
</div>

<section>
  <hr>
  <table class="text-gray">
    <thead>
      <tr>
        <th style="padding-left: 10px;">Value</th>
        <th style="padding-left: 15px;">Description</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td style="padding-left: 9px;padding-top: 10px;">Downloading</td>
        <td style="padding-left: 15px;padding-top: 10px;">Video is being downloaded to Qencode server.</td>
      </tr>
      <tr>
        <td style="padding-left: 9px;padding-top: 10px;">Queued</td>
        <td style="padding-left: 15px;padding-top: 10px;">Task is waiting for available encoders.</td>
      </tr>
      <tr>
        <td style="padding-left: 9px;padding-top: 10px;">Encoding</td>
        <td style="padding-left: 15px;padding-top: 10px;">Video is being transcoded.</td>
      </tr>
      <tr>
        <td style="padding-left: 9px;padding-top: 10px;">Saving</td>
        <td style="padding-left: 15px;padding-top: 10px;">Video is being saved to destination location (e.g. Amazon S3 bucket).</td>
      </tr>
      <tr>
        <td style="padding-left: 9px;padding-top: 10px;">Completed</td>
        <td style="padding-left: 15px;padding-top: 10px;">Video was saved to destination location. Transcoding job has completed successfully.</td>
      </tr>
    </tbody>
  </table>
</section>