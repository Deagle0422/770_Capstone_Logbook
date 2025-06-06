# Week 3
Wednsday 19 March
## Objectives
* Decide on backend framework and programming language
* Outline database structure for the project
* Plan implementation tasks for next week
## Notes and Observations
* Met with Marcellin to discuss backend direction
* Final decisions made for tech stack:
  * Framework: Django
  * Language: Python
  * Database: MySQL (local for now, may migrate to cloud-based later)
* Django selected due to familiarity, strong ORM, and rapid development capabilities
* Initial database schema drafted to cover telemetry, team data, event structure, and scoring system
* Database will track multiple aspects of a competition including team entries, telemetry from ECUs, and scoring
## Design Ideas
* Backend will use Django REST Framework to provide API access
* Data schema structured to support future analytics on energy and scoring
* Consideration for future modularity in case more event types or telemetry metrics are added
## Problems and Solutions:
* None so far. Discussions were productive and aligned
## Outstanding Issues:
* Need to explore Django ORM integration with MySQL
* Ensure schema constraints (e.g., foreign key relationships) are correctly set in Django models
## Reflections
* Great collaborative session with clear outcomes\
* Raw schema design is shaping up well but needs model translation and testing
## References
* Django Docs: https://docs.djangoproject.com/en/5.2/
* MySQL Docs: https://dev.mysql.com/doc/
## Next Steps
* Implement the database schema in Django models
* Set up Django project and test local MySQL connection
* Explore Django ORM: how it handles foreign keys and enum types
* Understand routing and views in Django to prepare for API integration
* Sync with frontend team to understand their data needs
## Raw Database Schema
Table Telemetry {
  id INTEGER [PRIMARY KEY]
  event_id INTEGER
  ecu_id VARCHAR
  time TIMESTAMP
  energy FLOAT
  power FLOAT
  voltage FLOAT  // calculated at end
  current FLOAT
}

Table Entries {
  team_id INTEGER [PRIMARY KEY]
  competition_id INTEGER [PRIMARY KEY]
  ecu_id INTEGER
}

Table Teams {
  id INTEGER [PRIMARY KEY]
  team_name VARCHAR
  school TEXT
  vehicle_class ENUM
  vehicle_type ENUM
}

Table Score {
  team_id INTEGER [PRIMARY KEY]
  event_id INTEGER [PRIMARY KEY]
  start_time INTEGER
  end_time INTEGER
  total_duration INTEGER
  score INTEGER
  average_energy FLOAT
}

Table Event {
  id INTEGER [PRIMARY KEY]
  competition_id INTEGER [NOT NULL]
  event_type VARCHAR
}

Table Competition {
  id INTEGER [PRIMARY KEY]
  name TEXT
  date DATETIME
}

Ref: Entries.competition_id > Competition.id  
Ref: Entries.team_id > Teams.id  
Ref: Score.team_id > Teams.id  
Ref: Score.event_id < Event.id  
Ref: Telemetry.event_id < Event.id  
Ref: Telemetry.ecu_id < Entries.ecu_id  
Ref: Event.competition_id > Competition.id

