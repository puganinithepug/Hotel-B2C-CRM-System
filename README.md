# Hotel B2C CRM System
This Java-based project simulates a hotel B2C CRM system, designed as a Java-based management system with full backend functionality.

Built on relational database principles, it is designed to model a real-world CRM.

With a fully implemented backend, it demonstrates how data can be effectively organized and stored in an SQL database, with a Java-based data management workflow.

**CRM - Primary Features**
- Creation and cancellation of customer reservations
- Dynamic and automated management of customers' VIP status across the database 
- Robust search tool for customer information
- Automated busness policy compliance across the database (capacity, discount, availability)

**Real-Time B2C KPI Reporting and Data Visualization**
- Bookings per month, per every type of suite available
- Expenses by month aggregated to show quarterly trends
- Seasonal trends in customer booking behavior
- SQl to Excel data visualization

**Technical Details**

Relational Schema Design & Data Modeling:
- Designed normalized multi-table schema (Guests, Reservations, Staff, Rooms, etc.)
- Modeled table inheritance (VIPGuest vs CasualGuest) and time-series consistency via DATE/TIME typing

Stored Procedure Development for Monthly Financial Reporting:
- Created MonthlyAmenityReport stored procedure to track monthly amenity usage and revenue
- Used SQL cursors, aggregates, and dynamic table generation for report creation

Trigger-Based Process Automation:
APPLYVIPDISCOUNT: Auto-upgrades guests to VIPs, applies tiered discount, and logs cost differences
ASSIGN_TO_VIP: Automatically assigns staff to VIPs based on discount tier

Query Optimization with Indexing:
- Created indexes on RoomNum, CheckIn, CheckOut, and GID to speed up availability and JOIN queries


