# Special Instructions

## Update your progress

- After you have completed a task, you must update the status of features and requirements met in the `progress.md` document

## Formulas need to be escaped  

this is valid : TEXT(TODAY()) &amp; &apos;-&apos; &amp; LPAD(TEXT(TODAY()),2)
this is invalid: TEXT(TODAY()) & '-' & LPAD(TEXT(TODAY()),2)

## Creating apex classes

- Do not use reserved words, such as `date` and `dateTime`, as variable names in Apex classes
- Tests must only use `assert`, `assertEquals`, or `assertNotEquals` to assert test responses
