# Person Record Specification

The person is the fundamental unit in Pater. A `person record` identifies a unique individual.

## Person Record Content

Person records are held in the `person` table. A person record contains the following:

- `person.id` (required): unique numerical identifier for the `person record`
- `person.name` (optional): unique numerical reference to a preferred `name record`
- `person.birth` (optional): unique numerical reference to a preferred birth `fact record`
- `person.death` (optional): unique numerical reference to a preferred death `fact record`

## Person Table SQL
```
CREATE TABLE "persons" (
	"id" INTEGER NOT NULL UNIQUE, PRIMARY KEY("id" AUTOINCREMENT),
	"name" INTEGER UNIQUE, FOREIGN KEY("name") REFERENCES "names"("id"),
	"birth" INTEGER UNIQUE, FOREIGN KEY("birth") REFERENCES "facts"("id"),
	"death" INTEGER UNIQUE, FOREIGN KEY("death") REFERENCES "facts"("id")
);
```
