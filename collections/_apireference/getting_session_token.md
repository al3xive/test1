---
title: Getting Session Token
position: 3
request: /v1/access_token
main_message: In order to access <span class="q6-blue-text">Qencode API</span> you should acquire a session token. You will be passing it as a param to <b style="color:#41c186;">create_task</b> method described below.
attributes:
  - attribute: api_key
    required: required
    message: An API access key obtained once registered at <span class="q6-blue-text">qencode.com</span> as a user.

response_examples:
  - code_block: |2-
      {
        “token” : “1357924680”,
        “expire” : “2017-12-31 23:59:59”
      }
    language: json
---
<div style="border: .14vw solid #41c186; border-radius: .4vw; padding: 1vw 1.8vw; font-weight: 300; line-height: 1.6vw;">
    To build secure solution we strongly recommend NOT to call this method directly from any
    client application of yours as you expose your api key to the world in this case. Recommended
    way is to obtain session token from your server and then pass to the client app.
</div>