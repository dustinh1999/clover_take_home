# Entity Modeling

Carrier

* Id  
* Name

Tower

* Id  
* Carriers   
* OS 

Device

* Id  
* OS  
* Carrier  
* Subscription

LogEvent

* DeviceDiscovered  
* PolicyEnforcedAction

DeviceDiscovered

* Device  
* Timestamp

GenericAction

* Id  
* Device  
* ActionType  
* Timestamp  
* Status

PolicyEnforcedAction

* GenericAction  
* Enforcement