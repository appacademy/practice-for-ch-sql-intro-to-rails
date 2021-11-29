# Homework

**Create a simple Rails project and try out what you've learned so far!**

In this project you'll be creating a simple Rails project to model the
relationships between people and houses. By the end of this project, each
`Person` will live in a house, and each `House` will have an `address`. You will
be able to call `House.residents` and get a list of the `people` that live in
that `House`. You will also be able to call `Person.house` and get the `House`
that that `Person` lives in.

**Pro Tip**: Refer to the Readings **often**

## Phase 1: `rails new`

- Create a new rails project using PostgreSQL.
  - Remember to use the `-G`, `--minimal`, and `-d` flags when creating your
    project!
  - Remember to create the database!
  - Remember that you need to have Postgres running in the background!

## Phase 2: Create Models and Migrations

- Create a `Person` model and a `people` table (each `Person` should have a
  `name` and a `house_id`)
  - You will need to create and run a Migration for each model. (Refer to the
    Migration reading if you need a reminder!)
  - You will need to create a file called `model_name.rb` in `/app/models/` for
    each model.
  - For each model, you should validate the presence of each attribute that the
    model can have. (Refer to the Basic Validations reading for an example.)
- Create a `House` model and a `houses` table (each `House` should have an
  `address`).

## Phase 3: Create associations

- Create Associations for `Houses` with `People` such that `Houses` can have
  many `#residents` and each `Person` belongs to a `#house`. (Refer to the
  readings for `belongs_to` and `has_many`.)
  - This relies on your specifying the correct `primary_key`, `foreign_key`, and
    `class_name`; otherwise, when you call `House.residents`, Rails will assume
    you are following conventions and look for a `residents` table rather than a
    `people` table!

## Phase 4: Try it out!

- Use the `rails console`--search for `rails console` in the ORM Review reading
  to find out more about it--to create some data and run some basic queries.
- You should be able to run the following:

  ```ruby
  house = House.new(address: '308 Negra Arroyo Lane')
  house.save!
  
  person = Person.new(name: 'Walter White', house_id: house.id)
  person.save!

  Person.first.house # House with address: "308 Negra Arroyo Lane"
  House.first.residents # array containing Person with name: "Walter White"
  ```