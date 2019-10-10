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

Declaration:


assignTagToContact()
--------------------

Declaration:


removeTagFromContact()
----------------------

Declaration:


getSubscriptionList()
---------------------

Declaration:


getSubscriptionPlanList()
-------------------------

Declaration:


getSubscriptionListByIFSId()
----------------------------

Declaration:


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
