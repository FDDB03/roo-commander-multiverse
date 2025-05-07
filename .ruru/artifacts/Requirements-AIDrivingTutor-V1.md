# Initial Requirements: AI Driving Tutor Chatbot (v1.0)

This document outlines the initial understanding of the goals, users, features, and requirements for the AI Driving Tutor Chatbot project. These are preliminary and subject to refinement based on further stakeholder input and research.

## 1. Project Goal

The primary goal of the AI Driving Tutor Chatbot is to **enhance the learning experience for student drivers and improve the efficiency of driving tutors** by providing accessible, consistent information, simulating driving scenarios, and offering supplementary support outside of practical driving lessons.

## 2. Target Users

*(Initial Personas - require validation)*

*   **Persona 1: The Driving Tutor (e.g., "Sarah")**
    *   **Role:** Professional driving instructor.
    *   **Needs:** Wants to save time answering repetitive student questions, track student progress on theory and hazard perception easily, provide supplementary learning materials, and potentially simulate specific scenarios students struggle with.
    *   **Pain Points:** Limited time per student, difficulty tracking individual theoretical weaknesses, students forgetting information between lessons.
    *   **Chatbot Interaction:** Uses the chatbot to monitor student progress, assign specific modules/scenarios, and possibly get insights into common student difficulties.

*   **Persona 2: The Student Driver (e.g., "Alex")**
    *   **Role:** Learner driver preparing for their driving test.
    *   **Needs:** Wants quick answers to driving rules and theory questions, practice hazard perception, understand complex maneuvers, get feedback on simulated scenarios, and review material learned in lessons.
    *   **Pain Points:** Forgetting rules, feeling unprepared for the theory test, anxiety about specific maneuvers or situations, needing clarification outside of lesson times.
    *   **Chatbot Interaction:** Uses the chatbot as a primary resource for Q&A, practicing scenarios, reviewing theory, and potentially tracking their own learning progress.

*   **Potential Persona 3: Driving School Administrator**
    *   *(To be explored)* Needs might include monitoring overall student progress, managing tutor resources, ensuring consistent teaching quality.

## 3. Core Features (Initial List)

*   **FAQ & Knowledge Base:** Answer common questions about driving rules, regulations, test procedures, vehicle maintenance, etc.
*   **Scenario Simulation:** Provide text-based or simple interactive simulations of common driving scenarios (e.g., navigating roundabouts, parallel parking steps, hazard perception).
*   **Progress Tracking:** Allow tutors (and potentially students) to track progress through theory topics or completed scenarios.
*   **Personalized Feedback:** Offer feedback based on simulated scenario performance or quiz results.
*   **Content Delivery:** Provide access to learning modules, videos, or links curated by the tutor/school.
*   **(Potential) Scheduling Assistant:** Integrate with tutor calendars to help schedule lessons (stretch goal).

## 4. Knowledge Base Considerations

The chatbot will require access to a comprehensive and up-to-date knowledge base, including:
*   Official driving rules and regulations (specific to the target region/country).
*   Theory test question banks.
*   Common driving scenarios and best practices.
*   Hazard perception principles and examples.
*   Basic vehicle maintenance information.
*   (Potentially) Tutor-specific teaching materials or emphasis points.

## 5. Initial User Stories (Examples)

*   **US1 (Student):** As a **Student Driver**, I want **to ask the chatbot questions about specific road signs**, so that **I can quickly clarify their meaning without waiting for my next lesson.**
    *   *Acceptance Criteria:*
        *   Chatbot recognizes questions about road signs.
        *   Chatbot provides the correct meaning and image (if possible) of the requested sign.
        *   Information is based on official regional regulations.

*   **US2 (Student):** As a **Student Driver**, I want **to practice hazard perception scenarios through the chatbot**, so that **I can improve my reaction times and awareness for the theory test.**
    *   *Acceptance Criteria:*
        *   Chatbot presents text-based or simple visual hazard scenarios.
        *   Chatbot prompts user for input on identifying hazards.
        *   Chatbot provides feedback on identified hazards (correct/missed).

*   **US3 (Tutor):** As a **Driving Tutor**, I want **to see which theory modules a student has completed via the chatbot**, so that **I can tailor my practical lesson focus accordingly.**
    *   *Acceptance Criteria:*
        *   Tutor can log in and view progress for their assigned students.
        *   Progress is displayed clearly (e.g., completed modules/scenarios, quiz scores).
        *   Data reflects student activity accurately.

*   **US4 (Student):** As a **Student Driver**, I want **the chatbot to explain the steps for parallel parking**, so that **I can review the maneuver sequence before attempting it in the car.**
    *   *Acceptance Criteria:*
        *   Chatbot provides a clear, step-by-step text description of parallel parking.
        *   Explanation includes key reference points and checks.
        *   (Optional) Includes a simple diagram or animation link.

---
*End of Initial Requirements v1.0*