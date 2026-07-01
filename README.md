# FOUND_CLUB_HACKATHON


---

# 🏆 Hackathon Management System

A robust, data-driven web application built with **Streamlit** and **MySQL** to manage the end-to-end lifecycle of technical hackathons. From admin approvals and financial tracking to team formation and project submission—this system ensures data integrity through advanced SQL constraints.

DEPLOY LINK : https://foundclubhackathonworld-7rxcpwjhrm7qnqvgqsfway.streamlit.app/

---

## Key Features

### 👨‍💼 Admin Dashboard

* **Hackathon Lifecycle:** Create, Edit, and Delete hackathons with dynamic status tracking (Upcoming, Ongoing, Evaluated).
* **Team Shortlisting:** Review project ideas and approve/reject teams using a centralized review hub.
* **Finance & Sponsorship:** Parse funding requests and automatically link sponsors to specific events.
* **Workshop Management:** Schedule and assign mentors to workshops linked with active hackathons.

### 👥 Participant Portal

* **Explore & Register:** Browse events with real-time status updates and detailed event guidelines.
* **Team Hub:** Create teams (as a Lead) or request to join existing ones (max 3 members).
* **My Activities:** Track participation status, join assigned workshops, and submit projects before the deadline.

---

## 🏗️ Database Infrastructure

The system architecture utilizes a centralized relational database to manage complex data relationships across 11 tables.

* **Cloud Hosting:** The production database is hosted on **Aiven (Managed MySQL)**, ensuring high availability and allowing the Streamlit application to access real-time data from any environment.
* **Database Schema:** All table structures, initial dummy data, and relational constraints are pre-configured in the `database_techclub.sql` file provided in this repository.
* **Data Integrity:** The system uses `defaultdb` as the primary schema. It enforces strict **Foreign Key Constraints** (`CASCADE`, `SET NULL`, and `RESTRICT`) to prevent orphaned records and maintain referential integrity.

---

## Technical Architecture

### **Database Schema & Constraints**

The system follows a normalized schema to minimize redundancy. Key SQL principles implemented:

* **ON DELETE CASCADE:** Automatically cleans up child records (e.g., deleting a hackathon removes its linked teams and projects).
* **ON DELETE SET NULL:** Ensures that if a Judge or Mentor is removed, the event history remains intact.
* **ON DELETE RESTRICT:** Protects critical data, such as preventing the deletion of an Admin while they are managing active events.

### **Tech Stack**

* **Frontend:** Streamlit (Python)
* **Backend:** MySQL (Aiven Cloud)
* **Data Processing:** Pandas & Datetime API
* **Styling:** Custom CSS & HTML components for card-based UI.

---

## Logical Flows

### **1. Team Formation (Max 3 Members)**

The system ensures that no team exceeds the 3-member limit by combining `HAVING COUNT` logic in SQL queries with conditional validation in the Python backend.

### **2. Project Submission Verification**

Before a project submission is finalized, the system performs a multi-step validation:

* **Deadline Check:** If `current_date > end_date`, the submission portal is automatically blocked.
* **Approval Verification:** Only teams marked as `Accepted` by the Admin can submit their GitHub repositories.
* **Identity Sync:** The system verifies that the Team and Hackathon names match the registration records stored in the database.

---

## How to Run

1. **Clone the repository:**
```bash
git clone https://github.com/your-username/hackathon-management-system.git

```


2. **Install Requirements:**
```bash
pip install streamlit mysql-connector-python pandas

```


3. **Database Setup:**
* Import `database_techclub.sql` into your local MySQL Workbench or Aiven Console.
* Update the `db_config` credentials in the Python files to match your host settings.


4. **Run the Application:**
```bash
streamlit run app.py

```

DEVELOPED BY : NED UNIVERISTY OF ENGINEERING AND TECHNOLOGY STUDENTS 
IZMA WARSIA
SAFA KHURRAM
SANIYA SIDDIQUI
AYESHA 

---

**Developed for:** NED University Technical Project 2026. 🎓
