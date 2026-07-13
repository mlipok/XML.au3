# Troubleshooting

## DOM document cannot be created

Symptoms:

- `_XML_CreateDOMDocument()` returns `$XML_RET_FAILURE`.
- `@error` is `$XML_ERR_OBJCREATE` or `$XML_ERR_DOMVERSION`.

Check:

- whether the requested MSXML version is installed,
- whether the version number is supported by the UDF,
- whether `Default` should be used to let the UDF detect an available version.

## XML cannot be loaded

Check:

- the full file path,
- file existence and access permissions,
- XML well-formedness,
- the `validateOnParse` setting,
- the encoding declaration versus the actual file encoding.

For `$XML_ERR_PARSE`, call `_XML_ErrorParser_GetDescription($oXmlDoc)` before replacing or releasing the document object.

## XPath syntax error

`_XML_SelectNodes()` and `_XML_SelectSingleNode()` return `$XML_ERR_XPATH` for invalid XPath syntax.

Verify:

- quoting inside predicates,
- matching brackets,
- absolute versus relative paths,
- namespace prefixes and `SelectionNamespaces` declarations.

## No nodes match

A valid XPath that finds nothing is different from an invalid XPath:

- `_XML_SelectSingleNode()` may return `$XML_ERR_NONODESMATCH`.
- `_XML_SelectNodes()` may return `$XML_ERR_EMPTYCOLLECTION`.

Treat an empty result as normal application state when the node is optional.

## Namespace documents return no results

Register prefixes through the namespace string supplied to `_XML_Load()` or `_XML_LoadXML()`. Use those prefixes in XPath expressions, including for a document that declares a default namespace.

## Saving fails because the file exists

`_XML_SaveToFile()` refuses to overwrite an existing file. Delete, rename, or archive the target explicitly before saving.

This behavior is intentional and should be handled by the calling script.

## Attributes are rejected

Functions that accept attribute tables expect two columns:

- `$XMLATTR_COLNAME`
- `$XMLATTR_COLVALUE`

Check the array dimensions and ensure names and values are strings where required.

## Tidy operation fails

`_XML_Tidy()` depends on:

- `MSXML2.SAXXMLReader`,
- `MSXML2.MXXMLWriter`,
- `ADODB.STREAM`.

Inspect `@error` and `@extended` to identify which COM component or encoding operation failed.

## Preserve error state immediately

Read or store `@error` and `@extended` immediately after the UDF call. Any later function call can overwrite them.
