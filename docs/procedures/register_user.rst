Register User
*************

.. graphviz::

   digraph {
   
      1 [label="Call to: 'IFSFactory::ParseHttpPost'." shape=rectangle]
      2 [label="Trigger event: 'onIFSHttpPostStart'." shape=rectangle]
      3 [label="Call to: 'IFSApi::getContactByIFSId'." shape=rectangle]
      4 [label="Is there a user associated\n with the current IFSId?" shape=invhouse]
      5 [label="Yes." shape=oval]
      6 [label="No." shape=oval]
      7 [label="Is there a user associated\n with the contact's email,\n first and last name?" shape=invhouse]
      8 [label="Yes." shape=oval]
      9 [label="An associated user was found." shape=rectangle]
      10 [label="No." shape=oval]
      11 [label="The user is new." shape=rectangle]
      
      subgraph cluster_1 {
         style=filled;
         color=lightgrey;
		   node [style=filled,color=white];
         label="Do the component parameters\n allow new user registration?"
         12 [label="Call to: 'IFSApi::getTagsByIFSId'." shape=rectangle]
         13 [label="Trigger event: 'onCustomUserRegistration'." shape=rectangle]
      }
      
      14 [label="Yes." shape=oval]
      15 [label="No." shape=oval]
      16 [label="Manual user registration." shape=rectangle]
      17 [label="Trigger event: 'onSetJoomlaFieldsFromContact'." shape=rectangle]
      18 [label="Set the user groups." shape=rectangle]
      19 [label="Save the user." shape=rectangle]
      20 [label="Call to: 'IFSFactory::getUserContact'." shape=rectangle]
      21 [label="Assign the 'success' tag and/or goal." shape=rectangle]
      22 [label="Assign the 'new user' tag." shape=rectangle]
      23 [label="Trigger event: 'onIFSHttpPostComplete'." shape=rectangle]
      
      
      1 -> 2 [arrowhead=vee arrowsize=1]
      2 -> 3 [arrowhead=vee arrowsize=1]
      3 -> 4 [arrowhead=vee arrowsize=1]
      4 -> 5 [arrowhead=vee arrowsize=1]
      4 -> 6 [arrowhead=vee arrowsize=1]
      6 -> 7 [arrowhead=vee arrowsize=1]
      7 -> 8 [arrowhead=vee arrowsize=1]
      8 -> 9 [arrowhead=vee arrowsize=1]
      6 -> 9 [arrowhead=vee arrowsize=1]
      7 -> 10 [arrowhead=vee arrowsize=1]
      10 -> 11 [arrowhead=vee arrowsize=1]
      11 -> 12 [arrowhead=vee arrowsize=1]
      12 -> 13 [arrowhead=vee arrowsize=1]
      13 -> 14 [arrowhead=vee arrowsize=1]
      13 -> 15 [arrowhead=vee arrowsize=1]
      15 -> 16 [arrowhead=vee arrowsize=1]
      16 -> 17 [arrowhead=vee arrowsize=1]
      14 -> 17 [arrowhead=vee arrowsize=1]
      9 -> 17 [arrowhead=vee arrowsize=1]
      17 -> 18 [arrowhead=vee arrowsize=1]
      18 -> 19 [arrowhead=vee arrowsize=1]
      19 -> 20 [arrowhead=vee arrowsize=1]
      20 -> 21 [arrowhead=vee arrowsize=1]
      21 -> 22 [arrowhead=vee arrowsize=1]
      22 -> 23 [arrowhead=vee arrowsize=1]
   }
