---
title: Getting Access Token
position: 16
request: /v1/create_token
main_message: This route is responsible for getting the access token.

request_examples:
  - code_block: |2-
      curl https://api.qencode.com/v1/access_token -d api_key=5a2a846a26ace 

    language: curl

response_examples: |2-
      {"error":0,"token":"1e1111fec48cc52060ca27312ed983ce","expire":"2018-09-03T14:01:56"}

    language: json
---