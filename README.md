# Hotel B2C CRM System
This Java-based project simulates a hotel B2C CRM system, designed as a Java-based management system with full backend functionality.

Built on relational database principles, it is designed to model a real-world CRM.

With a fully implemented backend, it demonstrates how data can be effectively organized and stored in an SQL database, with a Java-based data management workflow.

**Core Capabilities**

Guest & Reservation Management:

- Real-time reservation creation and cancellation with immediate consistency across concurrent operations
- Dynamic and automated management of customers' VIP status across the database -  automated tier upgrades based on booking history and spend
- Robust customer search with indexed queries for fast information retrieval
- Automated business policy compliance across the database -  capacity constraints, discount application, and availability validation enforced at the database layer

Real-Time KPI Reporting & Analytics:

- Bookings per month, per every type of suite available
- Expenses by month aggregated to show quarterly trends
- Seasonal trends in customer booking behavior
- SQL-to-Excel data visualization pipeline

**Technical Architecture**

**Data Pipeline Note:** There should be an ETL (for structured transaction logs) or ELT (for unstructured data such as customer calls) processes would feed data from booking systems and customer interactions into the OLTP layer. In this case loaddata.sql and create_vip_log.sql perform the initial data population and transaction logging.

**OLTP Layer — Real-Time Transactional Operations**

_Relational Schema Design & Data Modeling_

- Normalized multi-table design (Guests, Reservations, Staff, Rooms, etc.) with proper referential integrity
- Table inheritance modeling (VIPGuest vs CasualGuest) with DATE/TIME typing for temporal consistency

_Stored Procedure Development for Monthly Financial Reporting:_

- Created MonthlyAmenityReport stored procedure to track monthly amenity usage and revenue using SQL cursors, aggregates, and dynamic table generation for financial reporting

_Trigger-Based Process Automation:_

- APPLYVIPDISCOUNT auto-upgrades guests to VIPs, applies tiered discount, and logs cost differences
- ASSIGN_TO_VIP automatically assigns staff to VIPs based on discount tier

_Operational Characteristics:_

- Real-time guest transactions — check-ins, check-outs, reservations, and room assignments executed with immediate consistency
- VIP customer automation — triggers automatically apply discounts and assign concierge staff when high-value guests interact with the system
- Concurrent operations — multiple front-desk staff simultaneously accessing and modifying guest records without conflicts
- Transaction logging — audit trails capture all changes for compliance and dispute resolution

**ROLAP Layer — Analytical Reporting**

_Query Optimization with Indexing:_

- Created indexes on RoomNum, CheckIn, CheckOut, and GID to speed up availability and JOIN queries

_Real-Time Analytics:_

- Query-based reporting — aggregations and dimensional analysis run directly against operational tables (hotel occupancy, revenue per room type, VIP patterns)
- Data exports — results exported to CSV/Excel (q6-vis1.xlsx, q6-vis2.csv) for visualization and business intelligence
- Real-time insights — analytics reflect current operational state, crucial for hotel management decisions

**Key Files	- Functionality**
_Database Schema: createtbl.sql, droptbl.sql_
- Well-designed relational schema with table structure and cleanup
_Data & Operations (ETL/ELT): loaddata.sql, create_vip_log.sql_
- Initial data population and transaction logging for audit trails
_Business Logic (OLTP):	vip_discount_trigger.sql, vip_assistant_assignment.sql_
- Database triggers enforcing VIP customer rules and staff assignments automatically
_Application:	databaseApp.java_
- Menu-driven Java interface connecting to the database for hotel operations
_Analytics (ROLAP):	q6-vis1.xlsx, q6-vis2.csv_
- ROLAP-style reporting with data exports for visualization and analysis
_Documentation:	Entity Relationship Diagram.pdf. Hotel Management System and Database Analysis Report_
- Professional documentation showing system design and analysis
