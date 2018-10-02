---
title: Error Codes
position: 2
main_message: Below is an <b>Error Codes</b> table for the <span class="q6-blue-text">Qencode API</span>.

---
<section>
    <hr>
    <table class="text-gray">
        <thead>
          <tr>
              <th>ERROR CODE</th>
              <th style="padding-left: 10px;">VALUE</th>
              <th style="padding-left: 20px;">DESCRIPTION</th>
          </tr>
        </thead>
        <tbody>
          <tr>
              <td style="padding-top: 10px;">ERROR_OK</td>
              <td style="padding-left: 29px;padding-top: 10px;">0</td>
              <td style="padding-left: 20px;padding-top: 10px;">Operation completed successfully</td>
          </tr>
          <tr>
              <td style="padding-top: 10px;">ERROR_SERVER_INTERNAL</td>
              <td style="padding-left: 29px;padding-top: 10px;">1</td>
              <td style="padding-left: 20px;padding-top: 10px;">Internal server error occurred. Please contact support in this case.</td>
          </tr>
          <tr>
              <td style="padding-top: 10px;">ERROR_BAD_API_KEY</td>
              <td style="padding-left: 29px;padding-top: 10px;">2</td>
              <td style="padding-left: 20px;padding-top: 10px;">Your API key does not pass validation.</td>
          </tr>
          <tr>
              <td style="padding-top: 10px;">ERROR_API_KEY_NOT_FOUND</td>
              <td style="padding-left: 29px;padding-top: 10px;">3</td>
              <td style="padding-left: 20px;padding-top: 10px;">We can't find such API key in our database.</td>
          </tr>
          <tr>
              <td style="padding-top: 10px;">ERROR_BAD_TOKEN</td>
              <td style="padding-left: 29px;padding-top: 10px;">4</td>
              <td style="padding-left: 20px;padding-top: 10px;">Token does not pass validation.</td>
          </tr>
          <tr>
              <td style="padding-top: 10px;">ERROR_TOKEN_NOT_FOUND</td>
              <td style="padding-left: 29px;padding-top: 10px;">5</td>
              <td style="padding-left: 20px;padding-top: 10px;">We can't find such token in our database</td>
          </tr>
          <tr>
              <td style="padding-top: 10px;">ERROR_SERVICE_SUSPENDED</td>
              <td style="padding-left: 29px;padding-top: 10px;">6</td>
              <td style="padding-left: 20px;padding-top: 10px;">Service suspended. There can be different reasons for that, e.g. you are using Free plan and 500 minutes limit is reached,
                  or you have an outstanding invoice not paid. In case you are not sure what's the reason please contact support.
              </td>
          </tr>
          <tr>
              <td style="padding-top: 10px;">ERROR_MASTER_NOT_FOUND</td>
              <td style="padding-left: 29px;padding-top: 10px;">7</td>
              <td style="padding-left: 20px;padding-top: 10px;">Server issue. Please contact support in this case.</td>
          </tr>
          <tr>
              <td style="padding-top: 10px;">ERROR_SYSTEM_BUSY</td>
              <td style="padding-left: 29px;padding-top: 10px;">8</td>
              <td style="padding-left: 20px;padding-top: 10px;">We don't have enough resources to process request at the moment. You should retry it in a number of seconds specified in response.</td>
          </tr>
          <tr>
              <td style="padding-top: 10px;">ERROR_BAD_PAYLOAD</td>
              <td style="padding-left: 29px;padding-top: 10px;">9</td>
              <td style="padding-left: 20px;padding-top: 10px;">Payload value is too long.</td>
          </tr>
          <tr>
              <td style="padding-top: 10px;">ERROR_PROJECT_NOT_FOUND</td>
              <td style="padding-left: 29px;padding-top: 10px;">10</td>
              <td style="padding-left: 20px;padding-top: 10px;">Server issue. Please contact support in this case.</td>
          </tr>
          <tr>
              <td style="padding-top: 10px;">ERROR_BAD_PROFILE</td>
              <td style="padding-left: 29px;padding-top: 10px;">11</td>
              <td style="padding-left: 20px;padding-top: 10px;">Profile field value does not pass validation.</td>
          </tr>
          <tr>
              <td style="padding-top: 10px;">ERROR_PROFILE_NOT_FOUND</td>
              <td style="padding-left: 29px;padding-top: 10px;">12</td>
              <td style="padding-left: 20px;padding-top: 10px;">We can't find specified profile in our database.</td>
          </tr>
          <tr>
              <td style="padding-top: 10px;">ERROR_BAD_TOKENS</td>
              <td style="padding-left: 29px;padding-top: 10px;">13</td>
              <td style="padding-left: 20px;padding-top: 10px;">Task_tokens field value does not pass validation.</td>
          </tr>
          <tr>
              <td style="padding-top: 10px;">ERROR_FIELD_REQUIRED</td>
              <td style="padding-left: 29px;padding-top: 10px;">14</td>
              <td style="padding-left: 20px;padding-top: 10px;">Value for field specified in response is required in request.</td>
          </tr>
        </tbody>
    </table>
    <hr>
</section>