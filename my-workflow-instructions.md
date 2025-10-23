# Notes for Agentforce for Developers

## Update your progress

- keep track of the status of features and requirements met in the `progress.md` document

## Formulas need to be escaped  

this is valid : TEXT(TODAY()) &amp; &apos;-&apos; &amp; LPAD(TEXT(TODAY()),2)
this is invalid: TEXT(TODAY()) & '-' & LPAD(TEXT(TODAY()),2)

## Creating Custom objects

- Never create a custom setting. Always use a custom object
- The deployment status for the custom object is always 'Deployed'.
- Always specify a sharing model value for the Custom Object
- Never specify 'relationshipOrder' for a CustomField of type Lookup
- Text fields should have a length of 255

## Creating apex classes

- Never use reserved identifier names, such as `date` and `dateTime`, as variable names in Apex classes
- Tests should only use assert, assertEquals, and assertNotEquals to assert test responses
