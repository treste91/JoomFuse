XML RPC API
===========

The following functions :

dsQuery()
---------

Declaration: dsQuery($tableName, $searchFields, $returnFields)

Queries an IFS table with the provided data.

dsUpdate()
---------

Declaration: dsUpdate($tableName, $recordId ,$updateFields)

Updates an IFS table row with the provided data.

Currently, the cancelSubscription() function calls this. `Stack Overflow <http://stackoverflow.com/>`_.

dsAdd()
---------

Declaration: dsAdd($tableName, $updateFields)

Creates an IFS table row with the provided data.


cancelSubscription()
--------------------

Declaration: cancelSubscription($recurringOrderId, $endDate, $reasonStopped)

Is called to cancel the subscription of a specific order.
