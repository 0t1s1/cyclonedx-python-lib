Outputting
==========

Once you have an instance of a :py:mod:`cyclonedx.model.bom.Bom` you can produce output in either **JSON** or **XML**
against any of the supported CycloneDX schema versions.

We provide two helper methods:

* Output to string (for you to do with as you require)
* Output directly to a filename you provide

The default output will be XML at Schema Version 1.3.

Supported CycloneDX Schema Versions
-----------------------------------

This library supports the following schema versions:

* 1.0 (XML) - `(note, 1.1 schema version has no support for JSON)`
* 1.1 (XML) - `(note, 1.1 schema version has no support for JSON)`
* 1.2 (XML, JSON)
* 1.3 (XML, JSON)
* 1.4 (XML, JSON)

Outputting to JSON
------------------

The below example relies on the default schema version being 1.3, but sets the output format to JSON. Output is returned
as a ``str``.

.. code-block:: python

    from cyclonedx.output import get_instance, BaseOutput, OutputFormat

    outputter: BaseOutput = get_instance(bom=bom, output_format=OutputFormat.JSON)
    bom_json: str = outputter.output_as_string()


Outputting to XML
------------------

The below example relies on the default output format being XML, but overrides the schema version to 1.2. Output is
written to the supplied filename.

.. code-block:: python

    from cyclonedx.output import get_instance, BaseOutput, SchemaVersion

    outputter: BaseOutput = get_instance(bom=bom, schema_version=SchemaVersion.V1_2)
    outputter.output_to_file(filename='/tmp/sbom-v1.2.xml')