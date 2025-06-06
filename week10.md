# Week 10
May 7, 2025
## Objectives
* Finalize and validate all API endpoints between backend and frontend
* Test end-to-end data flow: frontend ↔ backend ↔ firmware (Raspberry Pi Pico)
* Debug issues in firmware-to-backend data transmission
## Notes and Observations
* Frontend Integration:  
  * All previously developed endpoints were integrated into frontend modules
  * Endpoints tested using frontend UI: we confirmed correct JSON structures and verified database writes and reads
* Firmware Communication Testing
  * Raspberry Pi Pico successfully initiated a connection and transmitted telemetry POST data
  * Observed partial success:
    * Some entries stored correctly in Telemetry table
    * Sometimes the backend failed to receive data
* Global current_event context not always loaded properly
## Design Ideas
* On firmware POST error, Return standardized error message to aid firmware debugging
## Problems and Solutions:
* current_event unassigned, we plan to make endpoint: GET /event/current/ with fallback to default
## Outstanding Issues
* Need a system for time sync between firmware timestamps and server time
## Reflections
* Frontend devs gave great feedback on endpoint usability (naming, parameter order, return structure)
* It was satisfying to see both firmware and frontend communicate with the backend
## Next Steps
* Backend & Firmware
  * Fix and finalize firmware data POST handling
  * Design an endpoint to validate current_event value before saving telemetry
* Frontend & API
  * Implement optional query params
