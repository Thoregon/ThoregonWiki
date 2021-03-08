Thoregon Collaboration
======================

## REST API's

### CollaborationChannel

#### Create


    POST https://apps.thoregon.io/collaboration/channel
        Header: '' : 'thoregon <jwt>'
        Body: {
            "name": "channel",
            "description": "desctiption",
            "set": "SET" 
        }

    Result (Body): {
            "name": "channel",
            "description": "desctiption",
            "set": "SET",
            "id": "qFs5VzJGghdDfgjfiUhhKz1w",
            "state": "active"
        }
    
#### Get

    GET https://apps.thoregon.io/collaboration/channel/:id  (replace :id with the channel id)
        Header: '' : 'thoregon <jwt>'

    Result (Body): {
            "name": "channel",
            "description": "desctiption",
            "set": "SET",
            "id": "qFs5VzJGghdDfgjfiUhhKz1w",
            "state": "active"
        }

#### Modify

Modify also activates the channel if it was inactive. 
To just activate a channel omit params

    PUT https://apps.thoregon.io/collaboration/channel/:id  (replace :id with the channel id)
        Header: '' : 'thoregon <jwt>'
        Body: {
            "name": "channel name"
        }

    Result (Body): {
            "name": "channel name",
            "description": "desctiption",
            "set": "SET",
            "id": "qFs5VzJGghdDfgjfiUhhKz1w",
            "state": "active"
        }

#### Deactivate


    DELETE https://apps.thoregon.io/collaboration/channel/:id  (replace :id with the channel id)
        Header: '' : 'thoregon <jwt>'

    Result (Body): {
            "name": "channel name",
            "description": "desctiption",
            "set": "SET",
            "id": "qFs5VzJGghdDfgjfiUhhKz1w",
            "state": "inactive"
        }
