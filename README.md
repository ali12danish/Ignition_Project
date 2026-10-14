# Ignition Perspective SCADA

This is a personal project I built to demonstrate my ability to architect and develop database-driven SCADA applications using Inductive Automation's Ignition Perspective.


Instead of just putting basic screens together, I designed this project to work like a real-world industrial system. It simulates a pharmaceutical solvent preparation process, complete with SQL database integration, dynamic reporting, and secure operator controls.

![Overview Screen Desktop](Media/Overview_GIF.gif)




## Key Features & Architecture

I focused on building a backend that is efficient, secure, and easy to maintain:

* **Database-Driven Tags (SQL Server):** To make the system easy to update, I avoided hardcoding limits into the screens. Instead, the application automatically pulls process limits, engineering units, and statuses directly from a centralized SQL Server database.
* **Secure Operator Controls (E-Signatures):** Because this simulates a highly regulated pharmaceutical process, I built a custom E-Signature module. Critical actions—like starting a batch or overriding a valve—require the operator to authenticate with a password and leave a comment, fulfilling standard FDA compliance requirements.

![E-Signature GIF](Media/E_Signature_GIF.gif)

   
* **Automated Audit Logging:** All E-Signature events, state changes and user login or logout are intercepted by a global Python script and logged to a custom SQL table. This creates a reliable, permanent history of who took what action and when.
  
![Audit Logging GIF](Media/Audit_Logging_GIF.gif)

  
* **Reusable, Scalable Design:** I used User-Defined Types (UDTs) and templates so the project is easy to expand. For example, there is only one master "Valve Popup" design in the entire project. It dynamically updates its data based on exactly which valve the operator clicks, saving massive amounts of development time.

## Technology Stack
* **Platform:** Ignition 8.1 (Perspective Module)
* **Scripting:** Python / Jython (Using centralized Project Library scripts)
* **Database:** Microsoft SQL Server
* **Additional Modules:** Tag Historian, Reporting


## Project Demo

Here is a short demonstration showing the responsive screen layout, the secure E-Signature popups blocking unauthorized access, and the automated reporting engine.


[🎥 Click here to open the Project Demo Video](Project_Demo/Demo.md)


