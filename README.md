Online Doctor Appointment System

A web-based system that lets patients find doctors, view free time slots and book or cancel appointments online, while doctors and the administrator manage appointments, doctors and slots.

This repository holds the design documentation for the project: presentation, UML diagrams, system architecture, the Software Design Analysis Report and the Lab 10 software metrics report. It was prepared as a Software Engineering & Design Principles project.

Table of Contents
Project Overview
Features
Technology Stack
System Architecture
Modules
Appointment Lifecycle
Documentation in this Repository
Repository Structure
Scope
Team
Project Overview

Booking a doctor by phone or at the clinic depends on reception availability, spoken details can be misunderstood, and manual entry can lead to clashes and double booking. This system replaces that with a structured digital flow:

The patient logs in or registers.
The patient searches for a doctor by specialization and picks an available date and time slot.
The backend validates the booking (valid patient, existing doctor, available and future slot) and saves the appointment together with the slot update, so a slot can never be booked twice.
The doctor views upcoming appointments and updates their status.
The administrator manages doctors, specializations and time slots.
Features

Patient

Register and log in
Search doctors by specialization and view details and consultation fee
View available time slots and book an appointment with a reason for the visit
Cancel an appointment and view booking history

Doctor

View upcoming appointments
Update appointment status: BOOKED -> CONFIRMED -> COMPLETED (or CANCELLED)

Administrator

Add and update doctors and specializations
Manage doctor time slots

System rules

Backend validation of every booking request (login, doctor, slot availability, slot not in the past)
Double-booking prevention: the appointment is created and the slot is marked unavailable as one unit
A cancelled appointment releases its slot
Role-based access: status updates and admin operations are restricted to authorized users
Technology Stack
Layer	Technology
Front end	HTML, CSS, JavaScript
Backend	Node.js, Express.js (REST-style APIs)
Database	MySQL
System Architecture

The system follows a three-layer architecture:

Layer	Responsibility
Presentation	Patient Portal, Doctor Dashboard, Admin Panel (HTML, CSS, JavaScript)
Application	Express.js REST APIs with validation and business rules: Auth, Doctor, Slot and Appointment services (plus an optional Notification service for reminders)
Data	MySQL database storing patients, doctors, time slots and appointments

The browser talks only to the API (over HTTPS, request/response), never directly to MySQL.

System Architecture Diagram

Modules

The system is divided into 7 modules along the stages of the booking process:

ID	Module	Main responsibility
M1	User Registration & Login	Register users, check credentials, start a session
M2	Doctor Search & Details	List doctors, filter by specialization, show fee and details
M3	Slot Management & Availability	Show free slots, check and release a slot
M4	Appointment Booking	Validate the booking, create the appointment and lock the slot
M5	Appointment Status Management	Doctor views appointments and updates status
M6	Admin Data Management	Add or update doctors, specializations and time slots
M7	History & Data Management	Store and retrieve records and booking history
Appointment Lifecycle

Pick slot -> Validate -> Lock slot -> Save together -> Confirm

Status	Meaning
BOOKED	Appointment saved
CONFIRMED	Doctor acknowledges
COMPLETED	Consultation finished
CANCELLED	Cancelled; slot is released
Documentation in this Repository
Document	Description
Presentation	10-slide project presentation: problem, workflow, architecture, UML, database, lifecycle, requirements and viva concepts
Software Design Analysis Report	Module identification, design strategy (Hybrid), design approach (Mixed), coupling and cohesion analysis, sequence diagram and annexures
Lab 10: Software Metrics & Complexity Analysis	Size, cyclomatic complexity, Halstead metrics, Maintainability Index and fan-in / fan-out
System Architecture Diagram	Presentation, Application and Data layers with external services
UML Class Diagram	Patient, Doctor, Specialization, TimeSlot, Appointment, AppointmentStatus, Administrator
UML Activity & Sequence Diagrams	Swimlane activity diagram and sequence diagram of the booking flow
All Diagrams (single PDF)	Architecture, class, activity and sequence diagrams in one file
UML Class Diagram

UML Class Diagram

UML Activity Diagram

UML Activity Diagram

UML Sequence Diagram

UML Sequence Diagram

Repository Structure
.
├── README.md
└── docs/
    ├── presentation/
    │   └── Online_Doctor_Appointment_System_Presentation.pdf
    ├── reports/
    │   ├── Online_Doctor_Appointment_Software_Design_Report.pdf
    │   └── Lab10_Software_Metrics_and_Complexity_Analysis_Online_Doctor_Appointment_System.pdf
    └── diagrams/
        ├── Online_Doctor_Appointment_System_Architecture_Diagram.pdf
        ├── Online_Doctor_Appointment_System_Architecture_Diagram.png
        ├── Online_Doctor_Appointment_UML_Class_Diagram.pdf
        ├── Online_Doctor_Appointment_UML_Class_Diagram.png
        ├── Online_Doctor_Appointment_UML_Activity_Sequence_Diagram.pdf
        ├── Online_Doctor_Appointment_UML_Activity_Diagram.png
        ├── Online_Doctor_Appointment_UML_Sequence_Diagram.png
        └── Online_Doctor_Appointment_System_All_Diagrams.pdf
Scope

This is the initial version of the system. Video consultation and advanced online payment are not assumed. Email/SMS reminders through a notification service are shown in the architecture as optional.

Team
S.No.	Name	Roll Number	Responsibility
1	Harsh Mishra	202401100100110	Backend & Database
2	Devansh	202401100100093	Frontend Development
3	Kushagra	202401100100143	Project Planning & Coordination
4	Madhav Agarwal	202401100100146	Testing & Development
