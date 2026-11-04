# Salon Appointment Scheduler

This project is a core component of the **freeCodeCamp Relational Database Certification**. It demonstrates the practical application of relational database design, SQL querying, and automation using Bash scripting. The system dynamically manages customers, services, and appointment bookings.

## Project Overview

The goal of this project is to build an interactive terminal-based application that allows clients to book appointments at a salon. The application communicates directly with a PostgreSQL database to check for existing customers, register new ones, and insert appointment schedules in real-time.

## Tech Stack & Skills Demonstrated

*   **Database Management:** PostgreSQL
*   **Querying Language:** SQL (Data Definition Language & Data Manipulation Language)
*   **Automation & Logic:** Bash Scripting (Shell Scripting)
*   **Concepts Applied:** Primary Keys, Foreign Keys, Table Joins, Conditional Loops, and Input Validation.

## Database Schema & Architecture

The database `salon` consists of three highly interconnected tables structured to enforce data integrity:

1.  **`services`**: Stores the available salon treatments.
    *   `service_id` (SERIAL, Primary Key)
    *   `name` (VARCHAR)
2.  **`customers`**: Stores unique client profiles.
    *   `customer_id` (SERIAL, Primary Key)
    *   `phone` (VARCHAR, Unique)
    *   `name` (VARCHAR)
3.  **`appointments`**: The junction table connecting customers to services with a specific time.
    *   `appointment_id` (SERIAL, Primary Key)
    *   `customer_id` (INT, Foreign Key referencing `customers`)
    *   `service_id` (INT, Foreign Key referencing `services`)
    *   `time` (VARCHAR)

## How the Script Works

The `salon.sh` script executes the following programmatic logic:
1.  **Displays Available Services:** Dynamically fetches and prints the list of services from the PostgreSQL database using a formatted UI loop.
2.  **Validates Service Selection:** Prompts the user to pick a service. If the input is invalid, it gracefully loops back to the service list.
3.  **Customer Lookup & Registration:** Requests the user's phone number. If the number doesn't exist in the database, the script prompts for a name and automatically registers the new customer.
4.  **Appointment Scheduling:** Prompts for the desired appointment time and inserts a new row into the `appointments` table.
5.  **Confirmation Output:** Prints a clean success message confirming the service, time, and customer name.

## How to Run & Test Locally

To test this project on your local machine, follow these steps:

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/guvengokhan
    cd fcc-relational-database-salon
    ```

2.  **Recreate the database:**
    Make sure you have PostgreSQL installed, then import the database structure using your generated SQL dump file:
    ```bash
    psql -U postgres < salon.sql
    ```

3.  **Make the script executable:**
    ```bash
    chmod +x salon.sh
    ```

4.  **Run the application:**
    ```bash
    ./salon.sh
    ```

---
*Completed as part of the Relational Database Curriculum on freeCodeCamp.*
