# Prestartr System Documentation

## Overview

Welcome to the documentation for the Prestartr system!

Prestartr appears to be a web-based software system designed to help manage operational work involving coordination between people, equipment, clients, and finances. Its main goal is to organize and track work, manage the necessary resources (like staff and machinery), handle scheduling, keep track of costs, and manage relationships with external companies.

This documentation aims to provide a clear understanding of the system's different modules and how they work together.

## System Architecture Diagram

The following diagram shows the high-level relationship between the core modules identified in the Prestartr system:

```mermaid
graph TD
    A[Prestartr Application] --> People(People Module);
    A --> Companies(Companies Module);
    A --> Plant(Plant Module);
    A --> Job(Job Module);
    A --> WO(Work Order Module);
    A --> Finance(Finance Module);
    A --> Scheduler(Scheduler Module);
    A --> Catalogues(Catalogues Module);
    A --> Forms(Forms Module);
    A --> Files(Files Module);
    A --> KB(Knowledge Base Module);

    %% Core Module Interactions
    Job --> People;
    Job --> Plant;
    Job --> Companies;
    Job --> Finance;
    Job --> Catalogues;

    WO --> People;
    WO --> Plant;
    WO --> Companies;
    WO --> Finance;
    WO --> Catalogues;

    Scheduler --> Job;
    Scheduler --> WO;
    Scheduler --> People;
    Scheduler --> Plant;

    Finance --> Job;
    Finance --> WO;
    Finance --> Companies;
    Finance --> Catalogues;

    Catalogues --> Job;
    Catalogues --> WO;
    Catalogues --> Finance;

    %% Supporting Module Usage (Linked from core modules needing them) - Using pipe syntax for labels
    Job ---|"Uses"|---> Forms;
    WO ---|"Uses"|---> Forms;
    Job ---|"Attaches"|---> Files;
    WO ---|"Attaches"|---> Files;
    Job ---|"References"|---> KB;
    WO ---|"References"|---> KB;
    People ---|"Uses"|---> Forms;  %% Example: Forms might be used in People module too
    Companies ---|"Attaches"|---> Files; %% Example: Files might be attached to Companies