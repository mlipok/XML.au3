# XPath, node selection, and namespaces

## Select one node

Use `_XML_SelectSingleNode()` when exactly one node object is required:

```vb
Local $oNode = _XML_SelectSingleNode($oXmlDoc, "/root/item[@id='1']")
```

A missing match sets `@error` to `$XML_ERR_NONODESMATCH`. Invalid XPath syntax sets `$XML_ERR_XPATH`.

## Select multiple nodes

Use `_XML_SelectNodes()` for a node collection:

```vb
Local $oNodes = _XML_SelectNodes($oXmlDoc, "/root/item")
If Not @error Then ConsoleWrite("Count: " & @extended & @CRLF)
```

On success, `@extended` contains the collection length. An empty result is treated as `$XML_ERR_EMPTYCOLLECTION` rather than a successful empty collection.

Both selection functions can accept a DOMDocument or an element, which permits relative XPath queries from a selected element.

## Read values

`_XML_GetValue()` returns an array by default. Element zero contains the number of returned values. Pass `True` as the third parameter to return only the first value as a string.

```vb
Local $sValue = _XML_GetValue($oXmlDoc, "/root/item", True)
```

## Namespaces

For namespaced XML, provide an MSXML `SelectionNamespaces` declaration when calling `_XML_Load()` or `_XML_LoadXML()`:

```vb
Local $sNamespaces = "xmlns:cfg='urn:example:configuration'"
_XML_Load($oXmlDoc, $sXmlFile, $sNamespaces, False)

Local $oNode = _XML_SelectSingleNode($oXmlDoc, "/cfg:root/cfg:item")
```

The XPath prefix is an alias used by the query. It does not need to match the prefix used in the XML file, but it must map to the same namespace URI.

Default namespaces still require an explicit query prefix. An unprefixed XPath normally selects nodes with no namespace.

## Relative queries

```vb
Local $oSection = _XML_SelectSingleNode($oXmlDoc, "/root/section")
Local $oItems = _XML_SelectNodes($oSection, "item")
```

Check `@error` immediately after each UDF call because a later AutoIt expression can overwrite it.