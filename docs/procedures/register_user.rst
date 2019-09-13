Register User
*************

.. graphviz::

   digraph {
      1 [label="Call to: 'IFSFactory::ParseHttpPost'." shape=box]
      2 [label="Trigger event: 'onIFSHttpPostStart'." shape=box]
      3 [label="Call to: 'IFSApi::getContactByIFSId'." shape=box]
      4 [label="Is there a user associated with the current IFSId?" shape=oval]
      5 [label="Yes." shape=underline]
      6 [label="No." shape=underlline]
      1 -> 2
      2 -> 3
      3 -> 4
      4 -> 5
      4 -> 6
   }
