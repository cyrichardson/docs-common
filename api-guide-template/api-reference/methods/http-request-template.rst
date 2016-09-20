
========================
Document an HTTP request
========================

.. This template provides the structure and some guidelines for documenting
   a single HTTP request (for example, GET /v2.0/servers). For more instructions, see :ref:`HTTP request documentation guidelines <http-request-documentation-guidelines>`. For an example, see :ref:`Example HTTP request topic <update-an-image>`.

.. Immediately following the title, show the URI in a code block (no label).
   For example:

.. code::

    PATCH /v1.0/images/{imageId}

.. Follow the URI code block with a description (no heading). Start with
   "This operation … ." Include only necessary information that applies to the operation as a whole. Specific information about a parameter should go in the parameter table, later in the file. If there is more parameter information than can be shown in the table, place it in a "Parameter details" section following the introduction.

   For example:

This operation updates the specified image. You can update only an image that you own. You can use the HTTP PATCH method to update certain standard properties, and to add, update, or remove custom, user-defined image properties.

Request parameters
~~~~~~~~~~~~~~~~~~

.. This section includes tables for header, URI, query, and request
   body parameters, as needed. Precede each table with a basic introduction, such as "The request has the following ___ parameters." For example:

The request has the following URI parameters.

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
   * - path
     - String
     - *(Required)* The location within the image where the operation is to be
       performed.
   * - value
     - String
     - The actual value to be added or replaced. This parameter is not required
       for the ``remove`` operation.

.. If there are no request body parameters, include the following
   sentence: "This operation does not accept a request body."

Request example
~~~~~~~~~~~~~~~

.. This section contains the code example with an introductory sentence,
   such as "The following example shows the JSON request for retrieving a list of flavors." Specify the type of request, if applicable (such as JSON, HTTP, or cURL). In the example, include the HTTP request header and show the body (if there is a body). For example:

The following example updates two properties for the image: `name` and
`tags`.

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
   this section, and then include a table for body parameters, as needed (using the `list-table` directive). Precede the table with a basic introduction, such as "The response has the following body parameters." Parameter tables include the following columns: Name, Type, Description. For example:

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
   * - visibility
     - String
     - Specifies image visibility as ``public``, ``private``, or ``shared``.
   * - checksum
     - String
     - The checksum of the image.
   * - minRam
     - String
     - The minimum server RAM required for this image.
   * - minDisk
     - String
     - The minimum server disk size required for this image.
   * - tags[ ]
     - Array
     - An array of user-defined image tags.
   * - created_at
     - String
     - The date and time that the image was created.
   * - updated_at
     - String
     - The date and time that the image was updated.
   * - schema
     - String
     - The schema of the image.

Response example
~~~~~~~~~~~~~~~~

.. This section contains the code example with an introductory sentence,
   such as "The following example shows the JSON response for the request." Specify the type of response, if applicable (such as JSON, HTTP, or cURL). In the example, include the HTTP request header and show the body (if there is a body). For example:

You can show multiple examples, by error code. Precede each with an
introductory sentence.

The following example shows the JSON response for retrieving the backup for a
project.

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
   the operation. Introduce it as follows: "This operation can have the following response codes." Response code tables include the following columns: Code, Name, Description. For example:

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
   * - 405
     - Method Not Allowed
     - The method received in the request line is known by the origin server
       but is not supported by the target resource.
   * - 413
     - Over Limit
     - The number of items returned is above the allowed limit.
   * - 415
     - Bad Media Type
     - This error might result if the wrong media type is used in the cURL
       request.
   * - 500
     - API Fault
     - The server encountered an unexpected condition that prevented it from
       fulfilling the request.
   * - 503
     - Service Unavailable
     - The server is currently unable to handle the request because of a
       temporary overload or scheduled maintenance, which will likely be
       alleviated after some delay.
