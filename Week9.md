# Week 9
May 14, 2025
## Objectives
* Update endpoints that rely on the old schema to maintain backend stability
* Begin implementation and testing of firmware integration via a POST endpoint
* Plan for global “current event” context variable to link telemetry entries properly
## Notes and Observations
* Database Schema Update:
  * Schema adjusted to support more precise and conflict-free telemetry entrie
  * Added a new unique ID field (id = models.AutoField(primary_key=True) or UUID)
  * All affected models and foreign key relationships were updated accordingly
* Endpoind Updates:
  * Several endpoints refactored to align with new schema (especially those using event_id, ecu_id, etc.)
  * Ensured backward compatibility where feasible to avoid breaking frontend views
* Firmware Integration (Raspberry Pi Pico):
  * Created a Django view to handle firmware data that Accepts POST requests with status, id (ECU UUID), and data array
  * Supports both "data" and "reconnection" modes
  * Telemetry data is parsed as CSV-style rows: voltage, energy, timestamp
  * Each entry is saved with the current active event_id, which is expected to be managed as a global variable
## Design Ideas
* Store current_event in Django cache (from django.core.cache import cache) or DB session
* Build a simple admin endpoint to set and get the current event (POST /api/event/set-current/, GET /api/event/current/)
## Problems and Solutions
* ECU ID not always provided, so we auto-generate UUID using uuid4() when absent
* There could be incomplete CSV line, so we add validation and skip logic for bad entries
## Outstanding Issues
* Global current_event not yet finalized or securely managed
* New endpoints are required based on frontend analytics needs (charts, summaries, etc.)
* Firmware reconnection logic is still rudimentary
## Reflections
* Integrating firmware brought a lot of insight into how live data flows through the stack
* Django’s robustness makes handling external hardware inputs relatively straightforward once schema is settled
## Next Steps
* Firmware & Backend
  * Finalize schema migration & confirm all endpoints are compatible
  * Clean up receive_data() view and factor into class-based view or APIView
* Frontend & Global State
  * Implement an API or session handler to set current_event from frontend
  * Add fallback if event is not set (error message, logging)
