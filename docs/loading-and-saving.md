# Loading, creating, and saving documents

## Create a DOM document

Use `_XML_CreateDOMDocument()` before loading XML:

```vb
Local $oXmlDoc = _XML_CreateDOMDocument(Default, "UTF-8")
If @error Then Return SetError(@error, @extended, 0)
```

Passing `Default` lets the UDF search for an available MSXML version. You may also request a specific supported DOM version.

The optional root parameter creates the document element immediately:

```vb
Local $oXmlDoc = _XML_CreateDOMDocument(Default, "UTF-8", "configuration")
```

## Load from a file

```vb
_XML_Load($oXmlDoc, $sXmlFile, "", False, True)
```

Important parameters:

- namespace declaration string,
- `validateOnParse`,
- `preserveWhiteSpace`.

The function requires an existing DOMDocument object and returns that object on success.

## Load from a string

```vb
Local $sXml = "<root><item>value</item></root>"
_XML_LoadXML($oXmlDoc, $sXml, "", False, True)
```

Disable validation when loading ordinary XML that does not include a DTD or schema relationship requiring parser validation.

## Create a new XML file

`_XML_CreateFile()` creates a DOM document, adds the XML declaration and root element, and saves it to disk:

```vb
Local $oXmlDoc = _XML_CreateFile(@ScriptDir & "\example.xml", "root", "UTF-8")
```

The function fails if the target file already exists. Delete, rename, or explicitly manage the existing file before calling it.

## Save a document

```vb
_XML_SaveToFile($oXmlDoc, @ScriptDir & "\result.xml")
```

`_XML_SaveToFile()` also rejects an existing destination. This protects files from silent replacement, but the caller must implement the desired overwrite policy.

## Formatting

Use `_XML_Tidy()` to generate indented XML text:

```vb
Local $sFormattedXml = _XML_Tidy($oXmlDoc, "UTF-8")
```

Passing `-1` omits the XML declaration. `_XML_Tidy()` uses MSXML SAX components and `ADODB.Stream`, so those COM components must be available.