# Ticket Routing

## Problem Description

You are developing a ticket routing system for a company's support desk. Each incoming ticket needs to be classified and routed to the appropriate department.

## Input

Two data files:

1. `tickets.csv` - Support tickets in CSV format with the following columns:
   - `ticket_id`: Unique identifier
   - `timestamp`: When the ticket was created
   - `title`: Brief description
   - `description`: Detailed information about the issue
   - `priority`: High, Medium, or Low

2. `departments.json` - A JSON dictionary with department information:
   ```json
   {
     "DEPARTMENT_CODE": {
       "department_name": "Department Name",
       "contact_email": "email@example.com",
       "contact_person": "Contact Person",
       "priority_level": 1
     },
     ...
   }
   ```

## Task

1. Parse the CSV file containing tickets
2. Use an LLM to classify each ticket into one of these departments:
   - Technical IT (TECH-IT)
   - HR/Personnel (HR-PERS)
   - Facilities (FACIL)
   - Finance (FIN)
   - External Customer Support (CUST-SUP)
3. Generate a mock email for each ticket to the appropriate department

## Output

For each ticket, your program should output:
- Which department it was assigned to
- A mock email with:
  - To: department contact email
  - Subject: Contains ticket ID and title
  - Body: Includes ticket details and appropriate context

## Example

Input ticket:
```
T-1001,2025-04-01 09:15:23,"Computer won't boot","When I press the power button on my desktop, nothing happens. I've checked that it's plugged in properly.",High
```

Expected output:
```
Ticket T-1001 assigned to: Technical IT

To: it.support@company.com
Subject: [HIGH] Ticket #T-1001: Computer won't boot
Attention: Alex Johnson

A new ticket has been assigned to your department:

Ticket ID: T-1001
Submitted: 2025-04-01 09:15:23
Priority: High

Description:
When I press the power button on my desktop, nothing happens. I've checked that it's plugged in properly.

Please address this ticket according to its priority level.
```

## Constraints
- You must use an LLM to classify the tickets
- All tickets must be routed to exactly one department
- No actual emails will be sent (mock functionality only)