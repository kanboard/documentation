Task Metadata API Procedures
============================

getTaskMetadata
---------------

-  Purpose: **Get all metadata related to a task by task unique id**
-  Parameters:

   -  **task_id** (integer, required)

-  Result on success: **list of metadata**
-  Result on failure: **empty array**

Request example to fetch all the metada of a task:

.. code:: json

    {
        "jsonrpc": "2.0",
        "method": "getTaskMetadata",
        "id": 133280317,
        "params": [
            1
        ]
    }

Response example:

.. code:: json

    {
        "jsonrpc": "2.0",
        "id": 133280317,
        "result": [
            {
                "metaKey1": "metaValue1",
                "metaKey2": "metaValue2"
            }
        ]
    }

getTaskMetadataByName
---------------------

-  Purpose: **Get metadata related to a task by task unique id and
   metakey (name)**
-  Parameters:

   -  **task_id** (integer, required)
   -  **name** (string, required)

-  Result on success: **metadata value**
-  Result on failure: **empty string**

Request example to fetch metada of a task by name:

.. code:: json

    {
        "jsonrpc": "2.0",
        "method": "getTaskMetadataByName",
        "id": 133280317,
        "params": [
            1,
            "metaKey1"
        ]
    }

Response example:

.. code:: json

    {
        "jsonrpc": "2.0",
        "id": 133280317,
        "result": "metaValue1"
    }

saveTaskMetadata
----------------

-  Purpose: **Save/update task metadata**
-  Parameters:

   -  **task_id** (integer, required)
   -  **array(“name” => “value”)** (array, required)

-  Result on success: **true**
-  Result on failure: **false**

Request example to add/update metada of a task:

.. code:: json

    {
        "jsonrpc": "2.0",
        "method": "saveTaskMetadata",
        "id": 133280317,
        "params": [
            1,
            {
                "metaName" : "metaValue"
            }
        ]
    }

Response example:

.. code:: json

    {
        "jsonrpc": "2.0",
        "id": 133280317,
        "result": true
    }

removeTaskMetadata
------------------

-  Purpose: **Remove task metadata by name**
-  Parameters:

   -  **task_id** (integer, required)
   -  **name** (string, required)

-  Result on success: **true**
-  Result on failure: **false**

Request example to remove metada of a task by name:

.. code:: json

    {
        "jsonrpc": "2.0",
        "method": "removeTaskMetadata",
        "id": 133280317,
        "params": [
            1,
            "metaKey1"
        ]
    }

Response example:

.. code:: json

    {
        "jsonrpc": "2.0",
        "id": 133280317,
        "result": true
    }
