# 📚 Table of Contents

- [Question Zero](#-question-zero)
- [Persona](#-persona)
- [System Architecture](#-system-architecture)
  - [Block Diagram](#-block-diagram)
  - [State Diagram](#-state-diagram)
  - [Activity Diagram](#-activity-diagram)
- [Project Management](#project-management)
  - [Milestones](#-milestones)
  - [User Stories](#-user-stories)
  - [Use Case](#-use-case)
  - [Scenario](#-scenario)
- [Team Roles and Responsibilities](#-team-roles-and-responsibilities)

# 🛫 Fly with VoyageX
We are VoyageX, a group of six driven individuals who are using technical prowess, teamwork, and creativity to explore bold paths. Our team, which has strengths in project management, automotive engineering, and information technology, thrives on finding innovative solutions to challenging issues. Curiosity and teamwork drive VoyageX, a place where a range of expertise and common goals come together to launch ideas and propel them beyond their wildest expectations.


---

# 🧠 Question Zero

The concept of **Question Zero** highlights the importance of beginning the design process by focusing on real human needs. It ensures that technology is developed not just for functionality, but to improve lives and help elderly residents in rural areas stay mobile, independent, and socially engaged.

**How can we design an autonomous shuttle service** (What)  
**that ensures transportation for senior citizens with walking aids** (For whom)  
**in Landkreis Kronach (rural areas)** (Where)  
**by providing an on-demand service** (How)  
**to increase their frequency of visits to supermarkets to cater to their everyday needs?** (Why)


---

# 👵 Persona

The **Persona Method** helps designers and engineers deeply understand the **challenges, motivations, and preferences** of their users. By crafting fictional user profiles, we can ensure that our autonomous shuttle solution is tailored to meet real-world demands.

## 💼 Meet Olivia Wilson

As shown in Figure 1, **Olivia Wilson** is a 70-year-old woman living alone in a senior apartment in Kronach. She uses a walker with a seat due to mild arthritis and occasional fatigue. Although she values her independence, her mobility limitations and the lack of accessible public transportation make grocery shopping increasingly difficult.

She no longer drives and feels emotionally burdened when asking family for help. Olivia prefers shopping in the mornings when stores are less crowded but is often deterred by poor weather, long walking distances, and steep bus steps.

<p align="center">
  <img src="assets/Persona.png" alt="Persona" width="70%"/>
</p>
<p align="center"><strong>Figure 1:</strong> Persona </p>

---

# 🧩 System Architecture

The system architecture outlines the autonomous shuttle’s functional structure. The block diagram represents a five-layer model which includes Sensors, Sense, Plan, Act and Actuator layer that highlights how data flows from sensors to physical action. The state diagram shows how the shuttle transitions through various modes like idle, driving, and parking. The activity diagram describes all the events that take place during the journey, to show the design of a smooth and accessible service. These elements together provide a clear and structured view of entire system.

## 🧱 Block Diagram

The autonomous shuttle system is designed to provide safe and accessible transportation for all users, especially those with mobility needs. Built on a five-layer architecture (Sensors, Sense, Plan, Act, and Actuator) the system is powered by ROS 2, ensuring compatibility with modern mobility standards.
Figure 2 describes the entire block diagram with inputs and outputs all all components of the system.

The Sensors Layer collects essential data to help the shuttle understand its surroundings and external conditions. A Lidar scans the environment to detect obstacles, while an RealSense camera identifies objects. A QR code scanner verifies passengers before boarding, and a Domain Bridge (HS-IoT) ensures continuous connection to external services like traffic updates and signal phasing.

In the Sense Layer, this data is processed to create a clear understanding of the shuttle’s surroundings. The Localization Module estimates the shuttle’s position and orientation by interpreting sensor data, while Object Detection and Obstacle Detection Modules recognize people, vehicles, and static hazards. A V2X Decoder gathers messages from nearby connected infrastructure or vehicles, helping the shuttle make informed decisions. All sensor data is merged using the Sensor Fusion and Filtering Module.The Map Server maintains an updated digital map. The Authentication Module handles secure passenger identification using scanned QR inputs.

The Plan Layer determines the shuttle’s behavior based on its understanding of the environment. At its core, the Decision Unit evaluates the situation and decides whether the shuttle should drive, park, board, or be ideal. The Path Planning Module calculates the most appropriate route, considering current location and goal position. This planning process ensures the shuttle navigates safely and efficiently.

In the Act Layer, the Path Execution Controller plays a central role, converting the planned path into real-time control actions. This module ensures the shuttle follows the route accurately, handling turns, speed changes, and route corrections. The Access Controller manages physical accessibility features such as the door and ramp, triggered only after verifying safe conditions and authenticated passenger access. Meanwhile, the V2X Encoder shares the shuttle’s primary details with surrounding infrastructure and other vehicles for safe interaction.

The Actuator Layer transforms these decisions into physical motion. A Door Actuator and Ramp Actuator provide safe entry and exit, especially for passengers with mobility challenges. The Domain Bridge connects shuttle with external systems.

Together, these layers form a robust and intelligent system for autonomous transport. With a focus on safety, and accessibility.

<p align="center">
  <img src="assets/block_diagram.png" alt="Block Diagram" width="70%"/>
</p>
<p align="center"><strong>Figure 2:</strong> Block Diagram </p>


[Visit block diagram Miro Board](https://miro.com/app/board/uXjVJfaT4fM=/?moveToWidget=3458764634693919231&cot=14)

## 🔄 State Diagram
The State Diagram showed in Figure 3 shows the full cycle of an autonomous shuttle. The shuttle starts in the Idle state, where it waits in a parking area or resting point until a booking is confirmed through a mobile app. Once a booking is made, the shuttle transitions to the Driving state. In this state, the vehicle navigates from its idle position to the user’s pickup location, using planned paths that consider safety and road conditions.

When the shuttle reaches the pickup spot, it moves to the Boarding state. Once the user boards, the shuttle resumes the Driving state again, this time heading to the user's intended drop-off location, which is a supermarket. Upon arrival, the shuttle switches to the Deboarding state, where the user exits safely to begin their shopping trip.

After drop-off, the shuttle searches for an available parking spot near the supermarket. When it reaches a parking spot, it transitions into a Parking state and parks itself safely. After that it changes its state to Ideal and remains there until the user finishes shopping. Once the user completes its shopping , the same cycle can repeat. This simple, well-defined state model ensures that the shuttle service is efficient, and offer safe, on-demand mobility to help seniors complete their tasks independently and reliably.

<p align="center">
  <img src="assets/State_diagram.png" alt="State Diagram" width="70%"/>
</p>
<p align="center"><strong>Figure 3:</strong> State Diagram </p>

## 🏃 Activity Diagram

The autonomous shuttle service begins when an elderly resident uses a dedicated app to request a ride to the supermarket. The app is designed specifically for seniors, with large icons and a simple interface to make booking process easy. Once a booking request is received, the system checks if the booking is confirmed. If not, the shuttle doesn’t proceed and waits in the parking area, until a valid request comes in. If the booking is successful, the shuttle plans a path to the user’s based on current traffic and road conditions in the rural area.

After planning the route, the shuttle drives to the user’s location. After reaching the pickup location, the shuttle authenticates user using a QR code scanner, ensuring the correct person boards the shuttle. After successful authentication, the user boards the shuttle, which is designed to accommodate walking aids with automated door and ramp access. The shuttle then drives to the supermarket, since the goal of this service is to assist elderly citizens in making routine shopping trips independently. Once at the supermarket, the user deboards the shuttle safely and proceeds with their shopping.

After drop-off, the shuttle begins searching for an available parking spot near the supermarket. Once a suitable spot is found, it parks itself and remains there until the user finishes shopping and requests the return trip. Figure 4 illustrates this activity flow, outlining each step of the shuttle’s interaction with the user from booking to parking.

<p align="center">
  <img src="assets/Activity_diagram.jpg" alt="Activity Diagram" width="70%"/>
</p>
<p align="center"><strong>Figure 4:</strong> Activity Diagram </p>


---

# 🗂️ Project Management

This section covers key project management aspects that ensure the autonomous shuttle system is developed efficiently, collaboratively, and aligned with real-world needs. The tools used throughout the project supported version control, task tracking, and documentation. User stories outlined specific goals from the perspective of developers and system components, helping break down complex tasks into manageable units. The use case and scenario described how the shuttle operates in a realistic environment, serving elderly users in rural areas through a simplified booking process and autonomous transportation.
The milestones provided a clear roadmap of deliverables and progress, guiding the team toward successful completion by Module 6. Team roles and responsibilities defined each member's contributions in ongoing collaboration. Lastly, 

## 🛠️ Tools

At **VoyageX**, we prioritize clear communication, collaborative design, and informed decision-making. For team coordination and updates, we use **Microsoft Teams** as our primary communication tools. To visualize ideas, map system behaviors, and co-create diagrams, we rely on **MIRO**, a flexible platform to design the system. Additionally, we use **Git** for version control to manage our codebase and track changes.

For background research and technical understanding, we utilized platforms such as **Google Scholar**, **Wikipedia**, and other freely available academic sources to explore related technologies, accessibility considerations, and autonomous mobility systems. These tools helped us stay  informed, and aligned throughout the development of our solution.

## 📋 User Stories

In this project, user stories are structured to reflect the development process and the technical goals of building a modular vehicle system. These stories capture the responsibilities and intentions of developers, system components, and the team as a whole.This approach helps align the project’s technical milestones with its functional goals.
[Visit User Stories Miro Board](https://miro.com/app/board/uXjVJfaT4fM=/?moveToWidget=3458764635025969912&cot=14)


## 📅 Milestones

Certainly! Here's a longer and more formal version of the sentence:

Figure 5 provides a comprehensive overview of the key milestones that the team has successfully accomplished so far, as well as the planned objectives and deliverables that are expected to be completed by the end of Module 6, ensuring steady progress and alignment with the overall project timeline.

<p align="center">
  <img src="assets/milestones.jpg" alt="Milestones" width="70%"/>
</p>
<p align="center"><strong>Figure 5:</strong> Project Milestones</p>


| Icons | Meaning              | | Colors  | Meaning                   |
|------|---------------------|-|--------|---------------------------|
| 🧪   | Testing            |  | Blue   | Technical Development     |
| 🔗   | Integration        | |  Green  | UI/UX or HMI              |
| ✅   | Compliance          | | Red    | Safety & Compliance       |
| 🎯   | User Experience    | | Purple | AI/Data/Simulation        |
| 🔐   | Security            | | Orange | Business & Launch         |
| 🛠️   | Development         | 


## 🔎 Use Case

Olivia Wilson, a 70-year-old retiree, lives alone in a senior apartment in Kronach. She values her
independence but faces challenges due to mild arthritis and fatigue, relying on a walker with a seat
for mobility. Grocery shopping has become difficult especially in poor weather as the nearest bus
stop is far, and she no longer drives. Though her daughter helps occasionally, Olivia dislikes feeling
dependent and wishes for a simple, stress-free way to shop on her own.

To meet this need, a human-centered Autonomous Grocery Shuttle has been launched in
Kronach, designed for seniors with mobility aids. Olivia can easily book a ride through simple,
icon-based mobile application,. The system remembers her preferences, and the shuttle picks her
up directly from her doorstep.
The vehicle features a ramp for easy boarding, a secure spot for her walker, and a quiet, comfortable
cabin with clear audio-visual cues. The ride is direct and smooth, taking her to the supermarket
entrance without delays or complex interactions.

After shopping, she’s picked up at a nearby
zone for her return trip.
This service empowers Olivia to maintain her independence, avoid physical strain, and keep a
regular routine without needing assistance while supporting both her mobility and emotional well-being.

<p align="center">
  <img src="assets/Olivia_wilson.png" alt="Use Case" width="70%"/>
</p>
<p align="center"><strong>Figure 6:</strong> Use Case</p>

## 🎬 Scenario


The autonomous grocery shuttle operation begins with a ride request initiated by the user, Olivia
Wilson, a 70-year-old retiree living independently in a senior apartment in Kronach. Due to mild
arthritis and balance issues, she relies on a walker with a seat and avoids long walks or using
unreliable rural public transportation. To maintain her independence and manage daily tasks like
grocery shopping, she uses a senior-friendly autonomous shuttle service designed for residents with
limited mobility.

Using a simple, icon-based mobile application, Olivia schedules her trip by selecting key details
such as pickup location (her residence), destination (supermarket), and desired departure time.
The app is designed with minimal text and large, intuitive icons, making it accessible and stress-free
for elderly users. Her mobility aid and boarding preferences are already saved in her profile,
enabling a quick and effortless booking process.

Once the request is submitted, the system verifies availability and assigns a trip to the shuttle. It
then generates an optimized multi-stop route through its path and trajectory planning module,
incorporating Olivia’s stop. Figure 7 illustrates the complete scenario, showing each step. 
The autonomous shuttle departs from its staging area and follows the assigned route. Upon arriving
at Olivia’s building entrance, it initiates a secure passenger verification process. Olivia confirms
her identity using a large touchscreen onboard, tapping a confirmation icon that syncs with her prior
booking.

Once verified, the vehicle automatically deploys an accessibility ramp and opens its doors. Olivia
boards without assistance, aided by the shuttle’s low-floor design, wide doors, secure handrails, and
dedicated walker space. Once seated and her walker is locked in place, the system conducts a safety
check to confirming proper seating, ramp retraction, and door closure.

The shuttle continues toward the supermarket, using its onboard perception system and V2X
communication modules to monitor traffic, receive real-time updates from surrounding
infrastructure, and ensure safe navigation. En route, the system detects a construction-related detour
via a V2X alert. The shuttle's path planning module instantly recalculates a new route, and Olivia is
informed of the minor adjustment through a clear, friendly voice announcement to ensuring her ride
remains predictable and comfortable.

At the supermarket, the shuttle stops at the designated accessible entrance, announces the arrival via
audio cue, opens the doors, and deploys the ramp. Olivia exits smoothly and begins her shopping
while the shuttle starts finding the spot to park itself. And after finding spot it parks itself safely and securely.

Once ready to return, Olivia opens the app and taps the “Return Home” icon. The system retrieves
her profile and dispatches to the supermarket to pick her up. The return
trip mirrors the outbound process: authentication, accessible boarding, safety confirmation, and a
direct route back to her residence.
Upon arrival, the shuttle deploys the ramp, and Olivia disembarks with her groceries and walker. A
completion report is automatically sent to the central management system, confirming the
successful and secure trip.

This seamless, autonomous experience empowers Olivia to manage her errands independently which enhancing her mobility, routine stability, and overall quality of life without needing to depend on
others.

<p align="center">
  <img src="assets/scenario.png" alt="Scenario" width="70%"/>
</p>
<p align="center"><strong>Figure 7:</strong> Scenario </p>

---

# 👥 Team Roles and Responsibilities

Our team is committed to project success through clear communication, timely delivery, and collaborative problem-solving. Each member has specific roles, from managing meetings and documenting progress to overseeing agile practices and ensuring team activities run smoothly. Together, we achieve collective growth and efficiency.

| **Responsibility**                                                                 | **Member**             | 
|------------------------------------------------------------------------------------|------------------------|
| Visual Collaboration Specialist                        | Ravikumar Savaliya     |
| Workflow Coordinator                    | Sonia S.               |
| QA & Compliance Lead                                                 | Monika N.                  |
| Tech & Meeting Coordinator                | Vamsi         |
| Data Integrity Analyst                              | Parth Pahinkar         |
| Documentation Lead                                               | Fenil Savaliya              |


### Component Responsibilities

| Component Name                                                                 | Responsibility         |
|--------------------------------------------------------------------------------|------------------------|
| [Path Planning](https://git.hs-coburg.de/voyagex/vx_path_planning) | Ravikumar               |
| [Obstacle Detection](https://git.hs-coburg.de/voyagex/vx_obstacle_detection)     | Vamsi               |
| [Object Detection](https://git.hs-coburg.de/voyagex/vx_object_detection)         | Team VoyageX      |
| [Sensor Data Fusion and Filtering Module](https://git.hs-coburg.de/voyagex/vx_v2x_fusion)                  | Ravikumar & Parth               |
| [Server](https://git.hs-coburg.de/voyagex/vx_server)                             | Ravikumar & Parth               |
| [Path Execution Controller](https://git.hs-coburg.de/voyagex/vx_path_execution_controller)   | Fenil         |
| [Desicion Unit](https://git.hs-coburg.de/voyagex/vx_decision_unit)       | Ravikumar & Parth                |
| [V2X Encoder](https://git.hs-coburg.de/voyagex/vx_v2x_encoder)                           | Parth                |
| [V2X Decoder](https://git.hs-coburg.de/voyagex/vx_v2x_decoder)              | Sonia                 |
| [Authentication](https://git.hs-coburg.de/voyagex/vx_authentication)          | Ravikumar & Parth      |
| [Access Controller](https://git.hs-coburg.de/voyagex/vx_door_operation)            | Ravikumar & Parth      |
| [Localization](https://git.hs-coburg.de/voyagex/vx_visualization) | Monika              |


### User Interface Concepts 

| HMI Type                                                                 | Team Members         |
|--------------------------------------------------------------------------------|------------------------|
| [Internal HMI](https://git.hs-coburg.de/voyagex/vx_path_planning) | Ravikumar, Fenil, Sonia               |
| [External HMI](https://git.hs-coburg.de/voyagex/vx_external_HMI)     | Vamsi, Monika, Parth              |
