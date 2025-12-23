# Vehicle Rental System - Database Assignment

This project implements a relational database for a Vehicle Rental System. It includes the schema definition for users, vehicles, and bookings, along with key queries for managing the system.

## Database Schema

The system is built around three core entities:

### 1. `users`
Stores information about both customers and administrators.
- `user_id`: Unique identifier (Primary Key).
- `name`: Full name of the user.
- `email`: Unique email address.
- `password`: Hashed password for authentication.
- `phone`: Contact number.
- `role`: Defines access level (`Admin` or `Customer`).

### 2. `vehicles`
Stores details of the vehicles available for rent.
- `vehicle_id`: Unique identifier (Primary Key).
- `name`: Model and brand name.
- `type`: Category (`car`, `bike`, `truck`).
- `registration_number`: Unique government plate number.
- `price`: Daily rental rate.
- `status`: Availability state (`available`, `rented`, `maintenance`).

### 3. `bookings`
Links users to vehicles for specific rental periods.
- `booking_id`: Unique transaction ID (Primary Key).
- `user_id`: References the user who made the booking.
- `vehicle_id`: References the vehicle being rented.
- `start_date` & `end_date`: Duration of the rental.
- `status`: Current state of the booking (`pending`, `confirmed`, `completed`, `cancelled`).
- `total_cost`: Calculated cost for the rental period.

## Entity Relationship Diagram (ERD)

You can view the visual Entity Relationship Diagram for this project at the following link:
[Vehicle Rental System ERD (Lucidchart)](https://lucid.app/lucidchart/29d71de5-715b-425a-a041-ada6899a5ed1/edit?viewport_loc=189%2C-251%2C2514%2C1259%2C0_0&invitationId=inv_7c41fa1c-9f5d-4a89-afc4-9f5f4bd0993f)

## SQL Queries Explanation

The `queries.sql` file contains the following operations:

### Query 1: Booking Overview
**Purpose**: Retrieves a detailed list of all bookings including customer and vehicle names.
- Uses `INNER JOIN` to fetch human-readable names from the `users` and `vehicles` tables.

### Query 2: Unbooked Vehicles
**Purpose**: Identifies vehicles that have never been booked.
- Uses a `NOT EXISTS` clause to find vehicles that don't have a corresponding entry in the `bookings` table.

### Query 3: Filter by Category
**Purpose**: Lists all vehicles of a specific type (e.g., 'car').
- Filters the `vehicles` table based on the `type` enum.

### Query 4: High-Demand Vehicles
**Purpose**: Finds vehicles that have been booked more than once.
- Uses `GROUP BY` and `HAVING` clauses to aggregate booking counts per vehicle and filter results.

## Getting Started

1. Ensure you have a PostgreSQL-compatible database.
2. Run the `queries.sql` script to create the schema, types, and execute the sample queries.
