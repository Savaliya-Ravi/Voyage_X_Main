# 📚 Table of Contents

- [Our Mission](#our-mission)
- [Problem (Question Zero)](#problem-question-zero)
- [Persona](#persona)
- [System Architecture](#system-architecture)
  - [Block Diagram](#block-diagram)
  - [State Diagram](#state-diagram)
  - [Activity Diagram](#activity-diagram)
- [Project Management](#project-management)
  - [Milestones](#milestones)
  - [User Stories](#user-stories)
  - [Use Case](#use-case)
  - [Scenario](#scenario)
- [Team Roles and Responsibilities](#team-roles-and-responsibilities)

---

# 🛫 Fly with VoyageX
We are VoyageX—a crew of six ambitious minds charting bold paths through innovation, collaboration, and technical excellence. With strengths spanning Information Technology, Automotive Engineering, and Project Management, our team thrives on solving complex problems with creative precision. Fueled by curiosity and guided by teamwork, VoyageX is where diverse expertise meets shared ambition—ready to lift ideas off the ground and take them further than imagined.



## 🎯 Our Mission

To design a **seamless, human-centered autonomous shuttle service** that supports users like Olivia by:

- Providing **doorstep pick-up and drop-off**
- Ensuring **safe and accessible onboarding** for those with walking aids
- Promoting **independence and routine** for elderly residents

Our solution empowers Olivia to maintain her lifestyle, meet daily needs, and reconnect with her community—**without stress, dependence, or barriers**.


---

## 🧠 Problem (Question Zero)

**How can we design an autonomous shuttle service** (What)  
**that ensures transportation for senior citizens with walking aids** (For whom)  
**in Landkreis Kronach (rural areas)** (Where)  
**by providing an on-demand service** (How)  
**to increase their frequency of visits to supermarkets to cater to their everyday needs?** (Why)

The concept of **Question Zero** emphasizes the importance of beginning the design process by focusing on real human needs. It ensures that technology is developed not just for functionality, but to improve lives—in this case, helping elderly residents in rural areas stay mobile, independent, and socially engaged.

---

## Persona

The **Persona Method** helps designers and engineers deeply understand the **challenges, motivations, and preferences** of their users. By crafting fictional, research-driven user profiles, we can ensure that our autonomous shuttle solution is tailored to meet real-world demands.

### 💼 Meet Olivia Wilson

**Olivia Wilson** is a 70-year-old woman living alone in a senior apartment in Kronach. She uses a walker with a seat due to mild arthritis and occasional fatigue. Although she values her independence, her mobility limitations and the lack of accessible public transportation make grocery shopping increasingly difficult.

She no longer drives and feels emotionally burdened when asking family for help. Olivia prefers shopping in the mornings when stores are less crowded but is often deterred by poor weather, long walking distances, and steep bus steps.

> “I just want to get my groceries without feeling like I’m a burden or in a rush.”

---

## System Architecture

We designed a modular and scalable system that ensures reliability, accessibility, and real-time responsiveness.

### Block Diagram

The autonomous shuttle system is designed to provide safe and accessible transportation for all users, especially those with mobility needs. Built on a five-layer architecture—Sensors, Sense, Plan, Act, and Actuator—the system is powered by ROS 2, ensuring modularity, real-time performance, and compatibility with modern urban mobility standards.

The Sensors Layer collects essential data to help the shuttle understand its surroundings and external conditions. A YDLIDAR G4 scans the environment to detect obstacles, while an Intel RealSense camera identifies objects. A QR code scanner verifies passengers before boarding, and a Domain Bridge (HS-IoT) ensures continuous connection to external services like cloud infrastructure and traffic updates.

In the Sense Layer, this data is processed to create a clear understanding of the shuttle’s surroundings. The Localization Module estimates the shuttle’s position and orientation by interpreting sensor data, while Object Detection and Obstacle Detection Modules recognize people, vehicles, and static hazards. A V2X Decoder gathers messages from nearby connected infrastructure or vehicles, helping the shuttle make informed decisions. All sensor data is merged using the Sensor Fusion and Filtering Module, while the Map Server maintains an updated digital map. The Authentication Module handles secure passenger identification using scanned QR inputs.

The Plan Layer determines the shuttle’s behavior based on its understanding of the environment. At its core, the Decision Unit evaluates the situation and decides whether the shuttle should drive, park, board, or be ideal. The Path Planning Module calculates the most appropriate route, considering current location and goal position. This planning process ensures the shuttle navigates safely and efficiently.

In the Act Layer, the Path Execution Controller plays a central role, converting the planned path into real-time control actions. This module ensures the shuttle follows the route accurately, handling turns, speed changes, and route corrections. The Access Controller manages physical accessibility features such as the door and ramp, triggered only after verifying safe conditions and authenticated passenger access. Meanwhile, the V2X Encoder shares the shuttle’s primary details with surrounding infrastructure and other vehicles for coordinated, safe interaction.

The Actuator Layer transforms these decisions into physical motion. A Door Actuator and Ramp Actuator provide safe entry and exit, especially for passengers with mobility challenges. The Domain Bridge also continues to relay relevant data to external systems, allowing monitoring or integration with smart mobility services.

Together, these layers form a robust and intelligent system for autonomous transport. With a focus on safety, accessibility, and real-time response, and backed by the reliability of ROS 2, the shuttle is ready for practical use in smart city environments.

![Block Diagram](block_diagram.jpg)

[Visit Miro Board](https://miro.com/welcomeonboard/V2tWM2k0RU5iY0xkQjZ6RHIveVJJUHJOdzRnSEJ2cFRmOWZIRzc5dCs4WFZDS2NVS3BFeGdQaVVLMUR4MDJBeDYrWXN3WTJ5TjRYWWM3ckkyTnBVVndya1U4UG5xQTJJeGhYY2xaaFI2azVmMW9Kb1dsckFwNHVJcTJTODB5dktyVmtkMG5hNDA3dVlncnBvRVB2ZXBnPT0hdjE=?share_link_id=175416963287)


### State Diagram
This state diagram shows the full cycle of an autonomous shuttle designed specifically for elderly users with walking aids. The shuttle starts in the Idle state, where it waits in a parking area or resting point until a booking is confirmed through a dedicated mobile app. Once a booking is made, the shuttle transitions to the Driving state. In this state, the vehicle navigates from its idle position to the user’s pickup location, using planned paths that consider safety and rural road conditions.

When the shuttle reaches the pickup spot, it moves to the Boarding state. Here, the user scans a QR code for authentication before boarding. The shuttle is designed to support individuals with mobility limitations, using features like automated ramps. Once the user boards, the shuttle resumes the Driving state again—this time heading to the user's intended drop-off location, which is a supermarket. Upon arrival, the shuttle switches to the Deboarding state, where the user exits safely to begin their shopping trip.

After drop-off, the shuttle searches for an available parking spot near the supermarket. When it reaches a parking spot, it transitions into a Parking state and parks itself safely. After that it changes its state to Ideal and remains there until the user finishes shopping. Once the user completes its shopping , the same cycle can repeat. This simple, well-defined state model ensures that the shuttle service is both efficient and responsive, offering safe, on-demand mobility to help seniors complete essential tasks like grocery shopping independently and reliably.

![State Diagram](State_diagram.jpg)

### Activity Diagram

The autonomous shuttle service begins when an elderly resident uses a dedicated app to request a ride to the supermarket. The app is designed specifically for seniors, with large icons and a simplified interface to make booking easier. Once a booking request is received, the system checks if the booking is confirmed. If not, the shuttle doesn’t proceed but instead waits in the parking area, until a valid request comes in. If the booking is successful, the shuttle plans a path to the user’s based on current traffic and road conditions in the rural area.

After planning the route, the shuttle drives to the user’s location. After reaching the pickup location, the shuttle authenticates user using a QR code scanner, ensuring the correct person boards the shuttle. After successful authentication, the user boards the shuttle, which is designed to accommodate walking aids with automated door and ramp access. The shuttle then drives to the supermarket, since the goal of this service is to assist elderly citizens in making routine shopping trips independently. Once at the supermarket, the user deboards the shuttle safely and proceeds with their shopping.

![Activity Diagram](Activity_diagram.jpg)


---

## Project Management

### Milestones

- Week 1–2: Requirement gathering and persona creation
- Week 3–4: System architecture and block diagram
- Week 5–6: Prototype development
- Week 7–8: Testing and final review

### User Stories

![User Stories](user_stories.jpg)

[Visit Miro Board](https://miro.com/welcomeonboard/bFdCeDJveHExeDFBWDdaVTBZci9jdDd2NVhjS3M5dUVMWEZoZDIveTR4NlVHN01hTUp5TUw4eEZyNS94aG1zVFJoM0NESlgvelJXR0grMWpBNDlyVlFya1U4UG5xQTJJeGhYY2xaaFI2azZzYjJlWFZNcjRzMXBnUGNBZXRDMGphWWluRVAxeXRuUUgwWDl3Mk1qRGVRPT0hdjE=?share_link_id=382741195050)


### Use Case

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
regular routine without needing assistance—supporting both her mobility and emotional well-being.

![Olivia Wilson](Olivia_wilson.png)

### Scenario

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

Once the request is submitted, the system verifies availability and assigns a shuttle to the trip. It
then generates an optimized multi-stop route through its path and trajectory planning module,
incorporating Olivia’s stop.
The autonomous shuttle departs from its staging area and follows the assigned route. Upon arriving
at Olivia’s building entrance, it initiates a secure passenger verification process. Olivia confirms
her identity using a large touchscreen onboard, tapping a confirmation icon that syncs with her prior
booking.

Once verified, the vehicle automatically deploys an accessibility ramp and opens its doors. Olivia
boards without assistance, aided by the shuttle’s low-floor design, wide doors, secure handrails, and
dedicated walker space. Once seated and her walker is locked in place, the system conducts a safety
check—confirming proper seating, ramp retraction, and door closure.

The shuttle continues toward the supermarket, using its onboard perception system and V2X
communication modules to monitor traffic, receive real-time updates from surrounding
infrastructure, and ensure safe navigation. En route, the system detects a construction-related detour
via a V2X alert. The shuttle's path planning module instantly recalculates a new route, and Olivia is
informed of the minor adjustment through a clear, friendly voice announcement—ensuring her ride
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

This seamless, autonomous experience empowers Olivia to manage her errands independently—
enhancing her mobility, routine stability, and overall quality of life without needing to depend on
others.

![Scenario](scenario.png)
---

## Team Roles and Responsibilities

Our team is committed to project success through clear communication, timely delivery, and collaborative problem-solving. Each member has specific roles, from managing meetings and documenting progress to overseeing agile practices and ensuring team activities run smoothly. Together, we achieve collective growth and efficiency.

| **Responsibility**                                                                 | **Member**             | **Component**|
|------------------------------------------------------------------------------------|------------------------|--------------|
| Project Management, Feedback jotting, Software Engineering                        | Ravikumar Savaliya     |[Path Planning](https://git.hs-coburg.de/voyagex/vx_path_planning)|
| Documentation (Goals, Protocols, Mails, Weekly Presentations)                     | Sonia S.               |[V2X Decoder](https://git.hs-coburg.de/voyagex/vx_v2x_decoder)|
| Validation and Submission Planner                                                 | Monika N.                  |[Localization](https://git.hs-coburg.de/voyagex/vx_localization)|
| Timekeeper, Meeting rules, and ensuring everyone is in the meeting                | Vamsi         |[Obstacle Detection](https://git.hs-coburg.de/voyagex/vx_obstacle_detection)|
| Planning team activities, seeking help and assistance                              | Parth Pahinkar         |[V2X Encoder](https://git.hs-coburg.de/voyagex/vx_v2x_encoder)|
| Assigning tasks and planning reviews                                               | Fenil Savaliya              |[Path Execution Controller](https://git.hs-coburg.de/voyagex/vx_path_execution_controller)|
