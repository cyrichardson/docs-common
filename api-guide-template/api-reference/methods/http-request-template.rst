
========================
Document an HTTP request
========================

   This template provides the structure, some guidelines, and example
   content for documenting a single HTTP request (for example,
   GET /v2.0/servers). For more guidelines, see 
   :ref:`HTTP request documentation guidelines
   <http-request-documentation-guidelines>`. For an extended example, 
   see :ref:`Example HTTP request topic <update-an-image>`.
   
   Delete the example content and comments, and add your content.

.. Immediately following the title, show the URI in a code block (no label).

.. code::

    METHOD /version/{projectId}/service/{placeholder}

.. Immediately follow the URI code block with a description
   (no heading). Include only necessary information that applies
   to the operation as a whole. Place specific information about a
   parameter in the parameter table, later in the file. If there is more
   parameter information than can be shown in the table, place it after
   the introduction.

   For example:

This operation [describe what the operation does].

Request parameters
~~~~~~~~~~~~~~~~~~

.. This section includes tables for header, URI, query, and request
   body parameters, as needed. Precede each table with a basic
   introduction, such as "The request has the following ___ parameters."

The request has the following [header | URI | query | request body]
parameters.

.. Parameter tables include the following columns: Name, Type, Description.
   Following is an example table, created with the `list-table` directive:

.. list-table::
   :widths: 15 10 30
   :header-rows: 1

   * - Name
     - Type
     - Description
   * - op
     - String
     - *(Required)* The operation to be executed: ``add``, ``remove``, or
       ``replace``. For more information about updating image properties, see
       the beginning of this operation section.
   * - value
     - String
     - The actual value to be added or replaced. This parameter is not required
       for the ``remove`` operation.

.. If there are no request body parameters, include the following
   sentence: "This operation does not accept a request body."

Request example
~~~~~~~~~~~~~~~

.. This section contains the code example with an introductory sentence,
   such as "The following example shows the JSON request for retrieving a list
   of flavors." Specify the type of request, if applicable (such as JSON,
   HTTP, or cURL). In the example, include the HTTP request header and show
   the body (if there is a body). For example:

The following example shows [describe what the example shows].

.. code::

    X-Auth-Token: f064c46a782c444cb4ba4b6434288f7c
    Content-Type: application/json
    Accept: application/json

.. code::

    [
        {"op": "replace", "path": "/name", "value": "Fedora 17"},
        {"op": "replace", "path": "/tags", "value": ["fedora", "beefy"]}
    ]

Response parameters
~~~~~~~~~~~~~~~~~~~

.. If you need to say something specific about the response, say it in
   this section, and then include a table for body parameters, as needed
   (using the `list-table` directive). Precede the table with a basic
   introduction, such as "The response has the following body parameters."
   Parameter tables include the following columns: Name, Type, Description.
   Following is an example table, created with the `list-table` directive:

The response has the following body parameters.

.. list-table::
   :widths: 15 10 30
   :header-rows: 1

   * - Name
     - Type
     - Description
   * - id
     - String
     - The UUID of the image.
   * - name
     - String
     - The name of the image.
   * - status
     - String
     - The status of the image.

Response example
~~~~~~~~~~~~~~~~

.. This section contains the code example with an introductory sentence,
   such as "The following example shows the JSON response for the request."
   Specify the type of response, if applicable (such as JSON, HTTP, or cURL).
   In the example, include the HTTP request header and show the body (if there
   is a body). For example:

The following example shows [describe what the example shows].

.. code::

    {
      "id":"e7db3b45-8db7-47ad-8109-3fb55c2c24fd",
      "name":"Fedora 17",
      "status":"queued",
      "visibility":"public",
      "tags": ["fedora", "beefy"],
      "created_at":"2012-08-11T17:15:52Z",
      "updated_at":"2012-08-11T17:15:52Z",
      "self":"/v2/images/e7db3b45-8db7-47ad-8109-3fb55c2c24fd",
      "file":"/v2/images/e7db3b45-8db7-47ad-8109-3fb55c2c24fd/file",
      "schema":"/v2/schemas/image"
    }

Response codes
~~~~~~~~~~~~~~

.. Provide a `list-table` table with the possible response codes for
   the operation. Response code tables include the following columns:
   Code, Name, Description. Following is an example table with just a
   few possible codes.

This operation can have the following response codes.

.. list-table::
   :widths: 15 10 30
   :header-rows: 1

   * - Code
     - Name
     - Description
   * - 200
     - Success
     - The request succeeded.
   * - 400
     - Error
     - A general error has occurred.
   * - 401
     - Unauthorized
     - The request has not been applied because it lacks valid authentication
       credentials for the target resource. The credentials are either expired
       or invalid.
   * - 403
     - Forbidden
     - The server understood the request but is not authorizing it.
