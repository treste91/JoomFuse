XML RPC API
===========

Contains the following functions :

dsQuery()
---------

Declaration: dsQuery($tableName, $searchFields, $returnFields)

Queries an IFS table with the provided data.

- Not currently used.


dsUpdate()
----------

Declaration: dsUpdate($tableName, $recordId ,$updateFields)

Updates an IFS table row with the provided data.

Currently, the `cancelSubscription() <https://joomfuse.readthedocs.io/en/latest/api/xml_rpc.html#cancelsubscription>`_ function calls this.


dsAdd()
-------

Declaration: dsAdd($tableName, $updateFields)

Creates an IFS table row with the provided data.

- Not currently used.


getProducts()
-------------

Declaration: getProducts()

Fetches all the entries from the IFS 'Product' table.

- Not currently used.


getDataFormTabs()
-----------------

Declaration: getDataFormTabs()

Fetches all the entries from the IFS 'DataFormTab' table.

Called by the getGroups() function of the JFormFieldJoomfuseIFSField class in order to list all the supported IFS field types.


getDataFormGroups()
-------------------

Declaration: getDataFormGroups()

Fetches all the entries from the IFS 'DataFormGroup' table.

Called by the getGroups() function of the JFormFieldJoomfuseIFSField class in order to list all the supported IFS field types.


getCustomFields()
-----------------

Declaration: getDataFormFields()

Fetches all the entries from the IFS 'DataFormField' table.

Called by the getGroups() function of the JFormFieldJoomfuseIFSField class in order to list all the supported IFS field types.


optIn()
-------

Declaration: optIn($email, $reason)

Called by the save() function of the IFSContact class in order to save all the contact information and related data to IFS.


assignTagToContact()
--------------------

Declaration: assignTagToContact($tagId, $contactId)

Assignes a specific IFS tag to a specific IFS contact.

Called by the:

- saveIFSTags() function of the IFSContact class in order to save the IFS Tags for a specific contact to IFS according to the add-tag lists created by assignIFSTag() and removeIFSTag() calls.

- httpPostFail() function of the IFSFactory class in order to perform the necessary steps (logging and error tag setting) when the http post is considered as failed.


removeTagFromContact()
----------------------

Declaration: removeTagFromContact($tagId, $contactId)

Removes a specific IFS tag to a specific IFS contact.

Called by the saveIFSTags() function of the IFSContact class in order to save the IFS Tags for a specific contact to IFS according to the remove-tag lists created by assignIFSTag() and removeIFSTag() calls.


getSubscriptionList()
---------------------

Declaration: getSubscriptionList()

Fetches all the entries from the IFS 'CProgram' table.

Called by the getOptions() function of the JFormFieldJoomfusesubscriptionproductlist class in order to create a field that lists all IFS actionsets in a select list.


getSubscriptionPlanList()
-------------------------

Declaration: getSubscriptionPlanList()

Fetches all the entries from the IFS 'SubscriptionPlan' table.

- Not currently used.

getSubscriptionListByIFSId()
----------------------------

Declaration: getSubscriptionListByIFSId($contactId)

Fetches all the entries from the IFS 'RecurringOrder' table.

Called by the getSubscriptionList() function of the IFSContact class in order to retrieve the the subscriptions list.


cancelSubscription()
--------------------

Declaration: cancelSubscription($recurringOrderId, $endDate, $reasonStopped)

Is called to cancel the subscription of a specific order.


getInvoicesByIFSId()
--------------------

Declaration: 


getActionSetList()
------------------

Declaration:


getJobsByIFSId()
----------------

Declaration:


runActionSet()
--------------

Declaration:


achieveGoal()
-------------

Declaration:


getTagList()
------------

Declaration:


getTagGroupList()
-----------------

Declaration:


getCreditCardsByIFSId()
-----------------------

Declaration:


getTagsByIFSId()
----------------

Declaration:


getComponentParams()
--------------------

Declaration:


getAPILocation()
----------------

Declaration:


getAPIKey()
-----------

Declaration:


getContactByEmail()
-------------------

Declaration:


getContactByIFSId()
-------------------

Declaration:


createContact()
---------------

Declaration:


updateContactById()
---------------------

Declaration:


testConnection()
----------------

Declaration:


testAPICredentials()
--------------------

Declaration:


getAppSettings()
----------------

Declaration:


validateNewCreditCard()
-----------------------

Declaration:


chargeInvoice()
---------------

Declaration:
