3rd Party Events
================

In order to provide the intended functionality of the 3rd party Joomla extensions, JoomFuse intercepts the following events thrown:

community/onBeforeProfileUpdate
-------------------------------

Declaration: community/onBeforeProfileUpdate($user_id, $valuesCode)

Thrown by the JomSocial core before the update of a user profile. This event is intercepted by the plg_community_joomfuse plugin in order to attempt to capture any password changes performed via the JomSocial pages.

Community/ onGroupJoin
----------------------

Declaration: Community/ onGroupJoin( $group, $memberid )

Thrown by the JomSocial core when a user has join a chat group. plg_community_joomfuse intercepts this event in order to push any contact tags possibly associated with this chat-group.

onGroupLeave
------------

Declaration: onGroupLeave( $group, $memberid )

Thrown by the JomSocial core when a user leaves a chat group. plg_community_joomfuse intercepts this event in order to remove any contact tags associated with this chat-group.
    
TODO: What happens when a group is just deleted? Do we get a sequence of onGrouLeaves for each member or do we need to capture that as well?

onGroupBanned
-------------

Declaration: onGroupBanned($group, $memberid)

Thrown by the JomSocial core when a user is banned from a chat group. plg_community_joomfuse intercepts this event and treats it as an onGrouLeave (see previous bulletpoint for details)

onGroupUnbanned
---------------

Declaration: onGroupUnbanned($group, $memberid)

Thrown by the JomSocial core when a user is un-banned from a chat group. plg_community_joomfuse intercepts this event and treats it as an onGroupJoin (see three bulletpoints above for details). 
