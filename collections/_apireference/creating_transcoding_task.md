---
title: Creating Transcoding Task
position: 4
request: /v1/create_task
main_message: This method requests a file's uploading endpoint from the <span class="q6-blue-text">Qencode</span> service.
attributes:
  - attribute: token
    required: required
    message: Session's token returns with <b style="color:#41c186;">access_token</b> method

request_examples:
  - code_block: |2-
      curl https://api.qencode.com/v1/create_task \
        -d token=76682314a86ed377730873394f8172f2 
    language: curl

response_examples:
  - code_block: |2-
      {"error":0,"upload_url":"https:\/\/storage.qencode.com\/v1\/upload_file","task_token":"471272a512d76c22665db9dcee893409"}
    language: json
---