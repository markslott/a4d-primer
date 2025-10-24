# Time Clock Application Instructions

## Overview

The goal of this project is to make Agentforce Vibes develop a simple time clock application. The application allows employees to clock in and out, with all times automatically recorded and calculated.  This project only contains a very basic scaffolding to get started with.

## Prerequisites

Before starting, ensure you have:

- VS Code installed with the Salesforce Extension Pack
- Salesforce CLI installed
- Node.js version 20 or greater installed

Instructions on setting up your environment can be found here: <https://developer.salesforce.com/docs/platform/einstein-for-devs/guide/einstein-setup.html>

This project is designed to work in a scratch org, so you will need one of those as well.

When you deploy the app to test it, don't forget to add your user to your perm sets

## Getting Started

1. Clone this project to your workstation using `git clone https://github.com/markslott/a4d-primer`
2. Open Agentforce Vibes and click the Manage Agentforce Rules & Workflows button (bottom left of the frame). Enable all of the Global Rules.
3. Add a new custom workspace rule (call it my-custom-rule.md) and paste in the contents of `my-workflow-instructions.md`. This will add a couple of rules that might make things go a little smoother.
4. Put Agentforce Vibes into `plan` mode (button is in the bottom right corner of the frame) and enter the following prompt:

   ```text
   read the requirements.md document and plan the development of this application. Use the existing project structure as a scaffolding.
   ```

5. Once Agentforce Vibes has planned out its strategy, switch to Act mode and supervise. It will build, get things wrong, fix it, and eventually with some of your guidance get to a deployable app.

## Key App Features

- Single-button interface for clocking in/out
- Automatic time recording (no manual entry)
- Real-time status display
- Color-coded visual feedback (green for clock in, red for clock out)
- Responsive design for desktop and mobile
- Error handling and user feedback

## Technical Implementation Details

- Primary UI implemented as a Lightning Web Component (LWC)
- Server-side logic in Apex class for time calculations
- Custom object `Time_Card__c` for storing time entries
- Automatic calculation of duration and work week fields
- Proper error handling and user feedback mechanisms
