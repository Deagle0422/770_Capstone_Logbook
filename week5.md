# Week 5
2 April 2025
## Objectives
* Implement basic GET and PUT API endpoints using Django REST Framework
* Ensure JSON data is correctly transferred between frontend and backend
* Begin building the RESTful structure of the backend to support data operations
## Notes and Observations
* Successfully developed and tested basic GET and PUT methods for selected models
* JSON data communication between frontend and backend is functioning correctly
* Additional endpoints created in preparation for upcoming frontend integration (e.g., endpoints for teams, scores, and telemetry)
* Used serializers to transform Django model data into JSON format
* Testing showed proper parsing of both incoming and outgoing data
## Design Ideas
* All endpoints designed following REST principles (clean URLs, appropriate methods)
## Problems and Solutions
* Faced minor serializer validation errors when testing PUT method — fixed by explicitly defining required fields in serializers
## Outstanding Issues
* Not all models have endpoints yet
* No authentication or security applied to APIs
* Connection between frontend components and backend still pending
## Reflections
* Solid progress this week; backend is starting to look production-ready
* Very satisfying to see JSON data flow correctly between client and server
## Next Steps
* Develop more endpoints (e.g., for Event and Competition models)
* Begin frontend integration — test actual data fetch using React/Vue/other framework
* Implement basic error handling and validation on backend side
* Sync with frontend team to finalize required data endpoints
