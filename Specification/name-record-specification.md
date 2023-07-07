# Name Record Specification

Names are associated with individuals. A `name record` contains details of a person's name. Multiple name records may be associated with a single individual, such as birth names, married names, stage names, pen names, nicknames and aliases. One of these may be set as a preferred name in a `person record`.

## Name Record Content

Name records are held in the `name` table. A name record contains the following:

- `name.id` (required): unique numerical identifier for the `name record`
- `name.person` (required): unique numerical reference to an associated `person record`
- `name.type` (required): type of name as defined by a `nameType record`
- `name.prefix` (optional): prefixed title
- `name.forename` (optional): first and middle names, given names, et cetera
- `name.surname` (optional): last name, family name, et cetera
- `name.suffix` (optional): suffixed title
- `name.postnominals` (optional): postnominal letters
