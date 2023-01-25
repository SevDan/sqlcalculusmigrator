# SqlCalculusMigrator - only concept yet

Sql Calculus Migrator is database schema migration engine 


## Concept

The idea of sql calculus migrator is engine for database schema migrations with automatic order inference based on migration expressions preconditions and postconditions analysis

## Todo

Supposed engine components: 
1. SQL expressions analysis calculator - should analyse any ansi sql expression and returns correct preconditions and postconditions
Preconditions := Set/List of 'Precondition'
Precondition := Predicative function (returns true or false) describes state requirement to expression execution (i.e. 'not exists table A' for 'CREATE TABLE A' expression) and sql script describes this function
Postconditions := Set/List of 'Postcondition'
Postcondition := Predicative function (returns true or false) describes state requirement that would be declared as 'true' after expression execution (i.e. 'exists table A' for 'CREATE TABLE A') and sql script describes this function
So, Precondition & Postcondition can be interpretated as expression function type parameter and effect: sqlExpression: DBState(Precondition=true) -> DBState(Postcondition:=true)
2. Expressions order engine - should inference any correct order for given migration sql expressions or show understandable reason why order cannot be inferenced (i.e. for 2 expressions 'create table A', 'drop table A' the only correct order is create expr. first and drop expr. second)
3. User interface - different usage ways:
3.1. Execute expressions in inferenced order with preconditions & postconditions checks and log database changesets (as standard database migration tool)
3.2. Show user inferenced order & compare with current configured (based on names/dates/etc.), show suggestions to correct it or warnings (as migrations linting tool)
4. Backward migrations generator
5. Locks/locks free algo for multiple instances running

## Needs

1. Embedded Prolog-like solver for expressions order engine 
2. SQL Syntax & Semantics parser
3. Database connectors
