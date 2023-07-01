# Pater: Family History for the 21st Century

## Introduction

## Persons

The person is the fundamental unit in Pater. Names, facts and relationships pertain to persons.

### Person record

A person record identifies a unique individual, their preferred name, and the preferred details of their dates and places of birth and death. Person records are held in the persons table.

- `person.id` is the unique and persistent numerical identifier of the person record.
- `person.name` is the unique numerical identifier of the preferred name record to be associated with an individual.
- `person.birth` is the unique numerical identifier of the preferred fact record containing details of the individual's birth.
- `person.death` is the unique numerical identifier of the preferred fact record containing details of the individual's death.

### Schema — "persons" table

```
CREATE TABLE "persons" (
	"id" INTEGER NOT NULL UNIQUE, PRIMARY KEY("id" AUTOINCREMENT),
	"name" INTEGER UNIQUE, FOREIGN KEY("name") REFERENCES "names"("id"),
	"birth" INTEGER UNIQUE, FOREIGN KEY("birth") REFERENCES "facts"("id"),
	"death" INTEGER UNIQUE, FOREIGN KEY("death") REFERENCES "facts"("id")
);
```

## Names

A name is a word or set of words by which a person is known. Most people are given a name at or shortly after birth, but names can change through events such as adoption or marriage, and multiple . Pater allows a person to have multiple names, with a preferred name set in the person record (see above).

### Name record

A name record identifies a unique name, associates it with a person record, and includes details about the name.

- `name.id` is the unique and persistent numerical identifier of the name record.
- `name.person` is the numerical identifier of the associated person record.
- `name.type` identifies the type of name, such as "full", "birth", "nickname", "married", "alias", "variation", "stage" or "pen". Name types are defined in the nameTypes table.
- `name.prefix` may contain a prefixed title, such as "King", "Queen", "Sir" or "Dame".
- `name.forenames` may contain one or more given names (first and middle names).
- `name.surname` may contain a last name (or family name).
- `name.suffix` may contain a suffixed title, such as "Baroness Spencer-Churchill".
- `name.postnominals` may contain postnominal letters, such as "DFC & Bar".

### Schema — "names" table

```
CREATE TABLE "names" (
	"id" INTEGER NOT NULL UNIQUE, PRIMARY KEY("id" AUTOINCREMENT),
	"person" INTEGER, FOREIGN KEY("person") REFERENCES "persons"("id")
	"type" INTEGER, FOREIGN KEY("type") REFERENCES "nameTypes"("id"),
	"prefix" TEXT,
	"forenames" TEXT,
	"surname" TEXT,
	"suffix" TEXT,
	"postnominals" TEXT
);
```

## Facts

A fact is anything known about a person. Facts can be divided into things that are true about a person ("attributes") and things that happened to a person ("facts"). Some facts may have properties of both. Pater avoids prescribing whether a fact is an attribute or an event, leaving this to the user.

### Attributes, events and dual-type facts

An attribute is something that is true about a person. Attributes tend to be more or less immutable; they have a permanent or virtually permanent quality. Thus, attributes will include eye colour, hair colour, height, sex, religion, and so on. Attributes are generally less concerned with date or place as they are with a particular value, unless that value is a date or place. Hence, "eye colour" may have the value "blue", but "residence" may have the value "London".

An event is something that happened to a person. Events are _always_ immutable; they are historical facts that cannot change. Thus, events will include births, deaths, marriages, retirements, funerals and so on. Events occur on a date or dates and typically, but not always, at a place. They do not have a value _per se_ (the value is the type of event), but may have a description. Hence, "birth" may occur in "1901" at "London", but "retirement" may occur in "1970" without a place, but a description of the relevant occupation and employer.

Some facts may behave like both an event and an attribute. For example:

- An event "birth" with a date and place may correspond to the attributes "birthday" and "birthplace"
- An attribute "residence" with a date and place may be better treated as an event.

### Fact record

A fact record identifies a unique fact, when it occurred or was true, where it occurred or was true, and any additional details as required.

- `fact.id` is the unique and persistent numerical identifier of the fact record. 
- `fact.category` identifies whether the record is an "
- `fact.type`
- `fact.dateRange`
- `fact.startDatePrecision`
- `fact.startDate`
- `fact.endDatePrecision`
- `fact.endDate`
- `fact.movement`
- `fact.place`
- 
### Schema — "facts" table

| Column               | Value                  |
|----------------------|------------------------|
| `id`                 | `INTEGER PK facts.id`  | 
| `category`           | `STRING`               |
| `type`               | `STRING`               |
| `dateRange`          | `STRING`               |
| `startDatePrecision` | `STRING`               |
| `startDate`          | `STRING`               |
| `endDatePrecision`   | `STRING`               |
| `endDate`            | `STRING`               |
| `place`              | `INTEGER FK places.id` |

- `id`: unique, auto-incrementing integer identifying the fact in the `facts` table.
- `category`: string containing either "attribute", "event" or "both".
- `type`: string containing one of a predefined but extensible fact types such as "birth", "death", "marriage", "height" or "residence".
- `dateRange`: string containing either "none", "between" or "from".
- `startDatePrecision`: string containing "on", "about", "before" or "after".
- `startDate`: string in YYYY-MM-DD format representing the first or only date on which an event happened or attribute was true.
- `endDatePrecision`: string containing "on", "about", "before" or "after".
- `endDate`: string in YYYY-MM-DD format representing the last date on which an event happened or attribute was true.

## Places

### Schema "places" table

| Column      | Value                  |
|-------------|------------------------|
| `id`        | `INTEGER PK places.id` |
| `current`   | `INTEGER`              |
| `name`      | `STRING`               |
| `locality`  | `STRING`               |
| `district`  | `STRING`               |
| `region`    | `STRING`               |
| `country`   | `STRING`               |
| `current`   | `INTEGER FK places.id` |
| `latitude`  | `REAL`                 |
| `longitude` | `REAL`                 |

- `id`: unique, auto-incrementing integer identifying the place in the `places` table.
- `current`: boolean indicating whether the place details are those of the current place.
- `name`: string containing the shorthand name for the place.
- `locality`: string containing the name of the town, village, suburb, or similar entity.
- `district': string containing the name of the district, county or similar entity.
- `region`: string containing the name of the region, province, state, territory or similar entity.
- `country`: string containing the name of the sovereign state, dependent state or similar entity.
- `latitude`: floating point containing the latitude of the place.
- `longitude`: floating point containing the longitude of the place.
