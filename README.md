# Pater: Family History for the 21st Century

Pater will be a free and open-source genealogy and family history application for macOS and other Apple platforms.

## The Problem

There is currently no powerful, user friendly and aesthetically pleasing genealogy application for macOS.

Popular existing applications include:

* MacFamilyTree (proprietary), and
* Gramps (FOSS).

MacFamilyTree is aesthetically pleasing and superficially user-friendly. It has been developed for macOS and looks consistent with other apps. However, data entry is slow and inefficient, and users are restricted to the almost arbitrary choices of developers when it comes to what data can be input or output and where. Improvements have been made between different versions, but at a hefty price and still with limited flexibility.

Gramps is powerful and cross-platform. However, it is ugly and unintuitive, and does not look like a macOS app. Data entry is also slow and inefficient, though users are not as restricted to the same degree as in MacFamilyTree. The flexibility of Gramps is	its greatest strength.

## Languages

Pater will be written in Swift and SwiftUI with a SQLite database for storing genealogical data using SQLite.swift.

## Data types

- `Person`

### `Person` data type

The `Person` data type consists of five fields:

| Field       | Description                            |
|-------------|----------------------------------------|
| `person_id` | Unique identifier                      |
| `name_id`   | Unique identifier of `Name` data type  |
| `birth_id`  | Unique identifier of `Event` data type |
| `death_id`  | Unique identifier of `Event` data type |
| `sex`       | Defaults to "U"                        |

#### Name, Birth, Death

The `name_id`, `birth_id` and `death_id` set defaults for lists and profile headers. A person may have multiple names (for example, a birth name, married name and stage name), and birth and death events where multiple possibilities exist due to uncertainty. By referencing these details in other tables, users can choose and change which details appear as the default in lists and profile headers.

#### Sex

Sex is the biological sex (or assigned sex) of the individual. This could be "F" for female, "I" for intersex, "M" for male, or "U" for unknown (default).

> Note: gender or gender identity can be input as an `Attribute` data type.

### `Name` data type

The `Name` data type consists of nine fields:

| Field          | Description                             |
|----------------|-----------------------------------------|
| `name_id`      | Unique identifier                       |
| `person_id`    | Unique identifier of `Person` data type |
| `name_type`    | "birth name", "married name", etc       |
| `surname`      | Surname                                 |
| `forenames`    | Forenames                               |
| `name_prefix`  | "Dr", "Sir", etc                        |
| `name_suffix`  | "Duke of ...", "Earl of ...", etc       |
| `postnominals` | "MBE", "PhD", etc                       |
| `description`  | Notes about the name                    |

### `Event` data type
