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

## Names

### Schema — "names" table

| Column         | Value                |
|----------------|----------------------|
| `id`           | `PK INT`: names.id   |
| `person`       | `FK INT`: persons.id |
| `type`         | `STRING`             |
| `title`        | `STRING`             |
| `forenames`    | `STRING`             |
| `surname`      | `STRING`             |
| `suffix`       | `STRING`             |
| `postnominals` | `STRING`             |

## Facts

### Events

### Attributes

### Dual-type facts

### Schema — "facts" table

| Column               | Value                  |
|----------------------|------------------------|
| `id                  | `INTEGER PK facts.id`  | 
| `category            | `STRING`               |
| `type                | `STRING`               |
| `dateRange           | `STRING`               |
| `startDate           | `STRING`               |
| `startDatePrecision` | `STRING`               |
| `endDate`            | `STRING`               |
| `endDatePrecision`   | `STRING`               |
| `place`              | `INTEGER FK places.id` |

## Places

### Schema "places" table

| Column      | Value                  |
|-------------|------------------------|
| `id`        | `INTEGER PK places.id` |
| `root`      | `INTEGER`              |
| `name`      | `STRING`               |
| `locality`  | `STRING`               |
| `district`  | `STRING`               |
| `region`    | `STRING`               |
| `country`   | `STRING`               |
| `current`   | `INTEGER FK places.id` |
| `latitude`  | `REAL`                 |
| `longitude` | `REAL`                 |
