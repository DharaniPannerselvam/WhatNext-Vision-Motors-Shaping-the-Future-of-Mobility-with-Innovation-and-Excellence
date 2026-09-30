WhatNext Vision Motors: Shaping the Future of Mobility with Innovation and Excellence

Salesforce CRM Implementation

WhatsNext Vision Motors is a Salesforce CRM project designed to streamline vehicle ordering, dealer operations, stock management, and test-drive communication.

The solution combines Salesforce configuration with Apex automation to improve order accuracy, reduce manual work, and provide a consistent customer experience.

Project Overview

Main Objectives

Automate vehicle ordering and stock validation.

Maintain vehicle, dealer, customer, order, and test-drive information.

Prevent orders when a vehicle is out of stock.

Reduce vehicle stock when an order is confirmed.

Automatically process pending orders when stock becomes available.

Send reminders for upcoming test drives.

Run pending-order processing automatically using Scheduled Apex.

Platform

Platform: Salesforce Developer Org

Application: WhatNext Vision Motors Lightning App

Technologies: Custom Objects, Record-Triggered Flow, Apex, Batch Apex, Scheduled Apex

Salesforce Components

1. Vehicle Dealer Custom Object

The Vehicle Dealer object stores information about dealers participating in the vehicle ordering process.

Configuration:

Label: Vehicle Dealer

Plural Label: Vehicle Dealers

Record Name: Dealer Name

Data Type: Text

2. Lightning App

A dedicated Lightning App named WhatNext Vision Motors provides centralized navigation for the project.

The application can include:

Vehicle

Vehicle Dealer

Customer

Order

Test Drive

Service Request

Reports

Dashboard

3. Test Drive Reminder Flow

A Record-Triggered Flow is used to send a customer an email reminder one day before a scheduled test drive.

Flow process:

Vehicle Test Drive record is created or updated.

Status is checked for Scheduled.

A scheduled path is created using the test-drive date.

Customer information is retrieved.

An email reminder is sent one day before the test drive.

4. Apex Trigger Handler

VehicleOrderTriggerHandler contains the business logic for vehicle orders.

The handler:

Validates vehicle stock before an order is processed.

Prevents an order when stock is unavailable.

Reduces vehicle stock when an order is confirmed.

5. Vehicle Order Trigger

The VehicleOrderTrigger runs on:

Before Insert

Before Update

After Insert

After Update

The trigger calls the VehicleOrderTriggerHandler to perform the required business logic.

6. Batch Apex

VehicleOrderBatch processes pending vehicle orders.

The batch:

Finds pending orders.

Checks vehicle availability.

Confirms eligible pending orders.

Reduces the available vehicle stock.

Updates the affected records.

7. Scheduled Apex

VehicleOrderBatchScheduler automatically starts the batch process.

The project model uses the following daily schedule:

0 0 0 * * ?

This runs the process every day at 12:00 AM (midnight).

Automation Flow

Customer
   |
   v
Vehicle Order
   |
   v
Stock Validation
   |
   +---- Stock Available ----> Confirm Order
   |                              |
   |                              v
   |                         Reduce Stock
   |
   +---- Stock Unavailable --> Pending Order
                                  |
                                  v
                           Batch Apex Processing
                                  |
                                  v
                         Stock Available?
                                  |
                                  v
                            Confirm Order

Testing Checklist

Test Case

Expected Result

Create vehicle with stock > 0

Vehicle record saves successfully

Create order for in-stock vehicle

Order proceeds according to configured automation

Create order when stock = 0

Order is prevented

Confirm an order

Vehicle stock decreases by 1

Create pending order

Order remains Pending while stock is unavailable

Add new vehicle stock

Pending order can be processed

Run VehicleOrderBatch

Eligible pending order becomes Confirmed

Create scheduled test drive

Reminder is scheduled

Reach reminder time

Customer receives the configured email

Check Scheduled Jobs

Daily processing job appears

Solution Architecture

Layer

Salesforce Component

Responsibility

Data

Vehicle / Dealer / Customer / Order / Test Drive

Stores CRM records

UI

Lightning App

Central navigation

Automation

Record-Triggered Flow

Test-drive reminders

Validation

Apex Trigger + Handler

Stock validation and updates

Processing

Batch Apex

Pending-order processing

Scheduling

Scheduled Apex

Automatic batch execution

Recommended Implementation Order

Create the Salesforce Developer Org.

Create the Vehicle Dealer custom object.

Create/configure the required project objects and fields.

Create the WhatNext Vision Motors Lightning App.

Create and activate the Test Drive Reminder Flow.

Create VehicleOrderTriggerHandler.

Create VehicleOrderTrigger.

Create VehicleOrderBatch.

Create VehicleOrderBatchScheduler.

Test the complete automation workflow.

Verify Scheduled Jobs.

Important Note

The Apex examples use Salesforce custom-field API naming conventions such as:

Vehicle__c

Status__c

Stock_Quantity__c

Verify the exact object and field API names in your Salesforce Developer Org before saving or executing Apex code.

Project Outcome

The completed Salesforce CRM design connects customer records, vehicles, vehicle orders, inventory validation, test-drive reminders, pending-order processing, and scheduled automation into a single workflow.

This project is intended as a practical Salesforce CRM implementation model and project reference.

Project Technologies

Salesforce CRM

Salesforce Lightning App

Custom Objects

Record-Triggered Flow

Apex

Apex Trigger

Apex Trigger Handler

Batch Apex

Scheduled Apex

Project Name: WhatNext Vision Motors
Project Type: Salesforce CRM Implementation
Primary Goal: Automate vehicle ordering and improve customer experience
