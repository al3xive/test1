---
title: Creating Transcoding Task
position: 4
request: /v1/create_token
main_message: This route is for creating a transcoding task.
attributes:
  - attribute: token
    required: required
    message: b49e034d198262f1d5d15ed9f3cb8ee1

request_examples:
  - code_block: |2-
      curl https://api.qencode.com/v1/create_task -d token=76682314a86ed377730873394f8172f2 

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