# About Updating the DNC List with New Numbers

Maintaining an up-to-date internal Do Not Call (DNC) list is essential if you want your call center to remain compliant.  For example, you might add a new number to this internal DNC list programmatically if the number for being placed on the DNC list is coming from a different source (like a web form).

### Request

Be sure to set the proper [BASE_URL](../../basics/uris.md#resources-and-parameters) and [authorization header](../../authentication/auth-ringcentral.md) for your deployment.

=== "HTTP"
    ```bash
    POST {BASE_URL}/api/v1/admin/accounts/{accountId}/dncLists
    Authorization: bearer <myAccessToken>
    Content-Type: application/json;charset=UTF-8
    ```

=== "Node JS"
    ```javascript
    /****** Install Node JS SDK wrapper *******
    $ npm install ringcentral-engage-voice-client
    *******************************************/

    const RunRequest = async function () {
        const EngageVoice = require('ringcentral-engage-voice-client').default

        // Instantiate the SDK wrapper object with your RingCentral app credentials
        const ev = new EngageVoice({
            clientId: "RINGCENTRAL_CLIENTID",
            clientSecret: "RINGCENTRAL_CLIENTSECRET"
        })

        try {
            // Authorize with your RingCentral Office user credentials
            await ev.authorize({
                username: "RINGCENTRAL_USERNAME",
                extension: "RINGCENTRAL_EXTENSION",
                password: "RINGCENTRAL_PASSWORD"
            })

            // Add a new DNC number
            const postBody = {
                "dncTag": {
                    "dncTagId": 0,
                    "dncTagLabel": "GLOBAL"
                },
                "countryCode": {
                    "id": "USA"
                },
                "phone": "5105550100",
                "reason": "Did not want to be called",
                "tag": "GLOBAL",
                "dncTagId": 0
            }
            const response = await ev.post('/api/v1/admin/accounts/{accountId}/dncLists', postBody)
            console.log(response.data);
        }
        catch (err) {
            console.log(err.message)
        }
    }

    RunRequest();
    ```
=== "Python"
    ```python
    #### Install Python SDK wrapper ####
    # $ pip3 install ringcentral_engage_voice
    #  or
    # $ pip install ringcentral_engage_voice
    #####################################
    
    from ringcentral_engage_voice import RingCentralEngageVoice
    
    def add_dnc_number():
        try:
            postBody = {
                "dncTag":{
                  "dncTagId":0,
                  "dncTagLabel":"GLOBAL"
                },
                "countryCode":{
                  "id":"USA"
                },
                "phone":"5105550134",
                "reason":"Did not want to be called",
                "tag":"GLOBAL",
                "dncTagId":0
            }
            response = ev.post("/api/v1/admin/accounts/{accountId}/dncLists", postBody).json()
            print(response)
        except Exception as e:
            print(e)
    
    
    # Instantiate the SDK wrapper object with your RingCentral app credentials
    ev = RingCentralEngageVoice(
        "RINGCENTRAL_CLIENTID",
        "RINGCENTRAL_CLIENTSECRET")
    
    try:
        # Authorize with your RingCentral Office user credentials
        ev.authorize(
            username="RINGCENTRAL_USERNAME",
            password="RINGCENTRAL_PASSWORD",
            extension="RINGCENTRAL_EXTENSION"
        )
    
        add_dnc_number()
    except Exception as e:
        print(e)
    ```

=== "Request Body"
    ```json    
    {
      "dncTag":{
        "dncTagId":0,
        "dncTagLabel":"GLOBAL"
      },
      "countryCode":{
        "id":"USA"
      },
      "phone":"5105550100",
      "reason":"Did not want to be called",
      "tag":"GLOBAL",
      "dncTagId":0
    }
    ```

### Primary Parameters

To add a number to the DNC list, send a JSON request body with the following notable parameters. See the example below for more.

  | API Property | Description |
  |-|-|
  | **`dncTag.dncTagId`** | set to `GLOBAL`. |
  | **`countryCode.id`** | set to your country, typically `USA`. |
  | **`phone`** | The number to be placed on the Do Not Call list. |
  | **`reason`** | A short description for why this number is being added to the DNC list. |
  | **`tag`** | set to `GLOBAL`. |

### Response

Once added, the DNC number is recorded to the list along with the name of the agent/admin entering the number and a date for when the number was added to the list.

=== "JSON"
    ```json
    {
      "phone":"5105550100",
      "tag":"GLOBAL",
      "countryCode":{
        "id":"USA",
        "description":null
      },
      "addedDate":"2020-11-03T18:10:11.740+0000",
      "addedBy":"Craig Chan",
      "reason":"Did not want to be called",
      "dncTagId":0
    }
    ```

### Primary Fields

When a number is aded to the DNC list, two fields are automatically added as well.

  | API Property | Description |
  |-|-|
  | **`addedDate`** | This date and time are added automatically to the list. |
  | **`addedBy`** | This field is automatically added to the list as the person executing the API. |
