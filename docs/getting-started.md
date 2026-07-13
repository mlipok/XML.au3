# Getting started

## Requirements

- AutoIt 3.3.10.2 or newer.
- `XML.au3` and `ADO_CONSTANTS.au3` available to the script.
- Microsoft MSXML installed on Windows.
- A compatible MSXML DOM version selected by `_XML_CreateDOMDocument()`.

## Basic workflow

A typical XML.au3 script follows this sequence:

1. Include `XML.au3`.
2. Create a DOM document with `_XML_CreateDOMDocument()`.
3. Load XML from a file with `_XML_Load()` or from a string with `_XML_LoadXML()`.
4. Query nodes with `_XML_SelectSingleNode()` or `_XML_SelectNodes()`.
5. Read or modify values, nodes, and attributes.
6. Save the result with `_XML_SaveToFile()`.

## Minimal example

```vb
#include "XML.au3"

Local $oXmlDoc = _XML_CreateDOMDocument(Default, "UTF-8")
If @error Then Exit ConsoleWrite("Unable to create MSXML DOMDocument." & @CRLF)

_XML_LoadXML($oXmlDoc, "<root><item id='1'>Example</item></root>", "", False)
If @error Then
    ConsoleWrite(_XML_ErrorParser_GetDescription($oXmlDoc) & @CRLF)
    Exit
EndIf

Local $oNode = _XML_SelectSingleNode($oXmlDoc, "/root/item")
If @error Then Exit ConsoleWrite("Node not found." & @CRLF)

ConsoleWrite($oNode.text & @CRLF)
```

## Error handling

Public functions generally use:

- the return value for the requested object, collection, string, array, or `$XML_RET_*` status,
- `@error` for a `$XML_ERR_*` code,
- `@extended` for parameter position, collection size, parser code, COM code, or other context.

For parse failures, preserve the DOM object and call `_XML_ErrorParser_GetDescription()` before discarding it.

## Beta status

XML.au3 is a beta UDF and its source contains functions marked as work in progress or not yet reviewed. Check the current function header and changelog before relying on behavior copied from older examples.