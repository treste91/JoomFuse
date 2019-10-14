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

Called by the getOptions() function of the JFormFieldJoomfusesubscriptionproductlist class in order to create a field that lists all IFS subscriptions in a select list.


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

Declaration: getInvoicesByIFSId($contactId)

Fetches all the entries from the IFS 'Invoice' table.

Called by the getInvoices() function of the IFSContact class in order to retrieve the the invoices list.


getJobsByIFSId()
----------------

Declaration: getJobsByIFSId($contactId)

Fetches all the entries from the IFS 'Job' table.

Called by the getJobs() function of the IFSContact class in order to retrieve the the jobs list.


getActionSetList()
------------------

Declaration: getInvoicesByIFSId($contactId)

Fetches all the entries from the IFS 'ActionSequence' table.

Called by the getOptions() function of the JFormFieldJoomfuseactionsetlist class in order to create a field that lists all IFS actionsets in a select list.


runActionSet()
--------------

Declaration: runActionSet($contactId, $actionsetId)

Runs an actionset.

Called by the runActionSet() function of the IFSContact class in order to run the specified actionset on this contact.


achieveGoal()
-------------

Declaration: achieveGoal($contactId, $callName, $integration)

Achieves a goal for a contact.

Called by the achieveGoal() function of the IFSContact class in order to achieve a goal for a contact.


getTagList()
------------

Declaration: getTagList()

Fetches all the entries from the IFS 'ContactGroup' table.

Called by the getGroups() function of the JFormFieldJoomfusetaglist class in order to create a field that lists all IFS tags in a select list.


getTagGroupList()
-----------------

Declaration: getTagGroupList()

Fetches all the entries from the IFS 'ContactGroupCategory' table.

Called by the getGroups() function of the JFormFieldJoomfusetaglist class in order to create a field that lists all IFS tags in a select list.


getCreditCardsByIFSId()
-----------------------

Declaration: getCreditCardsByIFSId($ifs_id)

Fetches all the entries from the IFS 'CreditCard' table.

Called by the getCreditCards() function of the IFSContact class in order to get all the credit card information assigned to a specific contact.


getTagsByIFSId()
----------------

Declaration: getTagsByIFSId($ifs_id)

Fetches all the entries from the IFS 'ContactGroupAssign' table.

Called by the:

- getIFSTags() function of the IFSContact class in order to get the list of IFS tags assigned to the spcific contact.

- parseHttpPost() function of the IFSFactory class in order to parse the http post based on the condition of the existence of a tag.


getComponentParams()
--------------------

Declaration: getComponentParams()

Retrieves the parameters of the JoomFuse component.

Called by the following functions of the IFSApi in order to retrieve the JoomFuse component parameters:

- getApiLocation()

- getApiKey()


getAPILocation()
----------------

Declaration: getApiLocation($testAppName)

Retrieves the location of the API.

Called by the following functions of the IFSApi in order to retrieve the location of the API:

- __getProducts()

- achieveGoal()

- assignTagToContact()

- chargeInvoice()

- createContact()

- deactivateCreditCard()

- dsAdd()

- dsUpdate()

- dsQuery()

- getActionsetList()

- getAppSettings()

- getContactByIFSId()

- getContactsByEmail()

- getCreditCardsByIFSId()

- getCustomFields()

- getDataFormGroups()

- getDataFormTabs()

- getInvoicesByIFSId()

- getJobsByIFSId()

- getSubscriptionList()

- getSubscriptionListByIFSId()

- getSubscriptionPlanList()

- getTagGroupList()

- getTagList()

- getTagsByIFSId()

- optIn()

- removeTagFromContact()

- runActionSet()

- testConnection()

- updateContactById()

- validateNewCreditCard()


getAPIKey()
-----------

Declaration: getAPIKey()

Retrieves the key of the API.

Called by the following functions of the IFSApi in order to retrieve the key of the API:

- __getProducts()

- achieveGoal()

- assignTagToContact()

- chargeInvoice()

- createContact()

- deactivateCreditCard()

- dsAdd()

- dsUpdate()

- dsQuery()

- getActionsetList()

- getAppSettings()

- getContactByIFSId()

- getContactsByEmail()

- getCreditCardsByIFSId()

- getCustomFields()

- getDataFormGroups()

- getDataFormTabs()

- getInvoicesByIFSId()

- getJobsByIFSId()

- getSubscriptionList()

- getSubscriptionListByIFSId()

- getSubscriptionPlanList()

- getTagGroupList()

- getTagList()

- getTagsByIFSId()

- optIn()

- removeTagFromContact()

- runActionSet()

- testConnection()

- updateContactById()

- validateNewCreditCard()


getContactByEmail()
-------------------

Declaration: getContactsByEmail($email)

Fetches all the entries from the IFS 'Contact' table assigned to a specific email.

Called by the locateIFSContact() function of the IFSContact class in order to locate a pre-existing contact by the given email and name and create it if it does not exist.


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
