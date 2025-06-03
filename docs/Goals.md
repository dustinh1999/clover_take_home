# Goals

We want to design a frontend architecture that is accessible, scalable, supports web & mobile, and works offline and online. 

Features we want to support:

* Real time dashboard: Contains information for all events that are performed by the towers  
* Auto discovery: Contains an API to automatically discover devices  
* Policy enforcement: Makes sure actions taken under an enterprise abide by the policies set by the enterprise  
* Auto-remedial action: Upon a policy being violated, automatically remediate with the correct course of action  
* Connect to different sources to onboard: The system should be able to connect to any source to onboard existing users

## Real Time Dashboard

The real time dashboard should contain all the information performed by the towers. When an API is executed by the tower, there should be an event log response. In this case, we call these LogEvents. 

### Offline vs Online

In the case of online, the real time dashboard will maintain a websocket that transfers the information from the tower immediately. This keeps it real time. Using a websocket maintains the performant API, as we keep the performance smooth and efficient.

In the case of offline, we can keep a cache of actions performed. While the dashboard is offline, it will display the latest snapshot of when it was online. It will maintain a cache of executable actions, and perform them once the system goes online again.

## Auto Discovery

There will be a Rest API to perform auto discovery. Since we want this to be performant and constant, we will use a websocket for this API. Upon locating a device for a specific enterprise, the API will be invoked and will send a DeviceDiscovered output to the real time dashboard or cache.

## Policy Enforcement and Auto-Remedial Action

Policy enforcement and auto remedial action goes hand in hand. The enterprises will have a POST API to set active policies. Once these are set, any user performed actions will be invoked via /user/action. The output of this API will trigger a websocket /security which will verify that no policies are violated. Otherwise, if there is a violated policy the remediation will automatically occur. 

## Connect to different sources to onboard

The API provided should allow different ways to onboard users into the system. This could include a variety of different methods, such as custom APIs, LDAP, among other methods. We specify a field sourceType which can be customized to several different methods in the API input.This allows the system to be flexible and performant as described.