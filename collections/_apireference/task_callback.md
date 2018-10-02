---
title: Task Callback
position: 10
request: /v1/task_token
main_message: In order to handle events for newly created, completed or any other tasks status changes on your server you may specify callback urls in your qencode account settings. Check parameters that are listed below.
attributes:
  - attribute: task_token
    required: required
    message: A task's token.
  - attribute: event
    required: required
    message: Name of the event, i.e. 'queued', 'saved' or 'error'
  - attribute: payload
    required: required
    message: Payload is passed by a client's application to <b style="color:#41c186;">start_encode</b> or <b style="color:#41c186;">start_encode2</b> methods.
  - attribute: error_code
    required: required
    message: Error code (only for error event).
  - attribute: error_message
    required: required
    message: Error's description (for error events only).

request_examples:
  - code_block: |2-
      {
        “task_token” : “1234567890”,
        “event” : “saved”,
        “payload” : “user data”
        "status" : {JSON-encoded string representing task status, see Getting task status}
      }
    language: curl
---