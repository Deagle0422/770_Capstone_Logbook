# Week 4
26 March 2025
## Objectives
* Define and implement Django models based on previously designed schema
* Deploy database structure through migrations
* Research Django REST framework and how to expose backend data to frontend
## Notes and Observations
* Successfully created Django models corresponding to the initial database schema:
  * Models for Telemetry, Entries, Teams, Score, Event, and Competition were implemented using Django's ORM
* Ran initial migrations and verified the local MySQL database was populated with correct structure
* Explored Django REST Framework (DRF) and how it enables frontend-backend integration via JSON-based APIs
* DRF simplifies data serialization and route creation
## Design Ideas
* Plan to create RESTful API endpoints to expose key data models to the frontend (e.g., list teams, retrieve scores)
* Use DRF's built-in serializers for rapid development
* Start with basic GET endpoints before adding POST/PUT
## Problems and Solutions
* Encountered a small issue with enum handling in Django — resolved by using choices in Django model fields
* Needed to tweak MySQL configuration for Django to connect; solution involved enabling mysqlclient and adjusting settings in settings.py
## Outstanding Issues
* No URLs or views have been created yet — frontend cannot access data as of now
* Serializers for models not yet written
## Reflections
* Django’s ORM makes data structure management intuitive
* Need to improve familiarity with URL routing and JSON formatting for APIs
## Next Steps
* Create URL routes for key models using Django urls.py
* Implement serializers for Team, Score, and Telemetry models
* Build basic views to return JSON responses to frontend requests
* Test API endpoints with browser
* Coordinate with frontend team to understand what data they need exposed first
