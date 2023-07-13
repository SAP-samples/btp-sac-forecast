# Simplify Business Decisions with SAP BTP and SAP Analytics Cloud
<!-- Please include descriptive title -->
<!--- Register repository https://api.reuse.software/register, then add REUSE badge:
-->
[![REUSE status](https://api.reuse.software/badge/github.com/SAP-samples/btp-sac-forecast)](https://api.reuse.software/info/github.com/SAP-samples/btp-sac-forecast)

## Purpose

This scenario is primarily intended to demonstrate how to integrate BTP extension application with analytics capabilities like reports, interactive dashboards, and visuals.

By the end of this scenario, you'll be able to:
*	Customize an extension application on BTP using calculation views within SAP Business Application Studio.
*	Set up a Live Data Connection from SAP Analytics Cloud to SAP HANA Cloud with SSO (Single Sign On) in a few steps to access application data in real time without having to set up the SAP HANA Analytics Adapter.
*	Use SAP Analytics Cloud as One Stop tool to build dashboards and stories, analyze and forecast business data.
*	Use one central point to access your application and analytics from SAP Build Work Zone, standard edition with rendering on different devices.

![Scenario Overview](scenario-overview.jpg)

## Business Scenario

* We will guide business analysts without deep statistical knowledge through the steps to perform a risk analysis forecast for a food delivery service that has several vendors delivering food to the company's customers.
* When service delivery issues arise, such as late deliveries, or goods delivered in unacceptable conditions to customers, risk manager John calculates the risk cost for each vendor, using a risk management application built on SAP BTP.

## Solution Architecture

 ![Solution Architecture](solution-architecture.jpg)

Let's go over the steps required to build this scenario:

1 - With help of system admin, You connect to the backend S/4HANA Cloud to fetch business partner data, or use a mock-server application built on CAP.

2 - Professional developer installs and customizes the risk management application using SAP Business Application Studio and adds analytics artifact modules like calculation views.

3 - Professional developer will deploy the app to Cloud Foundry runtime.

4 - With the help of SAP Analytics Cloud tenant admin, we will set up an SSO live connection to SAP HANA Cloud persistence.

5 - Citizen developers designs interactive analytics dashboards and reports for himself or others, he can also explore data from SAP Hana cloud in real time with Live Data Connection.

6 - Citizen developers seamlessly integrate Analytical content dashboard in SAP Build Work Zone, standard edition by calling SAC Story URL.

7 - A business user, in our case, a risk manager, can access the SAP Build Work Zone, standard edition service and open the risk management application along with analytics dashboard.
 

## Where to Start?

* Follow the below steps for quick start or start the [SAP Discovery Center Mission](https://discovery-center.cloud.sap/protected/index.html#/missiondetail/4265/4523/).

  | Step                                           | Description      |
  |------------------------------------------------|------------------|
  | Step 1: [Prepare](https://github.com/SAP-samples/btp-sac-forecast/tree/main/documentation/prepare)                                | Make sure prerequisites are fulfilled and all required systems are in place|   
  | Step 2: [Set Up](https://github.com/SAP-samples/btp-sac-forecast/tree/main/documentation/set-up)                                 | Set up and configure SAP systems and services |
  | Step 3: [Customize application](https://github.com/SAP-samples/btp-sac-forecast/tree/main/documentation/develop/open-app-in-BAS)                             | Add custom logic to Risk Management application |
  | Step 4: [Set up  a Live Data Connection](https://github.com/SAP-samples/btp-sac-forecast/tree/main/documentation/develop/create-live-conn)         | Set up a Live Data Connection between SAP HANA Cloud and SAP Analytics Cloud|
  | Step 5: [Develop visual reports](https://github.com/SAP-samples/btp-sac-forecast/tree/main/documentation/develop/create-story-sac)                 | Create Bar and Times Series charts reports in SAP Analytics|
  | Step 6: [Integrate reports](https://github.com/SAP-samples/btp-sac-forecast/tree/main/documentation/develop/integrate-story-SBWZ)                             | Integrate analytical reports in SAP Build Work Zone, standard edition|            

## Known Issues
No known issues.

## How to obtain support
[Create an issue](https://github.com/SAP-samples/btp-sac-forecast/issues) in this repository if you find a bug or have questions about the content.
 
For additional support, [ask a question in SAP Community](https://answers.sap.com/questions/ask.html).

## License
Copyright (c) 2023 SAP SE or an SAP affiliate company. All rights reserved. This project is licensed under the Apache Software License, version 2.0 except as noted otherwise in the [LICENSE](LICENSE) file.
