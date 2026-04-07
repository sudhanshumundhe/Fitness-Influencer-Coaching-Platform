## **Fitness Influencer Coaching Platform – ER Diagram**

### **Overview**

This project contains the Entity Relationship Diagram (ERD) for an online fitness coaching platform. The database is designed to help fitness influencers or trainers manage clients, coaching plans, sessions, progress tracking, and payments efficiently.

The system supports both:

* One-off consultations
* Long-term coaching plans with structured workout and diet programs

---

### **Database Entities**

**1. Users**
Stores general information for all platform users, distinguishing between clients and trainers.

**Attributes:**

* `user_id (PK)`
* `user_name`
* `user_type (client / trainer)`
* `email`
* `phone`
* `password_hash`
* `country`
* `state`
* `city`

---

**2. Trainers**
Stores detailed trainer information including specialties, experience, and availability.

**Attributes:**

* `trainer_id (PK)`
* `user_id (FK)`
* `trainer_FullName`
* `bio`
* `specialties`
* `gender`
* `experience_years`
* `day_of_week`

---

**3. Clients**
Stores client-specific information, goals, and personal details.

**Attributes:**

* `client_id (PK)`
* `user_id (FK)`
* `full_Fullname`
* `date_of_birth`
* `gender`
* `joined_date`
* `goals`

---

**4. Plans / Programs**
Stores workout or diet plans and coaching program details.

**Attributes:**

* `plan_id (PK)`
* `trainer_id (FK)`
* `title`
* `description`
* `duration_weeks`
* `price`
* `workout_description`
* `diet_description`

---

**5. Client Plans / Subscriptions**
Tracks which client has subscribed to which plan, including status and duration.

**Attributes:**

* `client_plan_id (PK)`
* `client_id (FK)`
* `plan_id (FK)`
* `start_date`
* `end_date`
* `duration_months`
* `status (active / completed / cancelled)`

---

**6. Sessions / Consultations**
Stores scheduled interactions between clients and trainers.

**Attributes:**

* `session_id (PK)`
* `trainer_id (FK)`
* `client_id (FK)`
* `session_type (consultation / live_workout)`
* `start_time`
* `end_time`
* `notes`

---

**7. Check-ins**
Stores client progress updates, including body measurements and notes.

**Attributes:**

* `check_in_id (PK)`
* `client_id (FK)`
* `submitted_at`
* `weight_kg`
* `body_fat_pct`
* `muscle_mass_kg`
* `waist_cm`
* `chest_cm`
* `notes`

---

**8. Trainer Notes**
Stores feedback and observations by trainers linked to sessions and check-ins.

**Attributes:**

* `note_id (PK)`
* `trainer_id (FK)`
* `client_id (FK)`
* `check_in_id (FK)`
* `session_id (FK)`
* `created_at`
* `content`
* `action_required`

---

**9. Payments**
Stores payment information related to client subscriptions.

**Attributes:**

* `payment_id (PK)`
* `client_plan_id (FK)`
* `payment_date`
* `amount`
* `payment_method (upi / card / bank_transfer / cod)`
* `payment_status (pending / paid / failed / refunded)`
* `transaction_id`

---

### **Relationships**

* A trainer can coach multiple clients
* A client can subscribe to multiple plans over time
* Plans can be subscribed to by multiple clients
* Sessions and check-ins are linked to both trainers and clients
* Payments are linked to client subscriptions
* Trainer notes are associated with clients, sessions, and check-ins

**Entity Relationships:**

* `users.user_id < trainers.user_id`
* `users.user_id < clients.user_id`
* `trainers.trainer_id < plans.trainer_id`
* `plans.plan_id < client_plans.plan_id`
* `clients.client_id < client_plans.client_id`
* `trainers.trainer_id < sessions.trainer_id`
* `clients.client_id < sessions.client_id`
* `clients.client_id < check_ins.client_id`
* `trainer_notes.trainer_id > trainers.trainer_id`
* `trainer_notes.client_id > clients.client_id`
* `trainer_notes.check_in_id > check_ins.check_in_id`
* `trainer_notes.session_id > sessions.session_id`
* `client_plans.client_plan_id < payments.client_plan_id`

---

### **Purpose of the Project**

This ER diagram demonstrates how a database can support an online fitness coaching platform. It ensures efficient management of clients, plans, sessions, progress tracking, and payments while supporting both one-off consultations and long-term coaching programs.

### **Author
**Sudhanshu Mundhe
