.. graphviz::

   digraph {

      subgraph a {
      
        style=filled;
        color=lightgrey;
        node [style=filled,color=white];
        label="Before saving the user!"
        
        1 [label="Catch event: 'onUserBeforeSave'." shape=triangle]
        2 [label="Is the http post parsing?" shape=invhouse]
        3 [label="Yes." shape=oval]
        4 [label="No." shape=oval]
        5 [label="Call to: 'IFSFactory::isParsingHttpPost'." shape=rectangle]
        6 [label="Call to: 'IFSApi::getUserContact'." shape=rectangle]
        7 [label="Is the user new?" shape=invhouse]
        8 [label="Yes." shape=oval]
        9 [label="No." shape=oval]
        10 [label="Is the email modified?" shape=invhouse]
        11 [label="Yes." shape=oval]
        12 [label="No." shape=oval]
        
      }
      
      subgraph b {
      
        style=filled;
        color=lightgrey;
        node [style=filled,color=white];
        label="After saving the user!"
        
        14 [label="Catch event: 'onUserAfterSave'." shape=triangle]
        15 [label="Was the save successful?" shape=invhouse]
        16 [label="Yes." shape=oval]
        17 [label="No." shape=oval]
        18 [label="Call to: 'IFSFactory::isParsingHttpPost'." shape=rectangle]
        19 [label="Is the http post parsing?" shape=invhouse]
        20 [label="Yes." shape=oval]
        21 [label="No." shape=oval]
        22 [label="Call to: 'IFSFactory::getUserContact'." shape=rectangle]
        23 [label="Is the user new?" shape=invhouse]
        24 [label="Yes." shape=oval]
        25 [label="No." shape=oval]
        26 [label="Call to: 'IFSContact::assignIFSTag'." shape=rectangle]
        27 [label="Was the email modified?" shape=invhouse]
        28 [label="Yes." shape=oval]
        29 [label="No." shape=oval]
        30 [label="Call to: 'IFSContact::optIn'." shape=rectangle]
        31 [label="Sync the user groups.'." shape=rectangle]
        
      }
      
      32 [label="Do nothing.'." shape=Mcircle]

      1 -> 2 [arrowhead=vee arrowsize=1]
      2 -> 3 [arrowhead=vee arrowsize=1]
      2 -> 4 [arrowhead=vee arrowsize=1]
      4 -> 32 [arrowhead=vee arrowsize=1]
      3 -> 5 [arrowhead=vee arrowsize=1]
      5 -> 6 [arrowhead=vee arrowsize=1]
      6 -> 7 [arrowhead=vee arrowsize=1]
      7 -> 8 [arrowhead=vee arrowsize=1]
      7 -> 9 [arrowhead=vee arrowsize=1]
      9 -> 32 [arrowhead=vee arrowsize=1]
      8 -> 10 [arrowhead=vee arrowsize=1]
      10 -> 11 [arrowhead=vee arrowsize=1]
      10 -> 12 [arrowhead=vee arrowsize=1]
      
      14 -> 15 [arrowhead=vee arrowsize=1]
      15 -> 16 [arrowhead=vee arrowsize=1]
      15 -> 17 [arrowhead=vee arrowsize=1]
      17 -> 32 [arrowhead=vee arrowsize=1]
      16 -> 18 [arrowhead=vee arrowsize=1]
      18 -> 19 [arrowhead=vee arrowsize=1]
      19 -> 20 [arrowhead=vee arrowsize=1]
      19 -> 21 [arrowhead=vee arrowsize=1]
      21 -> 32 [arrowhead=vee arrowsize=1]
      20 -> 22 [arrowhead=vee arrowsize=1]
      22 -> 23 [arrowhead=vee arrowsize=1]
      23 -> 24 [arrowhead=vee arrowsize=1]
      23 -> 25 [arrowhead=vee arrowsize=1]
      24 -> 26 [arrowhead=vee arrowsize=1]
      26 -> 27 [arrowhead=vee arrowsize=1]
      25 -> 27 [arrowhead=vee arrowsize=1]
      27 -> 28 [arrowhead=vee arrowsize=1]
      27 -> 29 [arrowhead=vee arrowsize=1]
      28 -> 30 [arrowhead=vee arrowsize=1]
      29 -> 31 [arrowhead=vee arrowsize=1]
      30 -> 31 [arrowhead=vee arrowsize=1]
   }
