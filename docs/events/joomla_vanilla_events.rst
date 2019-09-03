Joomla Vanilla Events
=====================

In order to provide all the needed functionality, the JF plugins intercept the following vanilla Joomla events:

editors-xtd/onDisplay
---------------------

Declaration: editors-xtd/onDisplay($name, $asset, $author) 

This event is being thrown by the content editors in Joomla in order for the listening plugins to inject their functionality in the UI. Currently plg_editors-xtd_joomfuse intercepts this event in order to inject shortcode-generation button in the article editors.

System/onAfterRender
--------------------

Declaration: System/onAfterRender()

This event is being thrown by the Joomla core when the entire page has been rendered. Currently plg_system_joomfuse intercepts this event in order to replace any shortcode strings in the produced html with the appropriate contact values.

User/onUserLogin
----------------

Declaration: User/onUserLogin($user, $options = array())

This event is being thrown by the Joomla core when a user has logged in. plg_user_joomfuse intercepts this event in order to simply load the related IFScontact along with any functionality that comes with that: Possible user creation, initial contact field values capture. The latter reason is the most important as JF requires us the capture the contact field values before any possible field changes take place.

User/onUserBeforeSave
---------------------

Declaration: User/onUserBeforeSave($user, $isnew, $data)

This event is being thrown by the Joomla core when a user is about to be saved (created/updated). plg_user_joomfuse intercepts this event in order to to:

1. Make sure that we have a before-modification set of contact field values so we can discover any changes that need to be pushed to IFS.

2. Cache the pre-user-modification user-associated usergroups as we cannot discover the post-user-modification. This way we can figure out which mapped contact tags we should eventually push to IFS.

3. Indirectly create the user/contact association (VERIFY THIS) by virtue of loading the related IFSContact

User/onUserAfterSave
--------------------

Declaration: User/onUserAfterSave($user, $isnew, $success, $msg)

Thrown from the Joomla core after a user has been created/updated. plg_user_joomfuse intercepts this event in order to:

1. Intercept any plaintext password changes that we made via the vanilla joomla user-edit screen.

2. Assign the “new user tag” when we are dealing with a new user creation

3. Opt-in the contact when dealing with a user creation and the auto-opt-in configuration option has been enabled.

4. Assign to the related contact all tags associated with his current usergroups.

User/onUserBeforeDelete
-----------------------

Declaration: User/onUserBeforeDelete($user)

Thrown by the Joomla core when a user is about to be deleted. Currently plg_user_joomfuse intercepts this event in order to cache the user-associated contact id before the related #__joomfuse_users row is being deleted because of the foreign-key relationship. This event needs some serious rethinking, cache-based functionality? 

This feature is currently NOT WORKING.

User/onUserAfterDelete
----------------------

Declaration: User/onUserAfterDelete($user, $success, $msg)

Thrown by the Joomla core when a user has been deleted. plg_user_joomfuse intercepts this event in order to throw the onContactUserDelete” JoomFuse event. The applicable JoomFuse plugins intercept this event and perform any tasks applicable to user deletions.
