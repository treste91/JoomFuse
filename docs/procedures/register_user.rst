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
         label="Do the component parameters\n allow new user registration?"
         12 [label="Call to: 'IFSApi::getTagsByIFSId'." shape=rectangle]
         13 [label="Trigger event: 'onCustomUserRegistration'." shape=rectangle]
         14 [label="Yes." shape=oval]
         15 [label="No." shape=oval]
      }
      
      
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
   }
