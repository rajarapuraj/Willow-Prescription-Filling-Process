# Willow-Prescription-Filling-Process
A concise overview of the end-to-end prescription order process in Epic Willow, including order routing, work queue handling, and Omnicell integration. Designed for healthcare IT and pharmacy workflow optimization.

## Table of Contents
- [Overview](#overview)
- [Definitions](#definitions)
- [Sources of Prescription Order](#sources-of-prescription-order)
- [Willow WorkQueues](#willow-workqueues)

## Overview
The prescription fulfillment journey in Epic Willow is a meticulously orchestrated process that begins the moment a provider clicks "**Order**". From that point forward, a highly coordinated and technology-driven workflow ensures safe, timely, and accurate medication delivery.

The process initiates in Order Composer, where the provider enters detailed medication instructions. The **Order Transmittal Engine (OTE)**, guided by the rules set in **Order Transmittal Config (OTC)**, then determines the appropriate destination—whether that’s a retail pharmacy, an in-house dispensing location, or an automated system.

Routing decisions are managed through **Rx Routing** and **Medication Routing Rules**, which evaluate clinical context and operational settings to choose the optimal delivery path. For retail prescriptions, **Surescripts** handles secure electronic transmission, while systems like **Omnicell** manage internal dispensing workflows.

The order then navigates through more than **15 smart work queues in Epic Willow**, each designed to validate, verify, and process the prescription with precision. This intelligent and layered infrastructure ensures the right medication reaches the right patient—safely and efficiently.

## Definitions
### What is Surescripts?
It is a nationwide health information network that enables secure electronic transmission of prescriptions and other health data between healthcare providers and pharmacies. It receives electronic prescriptions (eRx) from providers and sends them to retail pharmacies, replacing the need for paper or faxed prescriptions.

### What is Omnicell?
It is an automated medication dispensing system commonly used in inpatient and outpatient settings. It is integrated with Epic Willow to manage inventory, dispense medications securely, and track real-time medication usage at the point of care.

### What is Order Composer?
It is the Epic module used by clinicians to create and manage medication orders. It ensures providers enter all necessary details (dose, route, frequency, etc.) in a structured, standardized format to reduce errors and support downstream processing.

### What is Order Transmittal Engine (OTE)?
OTE is the internal Epic engine responsible for routing medication orders from Epic to the appropriate downstream system, such as Willow Ambulatory, Willow Inpatient, or external systems.It acts as the “delivery service” that moves orders to where they need to go for fulfillment.

### What is Order Transmittal Config (OTC)?
OTC is the configuration module for OTE in Epic, where routing rules are defined and maintained. It determines how, when, and where medication orders are transmitted — based on settings like provider, department, medication type, or encounter type.

### What is Rx Routing?
Rx Routing is the logic within Epic that determines the route a prescription takes once it's ordered — whether it’s sent to a retail pharmacy via Surescripts, to an in-house pharmacy, or held for printing. It decides if a medication goes through e-prescribing or manual processes, based on insurance, location, or delivery preferences.

### What are Medication Routing Rules?
These are configurable rules within Epic that guide how and where medication orders are routed. 
- Routing can depend on factors such as encounter type (inpatient vs. ambulatory), formulary status, or whether the medication is controlled.
- Ensure medications are routed to the correct pharmacy system (e.g., Omnicell, external retail pharmacy) based on clinical and operational needs.

## Sources of Prescription Order
1. **External Prescribers**: Electronic prescriptions sent from providers outside the organization using the Surescripts network. May show status like "Pending prescription entry" or "Patient not found". Requires manual patient matching and verification before processing.
   
2. **EpicCare Ambulatory/Inpatient**: Prescriptions written by internal Epic providers during ambulatory or inpatient visits. These will fall under "Flagged Prescriptions" tab in Hyperspace with a First Fill Review flag. These prescriptions will not proceed to fill until a pharmacist or technician reviews and removes the flag. Linked to Patient's encounter and clinical data in Epic.

3. **Manual Entry by Pharmacy Staff**: Pharmacists or pharmacy technicians manually enter prescriptions based on verbal orders, written scripts, or phone calls, especially for controlled substances, verbal orders, or when e-prescription systems are unavailable.

4. **Order Entry Through Interfaces** (3rd Party Systems): Interfaces with external clinical or prescribing systems integrated with Epic (e.g., hospital CPOE systems or retail pharmacy systems). May also trigger work queue items if mappings or patient matches are uncertain.

5. **Renewals and Refills Requests**: Refill or renewal requests from patients (through MyChart) or providers. These must be approved or denied and may generate a new prescription.

6. **Standing Orders / Protocols**: Automatically generated prescriptions based on care plans or protocols (e.g., vaccination schedules, discharge meds). Often requires pharmacist confirmation before fill.

## Willow WorkQueues
**Initial Review WQ**: Prescriptions entered in Hyperspace (in the clinic or hospital), reorders approved through Surescripts that need to be reviewed before filling, and certain refills requested by patients directly from MyChart or an IVR (interactive voice response).

**Clinical Review WQ**: Prescriptions that have had first fill review but need to be reviewed by a pharmacist.

**DUR Reject WQ**: Prescriptions with drug utilization review (DUR) errors.

**Refill Too Soon and PA Required WQ**: Prescriptions that either are being refilled too soon or require prior authorization.

**Ready to Fill WQ**: Prescriptions that have had clinical review or refill review and are ready to be filled. Technicians manually print fill labels from this queue.

**Waiting for Stock WQ**: Prescriptions for which there is either insufficient inventory or a completion fill hold.

**Charging WQ**: Prescriptions with problems related to adjudication.

**Expected Discharge for Pick-Up WQ**: Prescriptions for patients being discharged who are not part of the meds to beds program (a service where hospital patients receive their discharge medications and personalized medication counseling at their bedside before leaving the hospital, eliminating the need to stop at a pharmacy).

**Ready to Verify WQ**: Filled prescriptions that need to be verified by a pharmacist.

**Will Call WQ**: Verified prescriptions ready to be sold in person.

**Waiting Patients WQ**: Patients physically waiting in the pharmacy for their prescriptions. Clicking on this queue opens the Waiting Patients list in Front Counter.

**Pending Refill Approval WQ**: Prescriptions that have outstanding refill authorization requests.

**All Pharmacist Work WQ**: Prescriptions that require a pharmacist to take the next action on them.

**Everything WQ**: Any prescription in the process of being filled, as well as any prescriptions with refills requested and no refills remaining.

**Everything for Me WQ**: Any prescription included in the Everything queue that you have the ability to act on in the system.

**NOTE**: The standard work queues that appear on the homepage can vary depending on the user. The work queues that you see aren't necessarily the work queues that a technician sees.

![Willow_Prescription Fill WorkQueue](https://github.com/user-attachments/assets/f970af98-fe6f-4d39-8247-53ec69f7455f)
