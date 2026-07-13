# Validation and transforms

## XSD validation

Use `_XML_ValidateFile()` to validate an XML file against an XSD schema.

The function requires:

- the XML file path,
- the namespace used by the schema,
- the XSD file path.

Check `@error` and `@extended` after validation. The current UDF implementation validates files rather than an already loaded in-memory document.

## XSLT transformation

Use `_XML_Transform()` to apply an XSL stylesheet to a DOM document.

Important behavior:

- the XSL file must exist,
- the function creates MSXML XSL template and free-threaded DOM objects,
- the original `$oXmlDoc` reference is replaced with the transformed document on success.

Because the document object is overwritten, keep a separate copy when the original XML must remain available.

## Formatting XML

Use `_XML_Tidy()` to return an indented XML string.

- Pass `-1` to omit the XML declaration.
- Pass `Default` to use the UDF encoding setting.
- A specific encoding can be supplied as a string.

`_XML_Tidy()` uses `MSXML2.SAXXMLReader`, `MSXML2.MXXMLWriter`, and `ADODB.STREAM`. Object creation or encoding failures are reported through the UDF error model.

## Security considerations

Treat XML, XSD, and XSL files from untrusted sources as potentially unsafe. Review DTD, external entity, and external resource behavior before processing untrusted documents. The UDF may change MSXML parser properties while loading documents, so applications with strict security requirements should explicitly verify the resulting DOM configuration.
