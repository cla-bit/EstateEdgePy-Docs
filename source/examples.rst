===========================
How to use EstateEdgePy
===========================

For installation instructions, refer to: :doc:`get_started`.

The EstateEdgePy library supports asynchronous operations.
To use them, import and instantiate the appropriate wrappers as shown below:


Asynchronous support:
~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: python

    from EstateEdgePy import VERSION
    from EstateEdgePy.core.filters import DateRangeFilter, PriceRangeFilter, EntityFilter

    EstateEdgePy_version = VERSION

Output

.. code-block:: bash

    >>> '2.06'

----------------------------


Get sanction data.
------------------------------------

In `EstateEdgePy` version 2 [v2] one can easily get data from any real estate property passed.

Here is a simple way to get a sanction data. In this case we will be use `canada`.


**[A] First Method**

*   **Step 1**: Create the Property client object

    .. code-block:: python

        >>> client = EstateEdgeClient()


*   **Step 2**: Create the PropertyService instance and pass the client object.

    .. code-block:: python

        >>> service = PropertyService(client=client)


*   Step 3: Call the get_filtered() method and pass a list of filters you want

    .. code-block:: python

        >>> all_filters = [DateRangeFilter(date_column="", start_date="", end_date=""), EntityFilter(search_terms="", columns="", match_type="partial", case_sensitive=False)]
        >>> filtered_data = await service.get_filtered('MD', all_filters)


*   Step 6: You can transform the `filtered_data` to dataframe.

    .. code-block:: python

        print(filtered_data.to_pandas())  # returns dataframe of the filtered data
