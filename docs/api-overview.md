# API overview

This page groups the main public functions by purpose. Function headers in `XML.au3` remain authoritative for exact signatures and return behavior.

## Document creation and loading

- `_XML_CreateDOMDocument()`
- `_XML_CreateFile()`
- `_XML_Load()`
- `_XML_LoadXML()`
- `_XML_SaveToFile()`

## Selection and reading

- `_XML_SelectNodes()`
- `_XML_SelectSingleNode()`
- `_XML_NodeExists()`
- `_XML_GetValue()`
- `_XML_GetField()`
- `_XML_GetChildNodes()`
- `_XML_GetChildren()`
- `_XML_GetChildText()`
- `_XML_GetNodesCount()`
- `_XML_GetNodeAttributeValue()`
- `_XML_GetAllAttrib()`
- `_XML_GetAllAttribIndex()`

## Creating and changing content

- `_XML_CreateRootNode()`
- `_XML_CreateRootNodeWAttr()`
- `_XML_CreateChildWAttr()`
- `_XML_InsertChildNode()`
- `_XML_InsertChildWAttr()`
- `_XML_CreateAttribute()`
- `_XML_CreateCDATA()`
- `_XML_CreateComment()`
- `_XML_SetAttrib()`
- `_XML_UpdateField()`
- `_XML_UpdateField2()`
- `_XML_ReplaceChild()`
- `_XML_DeleteNode()`
- `_XML_RemoveAttribute()`
- `_XML_RemoveAttributeNode()`

## Formatting, transformation, and validation

- `_XML_Tidy()`
- `_XML_Transform()`
- `_XML_TransformNode()`
- `_XML_ValidateFile()`

## Conversion and inspection helpers

- `_XML_Array_GetAttributesProperties()`
- `_XML_Array_GetNodesProperties()`
- `_XML_Array_AddName()`
- `_XML_GetNodesPath()`
- `_XML_GetParentNodeName()`
- `_XML_Base64Encode()`
- `_XML_Base64Decode()`

## Diagnostics and configuration

- `_XML_ErrorParser_GetDescription()`
- `_XML_ComErrorHandler_UserFunction()`
- `_XML_Misc_GetDomVersion()`
- `_XML_MiscProperty_Encoding()`
- `_XML_MiscProperty_UDFVersion()`
- `_XML_Misc_Viewer()`

Some functions are explicitly marked as work in progress or not yet reviewed in the source. Test those functions against representative XML before relying on them in production workflows.
