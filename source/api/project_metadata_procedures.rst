Project Metadata API Procedures
===============================

getProjectMetadata
------------------

-  Purpose: **Get Project metadata**
-  Parameters:

   -  **project_id** (integer, required)

-  Result on success: **dictionary of metadata**
-  Result on failure: **false**

Request example:

.. code:: json

    {
        "jsonrpc": "2.0",
        "method": "getProjectMetadata",
        "id": 1797076613,
        "params": {
            "project_id": 1
        }
    }

Response example:

.. code:: json

    {
        "jsonrpc": "2.0",
        "id": 1797076613,
        "result": {
            "key1": "value1"
        }
    }

getProjectMetadataByName
------------------------

-  Purpose: **Fetch single metadata value**
-  Parameters:

   -  **project_id** (integer, required)
   -  **name** (string, required)

-  Result on success: **mixed**
-  Result on failure: **empty string**

Request example:

.. code:: json

    {
        "jsonrpc": "2.0",
        "method": "getProjectMetadataByName",
        "id": 1797076613,
        "params": {
            "project_id": 1,
            "name": "key1"
        }
    }

Response example:

.. code:: json

    {
        "jsonrpc": "2.0",
        "id": 1797076613,
        "result": "value1"
    }

saveProjectMetadata
-------------------

-  Purpose: **Add or update metadata**
-  Parameters:

   -  **project_id** (integer, required)
   -  **values** (dict, required)

-  Result on success: **true**
-  Result on failure: **false**

Request example:

.. code:: json

    {
        "jsonrpc": "2.0",
        "method": "saveProjectMetadata",
        "id": 1797076613,
        "params": {
            "project_id": 1,
            "values": {
                "key1": "value1"
            }
        }
    }

Response example:

.. code:: json

    {
        "jsonrpc": "2.0",
        "id": 1797076613,
        "result": true
    }

removeProjectMetadata
---------------------

-  Purpose: **Remove a project metadata**
-  Parameters:

   -  **project_id** (integer, required)
   -  **name** (string, required)

-  Result on success: **true**
-  Result on failure: **false**

Request example:

.. code:: json

    {
        "jsonrpc": "2.0",
        "method": "removeProjectMetadata",
        "id": 1797076613,
        "params": {
            "project_id": 1,
            "name": "my key"
        }
    }

Response example:

.. code:: json

    {
        "jsonrpc": "2.0",
        "id": 1797076613,
        "result": true
    }
