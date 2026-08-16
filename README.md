<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Build a Hospital Triage App with Gemini

**Project Link:** [View Project](https://nextwork.ai/projects/86345cfc-0f8e-4965-b1d2-4d915496e0e0)

**Author:** Teja vinaya sri Sabbella  
**Email:** tejavinaya456@gmail.com

---

![Image](https://nextwork.ai/sparkling_purple_timid_curupira/uploads/86345cfc-0f8e-4965-b1d2-4d915496e0e0_ati6nij9)

## Why I Built ArogyaBed

### Project motivation and goals

In this project the main objective of the Hospital Bed Availability Tracker is to develop a simple and user-friendly cloud-based application that:

Displays hospital bed availability in real time.
Shows beds according to their current status.
Allows staff to add and manage beds.
Allows users to search and filter beds.
Supports bed reservation.
Supports admission and discharge workflows.
Provides ward-wise occupancy information.
Provides alerts when bed availability is low.
Provides secure user authentication.
Stores application data in a cloud database.

## Launching the Hospital Command Center in Google AI Studio

### Setting up Build mode

In this step, Sign in to Google AI Studio
Open Google AI Studio.
Sign in with your Google account.
Switch to Build mode.
Create the initial ArogyaBed app
Enter a natural-language prompt describing the application.
For example:

Build a simple Hospital Bed Availability Tracker called ArogyaBed. Create a responsive dashboard showing total beds, available beds, occupied beds, reserved beds, and maintenance beds. Add pages for bed management and ward management. Allow users to search and filter beds by ward and status. Use a clean, modern healthcare-themed UI.

Run the generated application
Allow Google AI Studio to generate the application.
Open the Live Preview.
Verify the app
Check that the dashboard loads correctly.
Check that the bed availability cards are visible.
Check navigation between pages.
Test the search/filter interface.
Check that the layout works properly.
Make corrections if needed


![Image](https://nextwork.ai/sparkling_purple_timid_curupira/uploads/86345cfc-0f8e-4965-b1d2-4d915496e0e0_28sdmh1m)

## Powering Emergency Triage with Gemini AI

### Integrating the ESI triage engine

In this step. Add Gemini-powered triage

Paste this into the Antigravity Agent:

Add Gemini-powered triage to the ArogyaBed patient intake form. When a patient submits their symptoms and basic information, use Gemini to analyze the input and assign a triage priority: Critical, High, Medium, or Low. Display the priority clearly on the patient record. Add proper error handling and do not provide a medical diagnosis.

2. Test the triage

Then prompt:

Test the Gemini triage feature with sample patients. Test one critical case with severe symptoms and one non-urgent case with mild symptoms. Verify that the triage priority is generated correctly and displayed in the patient record.

3. Add the priority queue

Finally:

Add a patient triage queue to ArogyaBed. Sort patients automatically by priority, with Critical patients first, followed by High, Medium, and Low. Add color-coded severity badges and display the patient's name, symptoms, priority, and timep, I'm setting up... so that I can...

![Image](https://nextwork.ai/sparkling_purple_timid_curupira/uploads/86345cfc-0f8e-4965-b1d2-4d915496e0e0_t99amwjr)

![Image](https://nextwork.ai/sparkling_purple_timid_curupira/uploads/86345cfc-0f8e-4965-b1d2-4d915496e0e0_lwmr9m1o)

### Critical vs. minor case comparison

When Gemini triages a patient, it assesses the severity of the symptoms and assigns an appropriate priority.

🔴 Severe symptoms: The patient is classified as Critical/High Priority. The system can prioritize them for ICU or emergency beds and alert staff for immediate attention.
🟢 Minor symptoms: The patient is classified as Low Priority/Stable. They can be directed toward a General Ward bed or routine care.
🟡 Moderate symptoms: The patient falls between these categories and may be assigned an appropriate ward based on available beds and medical needs.

So, the main difference is urgency and bed allocation: severe patients are prioritized for critical-care resources, while minor patients are handled through less intensive care.

## Solving the Data Loss Problem with Firestore

### Understanding ephemeral container storage

In this step, I'm testinIn this step, you will:

Refresh the app and observe that the current patient records and bed statuses are lost because the app is using temporary/local data.
Enable Cloud Firestore to store patient and bed information persistently in the cloud.
Connect the app to Firestore so that changes are saved to the database instead of only existing in the current browser session.
Refresh the page again and verify that:
Patient records are still available.
Bed statuses remain unchanged.
Data is preserved even after restarting or refreshing the application.

Expected result: Your ArogyaBed app will move from temporary data storage to persistent cloud-based storage using Cloud Firestore

### Diagnosing why data disappeared on refresh

When I refreshed the page, the patient records and bed statuses disappeared because the app was storing the data only in temporary in-memory/browser state.

Refreshing the page reloads the application from scratch, so that temporary data is cleared. There was no persistent database saving the changes.

In short:
Refresh → app restarts → temporary data is lost → records and bed statuses disappear.

This is why Cloud Firestore is needed—to permanently store the patient and bed data so it survives page refreshes.

![Image](https://nextwork.ai/sparkling_purple_timid_curupira/uploads/86345cfc-0f8e-4965-b1d2-4d915496e0e0_yg4o4yio)

## Connecting AI Triage to Automatic Bed Assignment

### Building the triage-to-bed pipeline

Add automatic bed assignment
Critical patients → ICU beds
Stable/minor patients → General Ward beds
The system checks bed availability before assigning.
Test the complete triage-to-assignment workflow
Enter patients with different severity levels.
Gemini performs the triage.
The system automatically selects the appropriate ward and available bed.
Add the discharge process
When a patient is discharged, their bed changes from Occupied → Cleaning.
After cleaning is completed, the bed automatically becomes Available again.

Expected result: ArogyaBed will have an end-to-end workflow:
Patient Registration → AI Triage → Automatic Bed Assignment → Treatment → Discharge → Cleaning → Bed Available.

![Image](https://nextwork.ai/sparkling_purple_timid_curupira/uploads/86345cfc-0f8e-4965-b1d2-4d915496e0e0_2anydcyp)

### The discharge cycle and why it matters

When a patient is discharged, the bed status changes:

Occupied → Cleaning → Available

The Cleaning status ensures the bed is sanitized and prepared before another patient uses it.

This matters because it helps the hospital:

Maintain accurate real-time bed availability
Prevent assigning a bed that is still being cleaned
Reuse beds efficiently
Speed up new patient admissions
Reduce confusion and manual tracking errors

So, the discharge cycle ensures that every bed is safely and efficiently returned to the available pool.


## Deploying a Live, Shareable App on Cloud Run

### Publishing to a permanent .run.app URL

In this step, I'm deploDeploy ArogyaBed to Google Cloud Run
Package the application for deployment.
Publish it using the Cloud Run Starter Tier.
Cloud Run provides a live URL for accessing the application.
Open the live application
Access ArogyaBed through the Cloud Run URL.
Verify that the application loads correctly outside the local development environment.
Test the complete system end-to-end
Register a patient.
Run Gemini-based triage.
Verify automatic ICU/General Ward bed assignment.
Test patient discharge.
Confirm the bed moves Occupied → Cleaning → Available.
Refresh the live application and verify that Firestore data persists.

![Image](https://nextwork.ai/sparkling_purple_timid_curupira/uploads/86345cfc-0f8e-4965-b1d2-4d915496e0e0_ati6nij9)

### How Firestore enables real-time shared state

Multiple users see the saMultiple users can see the same bed statuses because the ArogyaBed app uses Cloud Firestore as a shared, centralized database.

All users access the same Cloud Run application.
Bed information is stored in Firestore, not just in an individual user's browser.
When one user changes a bed status, the updated status is saved to Firestore.
Other users retrieving the bed data can see that same updated status.


## Secret Mission: Staff Authentication and Triage Analytics

### Role-based access control with Firebase Auth

## Reflections and Takeaways

### Key tools and concepts learned

Gemini AI – Used for patient symptom analysis and AI-based triage.
Cloud Firestore – Used as a persistent database for storing patient records and bed statuses.
Google Cloud Run – Used to deploy the application and make it accessible through a live .run.app URL.
Automatic Bed Assignment – Learned how to route critical patients to ICU beds and stable patients to General Ward beds.
Bed Status Management – Implemented the lifecycle Available → Occupied → Cleaning → Available.
Data Persistence – Understood why database storage is important so data survives page refreshes.
End-to-End Testing – Tested the complete workflow from patient registration → triage → bed assignment → discharge.
Cloud-based Architecture – Learned how multiple users can access the same application and see shared, up-to-date data.

### Time and challenges

“It took me approximately 2–3 days to complete the project. This included developing the ArogyaBed application, integrating Gemini AI for patient triage, connecting Cloud Firestore for data persistence, implementing automatic bed assignment and discharge workflows, and deploying and testing the app on Google Cloud Run.”

### What's next

I did this project today to learn how to build an AI-powered healthcare application, use Gemini for patient triage, store data with Cloud Firestore, and deploy an application using Google Cloud Run.

Another skill I want to learn is how to build more advanced AI applications and integrate real-time services such as Google Maps and notifications.

---

*Built with [NextWork](https://nextwork.ai) - [View this project](https://nextwork.ai/projects/86345cfc-0f8e-4965-b1d2-4d915496e0e0)*
