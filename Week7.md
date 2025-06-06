# Week 7
April 30, 2025
## Objectives
* Finalize core backend endpoints for frontend integration
* Conduct database connection tests to verify data flow
* Plan for implementation of newly requested endpoints for more specific data analytics
## Notes and Observations
* Most endpoints planned for the initial backend–frontend connection are now functional and tested
* Successfully verified data communication with the MySQL database using Django REST API
* As frontend and firmware development progressed, new data endpoints were requested, mostly focusing on retrieving and submitting analytical metrics per team and event
## Design Ideas / Upcoming Endpoints
* Endpoints to be implemented
  * Score submission from frontend (calculated)
  * Retrive energy metrics over team and event
  * Quick access to ECU IDs for telemetry mapping
## Problems and Solutions
* Some endpoints may require query optimization or aggregation logic (e.g., annotate, group_by in Django ORM)
## Outstanding Issues
* New endpoints are not yet implemented
* Frontend integration status of the existing endpoints is still ongoing — need feedback from the frontend team
## Reflections
* Backend is now mature enough to support interactive and data-driven UI from the frontend
* Feeling more confident using Django’s path routing and class-based views for REST API development
## Next Steps
* Implement all newly listed endpoints using class-based views or viewsets
* Ensure serializers are properly defined
* Test endpoints with sample team/event data for different scenarios
* Begin documenting the API
* Sync with frontend to check how the data will be visualized (e.g., chart.js, line graphs)
