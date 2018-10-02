---
title: Subtask Callback
position: 11
request: /v1/task_token
main_message: Subtask is a procedure of converting a video into the specified resolution in your transcoding profile. Subtask callback allows you to handle the following status changes:<br><ul><li><b>Converting</b> - encoding process has already been started for a subtask.</li><br><li><b>Converted</b> - encoding process was finished successfully for a subtask.</li><br><li><b>Saving</b> - output video is being saved to the required directory.</li><br><li><b>Saved</b> - output video was successfully saved to the required directory.</li><br><li><b>Error</b> - an error occured during processing the subtask.</li></ul><br> Check parameters that are listed below.
attributes:
  - attribute: subtasks
    required: required
    message: A list of subtasks there are updates for.
  - attribute: task_token
    required: required
    message: A task's token.
  - attribute: event
    required: required
    message: List of events since last update
  - attribute: payload
    required: required
    message: Payload is passed by a client's application to <b style="color:#41c186;">start_encode</b> or <b style="color:#41c186;">start_encode2</b> methods.
  - attribute: tag
    required: required
    message: Subtask's tag, specified in transcoding profile settings
  - attribute: error_code
    required: required
    message: Error code (only for error event).
  - attribute: error_message
    required: required
    message: Error's description (for error events only).

request_examples:
  - code_block: |2-
      {
        “subtasks”: [
            {
                “token” : “1234567890”,
                “events” : [“converting”, “converted”],
                “payload” : “user data”,
                “tag” : “720“
            },
            {
                “token” : “1234569090”,
                “events” : [“saving”, “saved”],
                “payload” : “user data”,
                “tag” : “480“
            }
        ]
      }
    language: curl
---