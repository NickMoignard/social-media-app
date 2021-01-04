 Rich Text Editor
 Trix

* Database Ideas
Master DB + Read Replicas + Analytics DB

`
database.yml

development:
  primary:
    database: my_primary_db
    user: root
  primary_replica:
    database: my_primary_db
    user: ro_user
    replica: true
  secondary:
    database: my_secondary_db
    user: root
  secondary_replica:
    database: my_secondary_db
    user: ro_user
    replica: true

model.rb

class Model < ApplicationRecord
    self.abstract_class = true
    connects_to database: {
        writing: :animals_primary,
        reading: :animals_replica
    }
end


`
