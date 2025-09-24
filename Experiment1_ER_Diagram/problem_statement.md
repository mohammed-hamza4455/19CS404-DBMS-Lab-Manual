# ER Diagram Workshop – Submission Template

## Objective
To understand and apply ER modeling concepts by creating ER diagrams for real-world applications.

## Purpose
Gain hands-on experience in designing ER diagrams that represent database structure including entities, relationships, attributes, and constraints.

---

# Scenario A: City Fitness Club Management

**Business Context:**  
FlexiFit Gym wants a database to manage its members, trainers, and fitness programs.

**Requirements:**  
- Members register with name, membership type, and start date.  
- Each member can join multiple programs (Yoga, Zumba, Weight Training).  
- Trainers assigned to programs; a program may have multiple trainers.  
- Members may book personal training sessions with trainers.  
- Attendance recorded for each session.  
- Payments tracked for memberships and sessions.

### ER Diagram:

<img width="989" height="675" alt="image" src="https://github.com/user-attachments/assets/2c5f5f33-3caf-4c37-9579-d9cc090bf2d2" />


### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
| Member       |  Member_ID (PK), Name, MembershipType, StartDate                  | Stores details of gym members      |
| Program       |  Trainer_ID (PK), Name                  | Each trainer conducts programs      |
| Attendance       |  Attendance_ID (PK, FK Member_ID, FK Trainer_ID)                  | Records which member attended which program      |
| Payment       |  Payment_ID (PK, FK Member_ID), MembershipFee, SessionFee                  |Tracks payment details for each member       |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
| Joins (Member–Program)             | 1:N (Member to Program), N:M overall           |    Member must join at least one Program           | Many members can join many programs      |
|  Conducts (Program–Attendance)            | 1:M (Program to Attendance)           |    Mandatory           | Each program has multiple attendance records      |
|   Is Booked By (Attendance–Member)           |  1:N          | Mandatory              |  Each attendance is linked to a member     |
|  Tracked For (Attendance–Payment)            |  1:N          |  Optional             | Payments are tracked per attendance      |
| Is Recording (Attendance–Payment)             |    1:N        |   Optional            | Payment details are recorded for attendance      |

### Assumptions
- A member can join multiple programs (e.g., Yoga, Zumba, Weight Training)
- A trainer can conduct multiple programs, but each program is managed by one trainer.
- Payments are made either for membership or for individual sessions.

---

