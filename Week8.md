# Week 8
May 7, 2025
## Objectives
* Continue building more GET endpoints to enhance data delivery for frontend UI components
* Analyze telemetry data behavior across firmware/frontend/backend integration to determine database schema needs
## Notes and Observations
* Developed additional GET endpoints focused on improving data accessibility for dashboards or live displays, especially for telemetry data.
* These endpoints aim to support time-series charts, team comparisons, and real-time metric previews
* While integrating with firmware and frontend, discovered that telemetry entries could not be uniquely identified by ECU ID alone
* A new primary key is required for the Telemetry table to avoid data collisions and improve precision
## Design Ideas
* Consider adding a new unique id field to the Telemetry table
* Adjust Django models and corresponding migrations to reflect changes in schema
## Outstanding Issues
* Schema changes will require coordinated updates across backend, frontend, and firmware to ensure compatibility
* API responses may need to be adapted to reflect new telemetry structure
* Will need to write and test Django migrations carefully to avoid data loss
## Reflections
* Learned the importance of well-thought-out primary key design in sensor-based data systems
* Anticipate that future changes may also require indexed queries for faster telemetry access
## Next Steps
* Modify the Telemetry model to use a key that includes time context
* Test endpoints after schema modification to confirm everything still works
