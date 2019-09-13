Register User
*************

.. graphviz::

   digraph {
   
      1 [label="Call to: 'IFSFactory::ParseHttpPost'." shape=box]
      2 [label="Trigger event: 'onIFSHttpPostStart'." shape=box]
      3 [label="Call to: 'IFSApi::getContactByIFSId'." shape=box]
      4 [label="Is there a user associated with the current IFSId?" shape=oval]
      5 [label="Yes." shape=underline]
      6 [label="No." shape=underline]
      7 [label="Is there a user associated with the contact's email,  first name and last name?" shape=oval]
      8 [label="Yes." shape=underline]
      9 [label="Does the user exist?" shape=oval]
      
      1 -> 2
      2 -> 3
      3 -> 4
      4 -> 5
      4 -> 6
      6 -> 7
      7 -> 8
      8 -> 9
      6 -> 9
   }
