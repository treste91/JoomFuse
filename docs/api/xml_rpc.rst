XML RPC API
===========

The following events of the “joomfuse” group are being thrown:

onContactUserDelete  
-------------------

Declaration: onContactUserDelete(array $userProperties)

Triggered from plg_user_joomfuse while catching the vanilla joomla user.onUserAfterDelete($user, $success, $msg) event. The contents of the $userProperties are the contents of the $user array. Please note that the event is not being thrown if $success is false. 

//@TODO: We currently have numerous issues stemming from the IFSContact/IFSFactory object caching that manifest from the recipients of this event.

Currently, plg_joomfuse_jomsocial and plg_joomfuse_joomla catch this event

onJoomFuseBeforeContactSave
---------------------------

Declaration: onJoomFuseBeforeContactSave($userid, array $initialContactFields, array $finalContactFields)

Triggered from the JF Core IFSContact class, it signifies the start of the consideration process for pushing data to Infusionsoft. At the current form, there is no direct indication on whether any data will be pushed to IFS and we can expect one such call for each intercepted user/contact that was accessed during the pageload. This event can interrupt the contact update process by throwing an Exception.

Currently plg_joomfuse_joomla catches this event in order to (optionally) push the frontEndUserChangeTag to IFS, if configured so.

OnJoomFuseAfterContactSave
--------------------------

Declaration: OnJoomFuseAfterContactSave($userid, array $initialContactFields, array $finalContactFields)

Triggered from the JF Core IFSContact class. It signifies that the core has finished considering sending to IFS, and possibly doing so, contact data for the specified user/contact.

Currently no plugins catch and utilize this event

OnJoomFuseBeforeContactAssociation
----------------------------------

Declaration: OnJoomFuseBeforeContactAssociation($userid, $contactid)

Triggered from the JF Core IFSContact class, it signifies that a user/contact association is about to be created.

Currently no plugins catch and utilize this event.

OnJoomFuseAfterContactAssociation
---------------------------------

Declaration: OnJoomFuseAfterContactAssociation($userid, $contactid)

Triggered from the JF Core IFSContact class, it signifies that a user/contact association has been created.

Currently plg_joomfuse_joomla and plg_joomfuse_jomsocial utilize this event to add/remove tags according to the (vanilla Joomla or JomSocial) group/tag associations they track.

OnIFSHTTPPostStart
------------------

Declaration: OnIFSHTTPPostStart()

Triggered from the JF Core IFSFactory when an HTTP POST is beginning execution. Simply signals the beginning of the http post process and does not expect any return values.

Currently no plugins catch and utilize this event

OnIFSHTTPPostComplete
---------------------

Declaration: OnIFSHTTPPostComplete(array $userProperties, $isNew)

Triggered from the JF Core IFSFactory when an HTTP POST has completed execution. Simply signals the end of the http post process and does not expect any return values.

Currently no plugins catch and utilize this event.

GetCustomFieldMappings
----------------------

Declaration: JoomfusefieldMapping GetCustomFieldMappings()

Triggered from the JF Core (IFSFactory::getFieldMappings()) to provide the “list of IFS fields we’re working with” (and an uncalled-for call from the shortcodefields view model that simply needs to use the core) when we need to figure out what custom fields each JF extension is utilizing. 

As expected, all our supported 3rd party extensions utilize this call:  plg_joomfuse_jooma, plg_joomfuse_jomsocial and plg_joomfuse_communitybuilder.

OnPrepareACLGrant
-----------------

Declaration: Int[] OnPrepareACLGrant(IFSContact $ifs_contact, $isNew)

Triggered from the JF Core during the http post parsing when trying to decide if we need to modify the usergroups of the J user. The return array contains ints of the respective J usergroups we want the user to be added to.

OnPrepareACLDrop
----------------

Declaration: Int[] OnPrepareACLDrop(IFSContact $ifs_contact, int[] $addedGroups, $isNew)

Triggered from the JF Core during the http post parsing when trying to decide if we need to modify the usergroups of the J user. The $addedGroups params contains the groups that all the plugins across the platform have requested to add on the OnPrepareACLGrant call made previously. The returned array is an array of ints that signify the J usergroup id that this plugin wants to have the contact as a part of. Please note that even if a plugin requests the participation to a usergroup, that might end up being rejected due to another (or the same) plugin requesting the same usergroup to not be present (removals take precedence). 

Currently only plg_joomfuse_joomla utilize this API call.

onCustomUserRegistration
------------------------

Declaration: onCustomUserRegistration($ifs_contact)

Triggered from the JF Core HTT POST parser when it’s about to create a new J User. This event gives the opportunity to plugins to implement their own user registration process. If a plugin decides it wants to utilize this feature, it must throw a JoomfuseRegistrationSuccess exception that contains the created Juser in it. We throw the event in order to make sure that only one plugin can actually utilize this feature, or we can end up with double user creation issues. 

Currently no plugins  utilize this event.

onSetJoomlaFieldsFromContact
----------------------------

Declaration: onSetJoomlaFieldsFromContact($user_id, stdClass $ifs_contact, $isNew)

Triggered from the JF Core JTTP POST parser as a signal to all the supported extensions that they need to populate the Juser values they keep track of according to the contact values contained within the $ifs_contact object. 

No return value. 

As expected, all plugins of the joomfuse group utilize this event: plg_joomfuse_joomla, plg_joomfuse_communitybuilder, plg_joomfuse_jomsocial.

onJoomFuseBeforeContactSave
---------------------------

Declaration: onJoomFuseBeforeContactSave($userid, JoomFuseAPIField[] $initialContactFields, JoomFuseAPIField[] $finalContactFields)


Triggered from the JF Core (IFSContact::save()) when a contact is about to be saved. The two field arrays contain the current and future contents of the contact fields for examination. There are no return values, but throwing an Exception will prevent the update of the IFS Contact. 

Currently, only plg_joomfuse_joomla utilizes this event.

onJoomFuseAfterContactSave
--------------------------

Declaration: onJoomFuseAfterContactSave($userid, JoomFuseAPIField[] $initialContactFields, JoomFuseAPIField[] $finalContactFields)

Triggered from the JF Core (IFSContact::save()) when a contact has been saved. The two field arrays contain the previous and current contact fields for examination. There are no return values. 

Currently no extensions are utilizing this event.

onJoomfuseBeforeContactAssociation
----------------------------------

Declaration: onJoomfuseBeforeContactAssociation($user_id, $contact_id)

Triggered from the JF Core (IFSContact::load()) when a J User is about to be associated with an IFS Contact. 

There are no return values. 

Currently no plugins utilize this event.

onJoomfuseAfterContactAssociation
---------------------------------

Declaration: onJoomfuseAfterContactAssociation(IFSContact $contact)

Triggered from the JF Core (IFSContact::load()) when a J User has been associated with an IFS Contact. 

There are no return values. 

Currently the following plugins utilize this event:

1. plg_joomfuse_joomla to enforce the tag/group mapping configured in com_joomfuse

2. plg_joomfuse_jomsocial to enforce the tag/jomsocial-group mapping configured.

getJoomFuseContactFields
------------------------

Declaration: getJoomFuseContactFields($user_id, $isContactCreation)

Triggered from the JF Core:

1. IFSContact::save()

2. IFSContact::load()

3. IFSContact::locateIFSContact()

4. The shortcodes view model (remove this?) to retrieve the contact field values from all JoomFuse plugins that handling field mappings. 

5. plg_system_joomfuse to replace the shortcode strings with the appropriate vales (shouldn’t this be moved somewhere to the core or IFSContact?)

Please note that this event is thrown at least twice per pageload as it’s used from the JF Core to detect any contact field changes, which may trigger a contact update. The user_id parameter is the Joomla user id and isContactCreation signifies that this call is involved in a contact creation (which is unused and should be removed). 

Currently the following plugins utilize this event:

6. plg_joomfuse_communitybuilder: Provide values for the CB-sourced mapped fields

7. plg_joomfuse_jomsocial: Provide values for the JomSocial-sourced mapped fields

8. plg_joomfuse_joomla: Provide values for the 
  
 1. vanilla Joomla user fields
  
 2. The old plugin-based Joomla profile fields (plg_joomla_profile) 
  
 3. The new com_fields custom user fields

onNewUserRegistrationEmail
--------------------------

Declaration: onNewUserRegistrationEmail(array $userProperties, $password)

Called from the JF Core (IFSFactory::registerUser() while parsing an HTTP POST) and provides the opportunity to any listening plugin to compose it’s own welcome/registration email. The provided parameters are the JUser object as an array and the plaintext password used to create the account (which is one of the main reasons for the existence of this event). The return value is an array that is expected to have the ‘topic’ and ‘content’ array keys with the appropriate values. Please note that if more than one plugins return data for this event, only the contents of the last one will be used. 

Currently, only plg_joomfuse_joomla is utilizing this event. 

This feature and event should be considered for removal in JF3 in favor of the IFS-sourced emails.

onContactUserDelete
-------------------

Declaration: onContactUserDelete($userProperties)

Called from plg_joomla_joomfuse when a JUser has been deleted in order for all the listening plugins to perform any contact cleanup needed. The following plugins currently listen for this event:

1. plg_joomfuse_jomsocial: Removes all JomSocial-based tags from the Contact that are associated with the JomSocial chat groups

2. plg_joomfuse_joomla: Appends the “user deleted” tag to the contact and removes all the JoomFuse-utilized tags that are possibly set for the user. These are:
  
 1. Tags associated with all the mapped usergroups

 2. New User Tag

 3. New HTTP-POST user tag
  
 4. HTTP POST success tag
  
 5. HTTP POST fail tag
           
The userProperties parameter is the user info array as provided via the user/onUserAfterDelete event. There are no return values for this event.

onJoomfuseCron
--------------

Declaration: onJoomfuseCron($handler, JRegistry $registry)

Triggered via the JFCore (IFSFactory::cronCheck()) which sends to all listening plugins any cron task that should now execute. The handler param contains the identifier of the plugin responsible to handle this call and the data that contains all data pertaining the execution of the task in a JRegistry object. 

Currently only plg_joomfuse_jfportal utilizes this event in order to:

1. Run the actionsets associated with the “this contacts subscription cancellation is complete”    event.

2. Achieve the goals associated with the “this contacts subscription cancellation is complete” event.
