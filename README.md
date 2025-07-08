# Willow-Prescription-Filling-Process
A concise overview of the end-to-end prescription order process in Epic Willow, including order routing, work queue handling, and Omnicell integration. Designed for healthcare IT and pharmacy workflow optimization.

## What is Surescripts?
It is a nationwide health information network that enables secure electronic transmission of prescriptions and other health data between healthcare providers and pharmacies. It receives electronic prescriptions (eRx) from providers and sends them to retail pharmacies, replacing the need for paper or faxed prescriptions.

## What is Omnicell?
It is an automated medication dispensing system commonly used in inpatient and outpatient settings. It is integrated with Epic Willow to manage inventory, dispense medications securely, and track real-time medication usage at the point of care.

## What is Order Composer?
It is the Epic module used by clinicians to create and manage medication orders. It ensures providers enter all necessary details (dose, route, frequency, etc.) in a structured, standardized format to reduce errors and support downstream processing.

## What is Order Transmittal Engine (OTE)?
OTE is the internal Epic engine responsible for routing medication orders from Epic to the appropriate downstream system, such as Willow Ambulatory, Willow Inpatient, or external systems.It acts as the “delivery service” that moves orders to where they need to go for fulfillment.

## What is Order Transmittal Config (OTC)?
OTC is the configuration module for OTE in Epic, where routing rules are defined and maintained. It determines how, when, and where medication orders are transmitted — based on settings like provider, department, medication type, or encounter type.

## What is Rx Routing?
Rx Routing is the logic within Epic that determines the route a prescription takes once it's ordered — whether it’s sent to a retail pharmacy via Surescripts, to an in-house pharmacy, or held for printing. It decides if a medication goes through e-prescribing or manual processes, based on insurance, location, or delivery preferences.

## What are Medication Routing Rules?
These are configurable rules within Epic that guide how and where medication orders are routed. 
- Routing can depend on factors such as encounter type (inpatient vs. ambulatory), formulary status, or whether the medication is controlled.
- Ensure medications are routed to the correct pharmacy system (e.g., Omnicell, external retail pharmacy) based on clinical and operational needs.
