---
title: Uploading Video File
position: 5
request: https://master/v1/upload_file/task_token
main_message: This method uploads files using the <b style="color:#41c186;">tus</b> protocol for renewable uploads. Use this method for direct uploading your videos to the <span class="q6-blue-text">Qencode</span> servers (e.g. from your website or mobile application). Specify a direct URL using <b style="color:#41c186;">start_encode</b> method as a param to the already uploaded files (e.g. Amazon S3 storage).
attributes:
  - attribute: task_token
    required: required
    message: Task's token returns with <b style="color:#41c186;">create_task</b> method

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
<div style="border: .14vw solid #41c186; border-radius: .4vw; padding: 1vw 1.8vw; font-weight: 300; line-height: 1.6vw;">
    Please note that <b style="color:#41c186;">upload_file</b> method should be called for a host and returned with the <b style="color:#41c186;">create_task</b> method described above.
</div>