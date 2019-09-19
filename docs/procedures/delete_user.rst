Delete User
***********

Before deleting the user!
^^^^^^^^^^^^^^^^^^^^^^^^

.. graphviz::

   digraph {
        
      1 [label="Catch event: 'onUserBeforeDelete'." shape=parallelogram]
      2 [label="Call to: 'IFSFactory::getUserContact'.\n (The data of the user are needed later)" shape=rectangle]

      1 -> 2 [arrowhead=vee arrowsize=1]
      
   }

|
   
After deleting the user!
^^^^^^^^^^^^^^^^^^^^^^^

.. graphviz::
   
   digraph {
   
      3 [label="Catch event: 'onUserAfterDelete'." shape=parallelogram]
      4 [label="Was the deletion successful?" shape=invhouse]
      5 [label="Yes." shape=oval]
      6 [label="No." shape=oval]
      7 [label="Call to: 'IFSFactory::getUserContact'." shape=rectangle]
      8 [label="Call to: 'IFSFactory::setUserBeingDeleted'." shape=rectangle]
      9 [label="Trigger event: 'onContactUserDelete'."URL="https://joomfuse.readthedocs.io/en/latest/events/joomfuse_events.html#oncontactuserdelete" shape=rectangle]
      10 [label="Do nothing." shape=Mcircle]
     
      3 -> 4 [arrowhead=vee arrowsize=1]
      4 -> 5 [arrowhead=vee arrowsize=1]
      4 -> 6 [arrowhead=vee arrowsize=1]
      6 -> 10 [arrowhead=vee arrowsize=1]
      5 -> 7 [arrowhead=vee arrowsize=1]
      7 -> 8 [arrowhead=vee arrowsize=1]
      8 -> 9 [arrowhead=vee arrowsize=1]
      
   }
