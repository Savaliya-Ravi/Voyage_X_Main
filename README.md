# 🛫 Fly with VoyageX

## 📚 Table of Contents

- [🎯 Our Mission](#our-mission)
- [🧠 Problem (Question Zero)](#problem-question-zero)
- [👵 Persona](#persona)
- [🧩 System Architecture](#system-architecture)
  - [🧱 Block Diagram](#block-diagram)
  - [🔄 State Diagram](#state-diagram)
  - [🏃 Activity Diagram](#activity-diagram)
- [🗂️ Project Management](#project-management)
  - [📅 Milestones](#milestones)
  - [📋 User Stories](#user-stories)
  - [🔎 Use Case](#use-case)
  - [🎬 Scenario](#scenario)
- [👥 Team Roles and Responsibilities](#team-roles-and-responsibilities)

---

## 🎯 Our Mission

To design a **seamless, human-centered autonomous shuttle service** that supports users like Olivia by:

- Providing **doorstep pick-up and drop-off**
- Ensuring **safe and accessible onboarding** for walking aids
- Allowing **easy scheduling without apps**
- Promoting **independence and routine** for elderly residents

Our solution will help Olivia maintain her lifestyle, meet her daily needs, and reconnect with her community—**without stress, dependency, or barriers**.

---

## 🧠 Problem (Question Zero)

**How can we design an autonomous shuttle service** (What)  
**that ensures transportation for senior citizens with walking aids** (For whom)  
**in Landkreis Kronach (rural areas)** (Where)  
**by providing an on-demand service** (How)  
**to increase their frequency of visits to supermarkets to cater to their everyday needs?** (Why)

The concept of **Question Zero** emphasizes the importance of beginning the design process by focusing on real human needs. It ensures that technology is developed not just for functionality, but to improve lives—in this case, helping elderly residents in rural areas stay mobile, independent, and socially engaged.

---

## 👵 Persona

### The Persona Method

The **Persona Method** helps designers and engineers deeply understand the **challenges, motivations, and preferences** of their users. By crafting fictional, research-driven user profiles, we can ensure that our autonomous shuttle solution is tailored to meet real-world demands.

### 💼 Meet Olivia Wilson

**Olivia Wilson** is a 70-year-old woman living alone in a senior apartment in Kronach. She uses a walker with a seat due to mild arthritis and occasional fatigue. Although she values her independence, her mobility limitations and the lack of accessible public transportation make grocery shopping increasingly difficult.

She no longer drives and feels emotionally burdened when asking family for help. Olivia prefers shopping in the mornings when stores are less crowded but is often deterred by poor weather, long walking distances, and steep bus steps.

> “I just want to get my groceries without feeling like I’m a burden or in a rush.”

---

## 🧩 System Architecture

We designed a modular and scalable system that ensures reliability, accessibility, and real-time responsiveness.

### 🧱 Block Diagram

- Shows core modules like UI, Cloud Server, Autonomous Shuttle System, Sensors, and Edge Device Communication.
- Describes how modules interact to process requests and manage rides.

### 🔄 State Diagram

- Represents different states the shuttle can be in: Idle, Moving to Pickup, Waiting, En Route, etc.
- Helps us model user and system interaction logic.

### 🏃 Activity Diagram

- This activity diagram shows how an autonomous shuttle service can be used to help elderly residents with walking aids get to places like supermarkets in rural areas such as Landkreis Kronach.

The process starts when a senior citizen requests a shuttle. This could be done through a phone call, mobile app, or a simple local kiosk—designed to be accessible and easy for elderly users.

Once the booking request is received, the system checks if the booking is confirmed. If it’s not confirmed (maybe due to schedule issues or service unavailability), the shuttle doesn't move but instead waits in a nearby parking area until a new request comes in.

If the booking is confirmed, the shuttle plans a safe and accessible path to the pickup location. The shuttle then travels to where the user is, making sure it arrives smoothly and safely, even on narrow or uneven rural roads.

After reaching the pickup location, the shuttle authenticates the user (for example, by verifying a code or recognizing the booking), and the user gets on board. The shuttle design supports easy boarding, especially for seniors using walkers or walking sticks.

Next, the shuttle drives the user to their drop-off location—for example, the nearest supermarket or pharmacy. Once it gets there, the user safely exits the shuttle.

After the drop-off, the shuttle must find a place to park while waiting for the next ride. It begins by searching for an available parking spot. If it finds a spot, it parks and waits there. If it can’t find a spot immediately, it keeps searching until it does.

Finally, once parked, the shuttle waits quietly in the parking area until the next booking is made. The process is then complete.

- Maps decision points and parallel processes (like scheduling and verification).

---

## 🗂️ Project Management

### 📅 Milestones

- Week 1–2: Requirement gathering and persona creation
- Week 3–4: System architecture and block diagram
- Week 5–6: Prototype development
- Week 7–8: Testing and final review

### 📋 User Stories

- As Olivia, I want a ride without using an app so I can easily book it.
- As a caregiver, I want to ensure she is picked up safely.
- As a system admin, I want to monitor shuttles in real time.

### 🔎 Use Case

- Request Ride
- Confirm Identity
- Board Shuttle Safely
- Arrive and Exit

Each use case includes triggers, preconditions, flow, and postconditions.

### 🎬 Scenario

**Scenario:** Olivia needs to go grocery shopping.

1. Olivia calls the hotline.
2. System assigns shuttle closest to her.
3. Shuttle arrives, deploys ramp.
4. Olivia boards with her walker.
5. Ride completes, shuttle reports availability again.

---

## 👥 Team Roles and Responsibilities

Our team is committed to project success through clear communication, timely delivery, and collaborative problem-solving. Each member has specific roles, from managing meetings and documenting progress to overseeing agile practices and ensuring team activities run smoothly. Together, we achieve collective growth and efficiency.

| **Responsibility**                                                                 | **Member**             |
|------------------------------------------------------------------------------------|------------------------|
| Project Management, Feedback jotting, Software Engineering                        | Ravikumar Savaliya     |
| Documentation (Goals, Protocols, Mails, Weekly Presentations)                     | Sonia S.               |
| Validation and Submission Planner                                                 | Vamsi                  |
| Timekeeper, Meeting rules, and ensuring everyone is in the meeting                | Fenil Savaliya         |
| Planning team activities, seeking help and assistance                              | Parth Pahinkar         |
| Assigning tasks and planning reviews                                               | Monika N.              |
