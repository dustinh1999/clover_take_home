# API Endpoints

The below API are expected to be performant. They return only the information specifically requested.

| Tower API  | Type | Description |
| :---- | :---- | :---- |
| /towers | GET | List of cell towers |
| /towers/register | POST | Registers cell tower (updates DB) |

| Devices API | Type | Description |
| :---- | :---- | :---- |
| /devices | GET | List of devices |
| /devices/register | POST | User can register devices. Contains input SourceType which can be varied depending on how the user is registering. |

| user | Type | Description |
| :---- | :---- | :---- |
| /user/action | POST | Generates a user action object which is later checked by the active policies |

| Policies | Type | Description |
| :---- | :---- | :---- |
| /policies | GET | List of policies |
| /policies/register | POST | Create a new policy |

| Enforce | Type | Description |
| :---- | :---- | :---- |
| /enforce | POST | Trigger all active policies to be enforced |

| Discover | Type | Description |
| :---- | :---- | :---- |
| /discover | Websocket | Auto-discover new device |

| Dashboard | Type | Description |
| :---- | :---- | :---- |
| /dashboard | Websocket | Get real-time events |

| security | Type | Description |
| :---- | :---- | :---- |
| /security | Websocket | Catch any security events that require additional input from towers |

