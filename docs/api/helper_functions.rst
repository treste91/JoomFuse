Helper functions
================

The following functions are utilized in order to organize the API calls and ensure successful execution. 

IFS Contact
-----------

__construct()
^^^^^^^^^^^^^

Declaration: __construct($user_id)

The protected constructor of the IFSContact class. 

Called by the getInstanceByUserId() function of the IFSContact class to load the user data from the DB or create the contact in IFS.


setUserBeingDeleted()
^^^^^^^^^^^^^^^^^^^^^

Declaration: setUserBeingDeleted()

Sets the beingDleted property to true.

Called by the:

- onUserAfterDelete() of the PlgUserJoomfuse class in order to know not to update contact fields.

- save() function of the IFSContact class in order to avoid the contact field updates.


saveAllData()
^^^^^^^^^^^^^

Declaration: saveAllData()

Saves all information to IFS.

Called by the __destruct() function at the end of the page load of the PlgSystemJoomfuse class in order to have one point in the execution (as late as possible) where we have to decide what data to push to IFS.


save()
^^^^^^

Declaration: save()

Saves all the contact information to IFS.

This function is protected and only callable via the saveAllData() of the IFSContact class.


recreateIFSUsersTableRow()
^^^^^^^^^^^^^^^^^^^^^^^^^^

Declaration: recreateIFSUsersTableRow()

Re-creates the row of the 'IFSUser' table for the current user_id.

Called by the save() function of the IFSContact when a non-existent contact_id is detected in order to re-associated or re-create the IFS contact.


load()
^^^^^^

Declaration: load($user_id)

Loads the essentialy user data into the object. Notice that this function will also create a contact, if no association is found.

Called by the:

- __construct() function of the IFSContact class to load the user data.

- recreateIFSUsersTableRow() function of the IFSContact class to load the user data.


createUserContactAssociation()
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Declaration: createUserContactAssociation()

Creates the association between a user and the corresponding IFS contact.

Called by the load() function of the IFSContact class in order to create the association between the newly created IFS contact and the joomla user.


locateIFSContact()
^^^^^^^^^^^^^^^^^^

Declaration: locateIFSContact($email, $name)

Locates a pre-existing contact by the given email and name and creates it if it does not exist.

Called by the load() function of the IFSContact class in order to locate the IFS contact based on the provided email and name. If the contact does not exist, it is created.


getIFSTags()
^^^^^^^^^^^^

Declaration: getIFSTags($causesAPICall)

Gets the list of IFS tags assigned to the respective contact 

Called by the:

- hasIFSTagById() function of the IFSContact class in order to check whether this user has the specified IFS tag by its id.

- hasIFSTagByName() function of the IFSContact class in order to check whether this user has the specified IFS tag  by its name.

- saveIFSTags() function of the IFSContact class in order to save the IFS Tags for a specified contact to IFS.


assignIFSTag()
^^^^^^^^^^^^^^

Declaration: assignIFSTag($tagId)

Requests the assignement of a tag to this contact.

Called by the:

- parseHttpPost() of the IFSFactory class.

- mod_joomfusetrigger.php

- onContactUserDelete() function of the plgJoomfuseJoomla class.

- onJoomfuseAfterContactAssociation() function of the plgJoomfuseJoomla class.

- onJoomFuseBeforeContactSave() function of the plgJoomfuseJoomla class.

- onUserAfterSave() function of the PlgUserJoomfuse class.

- syncUserGroups() function of the PlgUserJoomfuse class.


removeIFSTag()
^^^^^^^^^^^^^^

Declaration: removeIFSTag($tagId)

Requests the disassociation of a tag to this contact.

Called by the:

- onContactUserDelete() function of the plgJoomfuseJoomla class.

- onJoomfuseAfterContactAssociation() function of the plgJoomfuseJoomla class.

- syncUserGroups() function of the PlgUserJoomfuse class.


hasIFSTagByName()
^^^^^^^^^^^^^^^^^

Declaration: hasIFSTagByName($tagName, $causesAPICall)

Checks to see on whether this user has the specified IFS tag (by tag name).

- Currently not used.


hasIFSTagById()
^^^^^^^^^^^^^^^

Declaration: hasIFSTagById($tagId, $causesAPICall)

Checks to see on whether this user has the specified Infusionsoft tag (by tag id).

Called by the:

- onPrepareACLDrop() of the PlgJoomfuseJoomla class in order to decide which user groups to remove from the user.

- onPrepareACLGrant() of the PlgJoomfuseJoomla class in order to decide which user groups to add to the user.

- syncUserGroups() of the PlgUserJoomfuse class in order to decide which user groups to add to the user.


saveIFSTags()
^^^^^^^^^^^^^

Declaration: saveIFSTags()

Saves the IFS Tags for this contact to infusionsoft according to the add/remove-tag lists created by assignIFSTag() and removeIFSTag() calls.

Called by the save() function of the IFSContact class in order to add/remove the appropriate IFS tags.


getInstanceByUserId()
^^^^^^^^^^^^^^^^^^^^^

Declaration: getInstanceByUserId($userid)

Returns a contact instance based on the provided user id.

Called by the:

- getUserContact() of the IFSContact class in order to retrieve the contact instance based on the provided user id.

- associateNextUserBatch() of the JoomfuseModelAssociateall class in order to retrieve the contact instance based on the provided user id.


getSubscriptionList()
^^^^^^^^^^^^^^^^^^^^^

Declaration: getSubscriptionList($causesAPICall)

Retrieves the subscriptions of the provided user.

- Currently not used.


getInvoices()
^^^^^^^^^^^^^

Declaration: getInvoices($causesAPICall)

Retrieves the invoices of the provided user.

- Currently not used.


getJobs()
^^^^^^^^^^^^^

Declaration: getJobs($causesAPICall)

Retrieves the jobs of the provided user.

Called by the getJob() function of the IFSContact class in order to retrieve a specific job of a specific user.


getJob()
^^^^^^^^^^^^^

Declaration: getJob($jobId, $causesAPICall)

Retrieves a specific job of the provided user.

- Currently not used.


runActionSet()
^^^^^^^^^^^^^^

Declaration: runActionSet($actionsetId, $causesAPICall)

Runs the specified actionset on this contact.

- Currently not used.


achieveGoal()
^^^^^^^^^^^^^

Declaration: achieveGoal($callName, $integration, $causesAPICall)

Runs the specified actionset on this contact.

Called by the parseHttpPost() function of the IFSFactory class in order to run the specified actionset.


getCreditCards()
^^^^^^^^^^^^^^^^

Declaration: getCreditCards($causesAPICall)

Gets all the credit card information assigned to this contact.

- Currently not used.


OptIn()
^^^^^^^

Declaration: OptIn($message)

Requests that the contact will be opted in.

Called by the:

- onJoomfuseAfterContactAssociation() function of the PlgJoomfuseJoomla class in order to address the opt-ins.

- onUserAfterSave() function of the PlgUserJoomfuse class in order to opt-in new users.




IFS Factory
-----------


getUserContact()
^^^^^^^^^^^^^^^^

Declaration: getUserContact($id)

Get the IFSContact for the optionally provided user id (defaults to current user).

Called by the:

- associateContactForUserId() function of the JoomfuseControllerMain class.

- getPluginUserGroups() function of the IFSFactory class.

- parseHttpPost() function of the IFSFactory class.

- mod_joomfusetrigger.php

- onContactUserDelete() function of the plgJoomfuseJoomla class.

- onJoomFuseBeforeContactSave() function of the plgJoomfuseJoomla class.

- replaceShortcodes() function of the PlgSystemJoomfuse class.

- onUserAfterDelete() function of the PlgUserJoomfuse class.

- onUserAfterSave() function of the PlgUserJoomfuse class.

- onUserBeforeDelete() function of the PlgUserJoomfuse class.

- onUserBeforeSave() function of the PlgUserJoomfuse class.

- onUserLogin() function of the PlgUserJoomfuse class.


isParsingHttpPost()
^^^^^^^^^^^^^^^^^^^

Declaration: isParsingHttpPost()

Checks if we're currently parsing an HTTP POST.

Called by the:

- onUserAfterSave() function of the PlgUserJoomfuse class.

- onUserBeforeSave() function of the PlgUserJoomfuse class.


getFieldMappings()
^^^^^^^^^^^^^^^^^^^

Declaration: getFieldMappings()

Retrieves the appropriate field mappings.

Called by the getContactByIFSId() function of the IFSApi class to retrieve the field mappings.


contactIdBeingProcessed()
^^^^^^^^^^^^^^^^^^^^^^^^^

Declaration: contactIdBeingProcessed($is_id)

Signals the beginning of the HTTP Post parsing of the given IFS id.

Called by the parseHttpPost() function of the IFSFactory class.


contactIdEndsProcess()
^^^^^^^^^^^^^^^^^^^^^^

Declaration: contactIdEndsProcess($is_id)

Signals the end of the HTTP POST process so other posts can work on the same contact id.

Called by the parseHttpPost() function of the IFSFactory class.


parseHttpPost()
^^^^^^^^^^^^^^^

Declaration: parseHttpPost()

Parses Infusionsoft HTTP POSTs.

Called by the function display() of the JoomfuseViewJoomfuse class.


registerUser()
^^^^^^^^^^^^^^

Declaration: registerUser($ifs_contact)

Registers a new user according to the given contact object.

Called by the parseHttpPost() function of the IFSFactory class.


httpPostFail()
^^^^^^^^^^^^^^

Declaration: httpPostFail($message, $contactId)

Performs the necessary steps (logging and error tag setting) when the http post is considered as failed.

Called by the parseHttpPost() function of the IFSFactory class.


mailUser()
^^^^^^^^^^

Declaratoion: mailUser($topic, $subject, $email)

Generic function to email users messages generated from the HTTP POST

Called by the registerUser() function of the IFSFactory class.


mailAdmin()
^^^^^^^^^^^

Declaration: mailAdmin($topic,$body)

Email admin users for any registration errors.

Called by the:

- registerUser() function of the IFSFactory class.

- mailUser() function of the IFSFactory class.


logError()
^^^^^^^^^^

Declaration: logError($message, $level)

Performs logging for the component. Will only create log entries in the /log/com_joomfuse.txt file if the debug option LOG is enabled.

Called by numerous function throughout the JoomFuse component and the associated plugins and modules.


getPluginUserGroups()
^^^^^^^^^^^^^^^^^^^^^

Declaration: getPluginUserGroups($ifs_user, $isNew , $remove, $addGroups)

Requests the joomfuse plugin to decide on which user groups they want to assign (or drop) to the given user.

Called by the parseHttpPost() function of the IFSFactory class.


getUserByIFSId()
^^^^^^^^^^^^^^^^

Declaration: getUserByIFSId($ifs_id)

Retrieves a user by the given ifs_id.

Called by the 

- parseHttpPost() function of the IFSFactory class.

- getDeleteResult() function of the JoomFuseModelDeleteUser class.


getUserByEmailAndName()
^^^^^^^^^^^^^^^^^^^^^^^

Declaration: getUserByEmailAndName($search_email, $search_name)

Retrieves a user by the given email and name.

Called by the parseHttpPost() function of the IFSFactory class.


getNameByFLName()
^^^^^^^^^^^^^^^^^

Declaration: getNameByFLName($fname, $lname)

Extrapolates the name of a user based on the first and last name.

Called by the 

- parseHttpPost() function of the IFSFactory class.

- registerUser() function of the IFSFactory class.

- onSetJoomlaFieldsFromContact() function of the plgJoomfuseJoomla class.


getFirstNameFromName()
^^^^^^^^^^^^^^^^^^^^^^

Declaration: getFirstNameFromName($name)

Returns the First Name part from a full name.

Called by the getJoomFuseContactFields() function of the plgJoomfuseJoomla class.


getLastNameFromName()
^^^^^^^^^^^^^^^^^^^^^

Declaration: getLastNameFromName($name)

Returns the Last Name part from a full name.

Called by the getJoomFuseContactFields() function of the plgJoomfuseJoomla class.


getNamePart()
^^^^^^^^^^^^^

Declaration: getNamePart($name, $lastName)

Returns either the first or the last name given a name. Helper function for implementing getFirstNameFromName and getLastNameFromName.

Called by the 

- getFirstNameFromName() function of the IFSFactory class.

- getLastNameFromName() function of the IFSFactory class.


scheduleCron()
^^^^^^^^^^^^^^

Declaration: scheduleCron($date, $handler, $params)

Schedule the execution of a cronjob.

- Currently not used.


cronCheck()
^^^^^^^^^^^

Declaration: cronCheck()

Checks the cron table for any pending cronjobs and triggers events for their execution.

Called by the:

- display() function of the JoomfuseViewCron class.

- __construct() function of the PlgSystemJoomfuse class.

