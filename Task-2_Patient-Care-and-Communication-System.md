Task 2: Patient Care & Communication System

Role: Business Analyst – Clinic Operations

What problem I am trying to solve

In small clinics, a lot of the doctor’s time is lost in patient communication.

Currently:

Patients message the doctor directly on WhatsApp

Follow-ups are remembered mentally

Messages are sent randomly and manually

The doctor keeps switching between consultation and WhatsApp

This creates:

unnecessary stress for the doctor

missed follow-ups

inconsistent patient communication

The goal of this task is to remove WhatsApp chaos, automate routine communication, and ensure that the doctor is involved only when really needed.

Design principle I followed

Doctor time is extremely limited

Routine communication should not reach the doctor

Human judgment is needed only for exceptions

The system must be simple enough for clinic staff to run daily

No new software is introduced.
Only HMS data + Google Sheets + Google Forms are used.

Step 1: Classify Patient Message Types (One-time setup)

Not every patient message needs a doctor’s input.
So the first step is to clearly classify message types.

Message Type Classification
Message Type	Example	Doctor Input Needed
Follow-up Reminder	“Please visit on Aug 5”	No
Post-procedure Care	“Mild swelling is normal”	No
Side-effect Advisory	“Nausea may occur”	No
Custom Instruction	“Avoid sun exposure for 7 days”	Yes
Patient Question	“Is itching normal?”	Yes

This classification helps separate routine work from exceptions.

Step 2: Care Control Sheet (Main Working Sheet)

I design one central Google Sheet called Care_Control.
Every patient interaction is tracked here.

Sheet Columns

Patient Name

Phone Number

Visit Type (OPD / Procedure)

Message Type

Message Text

Doctor Approval (Required / Not Required)

Status (Pending / Sent / Closed)

This sheet becomes the single source of truth for patient communication.

Step 3: How Daily Entries Are Created

Appointment and prescription data comes from HMS

Based on visit type, the message type is auto-filled

For routine messages, message text is pre-filled

For custom instructions, message text is left blank

This ensures that most messages do not require doctor input.

Step 4: Doctor Review Window (Every 3–4 hours)

The doctor is involved only in short, focused review sessions.

Review Process

Filter Care_Control sheet where:

Doctor Approval = Required

Status = Pending

Sit with the doctor for 10 minutes

Doctor either:

approves the message, or

dictates a short instruction

What the doctor never does

Types messages

Opens WhatsApp

Replies individually

This protects the doctor’s attention and reduces context switching.

Step 5: Patient Questions Handling (Google Form)

Patients are instructed not to message the doctor directly.

Instead:

Patients submit questions using a Google Form

Form fields include:

Name

Phone

Question

Urgency (Routine / Urgent)

Responses go to a separate sheet called Patient_Questions.

Handling Process

Questions are batched every 3 hours

Reviewed once with the doctor

Answers are recorded and sent

Status is updated accordingly

This avoids constant interruptions.

Step 6: Message Dispatch Rules

Messages are sent only when all conditions are satisfied:

Message text is filled

Status = Pending

Doctor Approval is either:

Not Required, or

Approved

Status Flow

Pending → Sent → Closed

This ensures no message is sent accidentally or without approval.

Step 7: Daily Closing Check (5 minutes)

Before clinic closing:

Filter messages with Status = Pending

Ensure nothing important is missed

Reschedule if required

This acts as a final safety net.

Final Outcome of This System

Routine patient communication is automated

Doctor reviews only exceptions

WhatsApp chaos is eliminated

Follow-ups are not missed

Doctor spends less than 10 minutes per review session

The system is simple, realistic, and can be started immediately without new tools.
