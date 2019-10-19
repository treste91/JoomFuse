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





IFS Factory
-----------
