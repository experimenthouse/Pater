# Pater: Family History for the 21st Century

## Introduction

## Persons

### Schema — "persons" table

| Column    | Value               |
|---------|-----------------------|
| `id`    | `INTEGER PK`          |
| `name`  | `INTEGER FK names.id` |
| `birth` | `INTEGER FK facts.id` |
| `death` | `INTEGER FK facts.id` |

- `id`: unique, auto-incrementing integer identifying the person in the `persons` table.
- `name`: unique integer referencing the person's preferred name in the `names` table.
- `birth`: unique integer referencing the person's preferred date and place of birth in the `facts` table.
- `death`: unique integer referencing the person's preferred date and place of death in the `facts` table.

## Names

### Schema — "names" table

| Column         | Value                   |
|----------------|-------------------------|
| `id`           | `INTEGER PK names.id`   |
| `person`       | `INTEGER FK persons.id` |
| `type`         | `STRING`                |
| `prefix`       | `STRING`                |
| `forenames`    | `STRING`                |
| `surname`      | `STRING`                |
| `suffix`       | `STRING`                |
| `postnominals` | `STRING`                |

- `id`: unique, auto-incrementing integer identifying the name in the `names` table.
- `person`: unique integer referencing the associated person in the `persons` table.
- `type`: string containing one of a predefined but extensible name types such as "birth", "full", "married", "nickname", "alias" or "variant".
- `prefix`: string containing a person's prefixed title such as "Sir", "Dame", "King", "Queen" or "Dr".
- `forenames`: string containing a person's given names (first and middle names).
- `surname`: string containing a person's surname (last name).
- `suffix`: string containing a person's suffixed title such as "Baroness Spencer-Churchill".
- `postnominals`: string containing a person's postnominal letters such as "DFC & bar".

## Facts

### Attributes

### Events

### Dual-type facts

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
