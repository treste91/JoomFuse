Register User
*************

.. graphviz::

   digraph {
   
      1 [label="Call to: 'IFSFactory::ParseHttpPost'." shape=rectangle]
      2 [label="Trigger event: 'onIFSHttpPostStart'." shape=rectangle]
      3 [label="Call to: 'IFSApi::getContactByIFSId'." shape=rectangle]
      4 [label="Is there a user associated with the current IFSId?" shape=invhouse]
      5 [label="Yes." shape=oval]
      6 [label="No." shape=oval]
      7 [label="Is there a user associated with the contact's email, first name and last name?" shape=invhouse]
      8 [label="Yes." shape=oval]
      9 [label="Does the user exist?" shape=invhouse]
      10 [label="No." shape=oval]
      
      1 -> 2
      2 -> 3
      3 -> 4
      4 -> 5
      4 -> 6
      6 -> 7
      7 -> 8
      8 -> 9
      6 -> 9
      7 -> 10
   }
