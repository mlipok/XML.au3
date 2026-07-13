# XML.au3 documentation

This directory contains project documentation for the **XML.au3 UDF**.

XML.au3 provides AutoIt wrappers and helper functions for reading, creating, querying, updating, validating, formatting, and transforming XML documents through Microsoft MSXML COM components.

## Documentation index

- [Getting started](getting-started.md)
- [Loading, creating, and saving documents](loading-and-saving.md)
- [XPath, node selection, and namespaces](xpath-and-selection.md)
- [Creating and updating XML content](modifying-content.md)
- [Validation, transformation, and formatting](validation-and-transforms.md)
- [API overview](api-overview.md)
- [Troubleshooting](troubleshooting.md)
- [References and support](links.md)

## Repository files

The principal project files are:

- `XML.au3` — the main UDF implementation.
- `ADO_CONSTANTS.au3` — constants used by XML.au3 for `ADODB.Stream` operations.

## Release status

The repository preserves the public `1.1.1.14` beta release. The UDF source contains historical refactoring notes, work-in-progress functions, and warnings about script-breaking changes between versions.

Review the current function headers before migrating code from an older XMLWrapper or XMLWrapperEx release.

## Documentation scope

These pages describe the intended workflow and the most important integration constraints. Function headers in `XML.au3` remain the authoritative source for exact parameter order, return values, `@error`, and `@extended` behavior.
