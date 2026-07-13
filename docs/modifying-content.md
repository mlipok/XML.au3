# Creating and updating XML content

## Create child nodes

Use `_XML_CreateChildWAttr()` to append a child element under nodes selected by XPath. Attributes are supplied as a two-column array using `$XMLATTR_COLNAME` and `$XMLATTR_COLVALUE`.

```vb
Local $aAttributes[1][$XMLATTR_COLCOUNTER]
$aAttributes[0][$XMLATTR_COLNAME] = "id"
$aAttributes[0][$XMLATTR_COLVALUE] = "42"

_XML_CreateChildWAttr($oXmlDoc, "/root", "item", $aAttributes, "Example")
```

Use `_XML_InsertChildNode()` or `_XML_InsertChildWAttr()` when the new element must be inserted before a selected child index. These functions are listed as work in progress in the current UDF.

## Root nodes

- `_XML_CreateRootNode()` creates a root element and returns the created node.
- `_XML_CreateRootNodeWAttr()` creates a root element with one or more attributes.

A valid XML document can contain only one document element.

## Attributes

Relevant functions include:

- `_XML_CreateAttribute()`
- `_XML_SetAttrib()`
- `_XML_GetNodeAttributeValue()`
- `_XML_GetAllAttrib()`
- `_XML_RemoveAttribute()`
- `_XML_RemoveAttributeNode()`

Several attribute APIs accept a two-column array. Use the exported column constants instead of numeric indexes.

## Update values

`_XML_UpdateField()` updates one selected node. `_XML_UpdateField2()` updates multiple matching nodes but remains marked for further review in the source.

```vb
_XML_UpdateField($oXmlDoc, "/root/item[@id='42']", "Updated")
```

## Delete and replace nodes

- `_XML_DeleteNode()` removes nodes selected by XPath.
- `_XML_ReplaceChild()` replaces matching elements while copying attributes and child nodes.

## Comments and CDATA

- `_XML_CreateComment()` inserts a comment under a selected node.
- `_XML_CreateCDATA()` creates an element containing a CDATA section.

Always check `@error` after mutation operations. Node creation, append, parse, and XPath failures use different `$XML_ERR_*` values.