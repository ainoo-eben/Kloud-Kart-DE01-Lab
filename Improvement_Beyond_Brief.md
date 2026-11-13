# Kloud Kart: Improvement beyond the brief

## 1. Proposed Improvement

I propose building a data strategy implementation tracker for Kloud Kart.

The proposed 12-month data strategy gives Kloud Kart a direction and a roadmap. However, Nana will still need a practical way to monitor implementation, follow up on responsibilities, identify delays and communicate progress to management.

The tracker will turn the written roadmap into an interactive management tool.

## 2. What the tracker will do

The tracker will provide Nana with a central place to monitor the progress of the data strategy.

Its main features will include:

- **Roadmap tracking:** Display activities under each quarter and show whether they are not started, in progress, completed or delayed.
- **Task ownership:** Record the person responsible for each activity and its expected completion date.
- **Milestone monitoring:** Highlight important deadlines, including the 90-day customer data complaint response.
- **Risk and blocker tracking:** Record implementation challenges, their potential impact and the actions being taken to address them.
- **Budget tracking:** Record estimated and actual spending across major implementation areas, such as infrastructure, cloud services and staffing.
- **Progress reporting:** Generate a summary of completed activities, outstanding work, delays and major risks for management updates.

## 3. Value to Nana and Kloud Kart

This improvement will help Nana move beyond having a written plan to actively managing its implementation.

It will give her better visibility into:

- Whether the strategy is progressing according to schedule.
- Which activities require attention or management support.
- Who is responsible for outstanding work.
- Whether implementation costs are staying within expectations.
- What progress can be communicated to the board.

**Estimated time saving:** Assuming Nana and colleagues currently spend about two staff-hours each week collecting and consolidating updates, and the tracker cuts that effort roughly in half, it could save about one staff-hour per week, or approximately 50 hours over a 50-week year. This is a planning estimate, not a measured result; I would validate the baseline and actual saving during a pilot. I have not estimated a monetary saving because salary rates are not available.

## 4. Why This Goes Beyond the Brief

The original brief requires a 12-month roadmap with quarterly outcomes that Nana can verify. It does not require a working application for monitoring the roadmap's implementation.

The tracker adds a management capability that supports the recommended strategy without duplicating the warehouse, reporting pipeline or customer data governance solution.

It is therefore an additional tool for helping Nana manage the changes we have recommended.

## 5. Proposed Implementation

I will build a working prototype using:

- **Python:** Application logic and data handling.
- **Streamlit:** Interactive dashboard and user interface.
- **SQLite:** Lightweight storage for tasks, milestones, risks and budget records.

The prototype will use fictional Kloud Kart implementation data because access to the company's internal systems and actual project records has not been provided.

The application will be designed so that activities, owners, deadlines, statuses, risks and costs can be updated as implementation progresses.

## 6. Scope and Limitations

The prototype will demonstrate the core tracking and monitoring features. It will not automatically connect to Kloud Kart's production systems, manage employee accounts or retrieve actual financial information.

Real implementation would require Nana and the relevant team members to maintain accurate updates.

## 7. Expected Outcome

At the end of the build, I expect to deliver a working dashboard that allows Nana to view the 12-month roadmap, update implementation progress, monitor deadlines, record risks and review project spending from one place.

The value is simple: the data strategy will not just tell Kloud Kart what to do; Nana will have a practical way to see whether it is being done.
