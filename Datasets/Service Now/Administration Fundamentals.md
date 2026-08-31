> ServiceNow Platform is a Application Platform as a Service (aPaaS). Its a loop between the Client and the Server

**User Access and Personas**
- System Administrator: access to all platform features. applications, functions and data  
- Specialized Administrator: specific admin access
- Process User: fulfil ITIL activities associated with the ITIL workflow 
- Approver: can perform all requestor actions and allows users to view/modify approval record directed to them 
- Requester: do not have roles but can submit and manage their own requests, access public pages, etc
- Users: are represented by a record on the User `sys_user` table 
- Group: a collection of users represented by a record on the Group `sys_user_group` table 
- Role: used to define access at the application module, and/or Access Control List (ACL), roles can contain other roles, group and users. Represented by a record on the Role `sys_user_role` table.
- Delegated developers: non-administrator users and group which are assigned one or more permissions to develop applications 
 
 **Baseline implementation** is a set of installed application on a ServiceNow instance before any configuration or customization. Applications and features can be activated from either Plugins, ServiceNow Store or Request from ServiceNow. **Configuration** consists primarily of things that can be done without coding. **Customizations** is adding additional functionality and features that does not exist in the platform. *Best practice is to search **Plugins** first* 
 
 An **Instance** is a copy of a ServiceNow environment specific to a customer. A **production** instance is where employees do their work. A **personal instance** or **non-production instance** can be used to to explore/configure/build an application before implementation. **Personal Develop Instance (PDI)** is an independent instance to configure develop and learn.  

A **list** displays a set of records from a table within the context frame; each row is a **record**, each column is a **field**, each cell is a **data value**. A **choice or reference** field is pre-defined and can be declared dependent on another field on the same table. *Dependent fields* have limited available values.  **Dot-Walking** gathers information from a series of table through reference fields. A **view** is a custom subset list. A **filter** is a set of conditions applied to a table to isolate a subset, consists of 3 components: *Field*, *Operator*, and *Value*. 

The **Context Menu (≡) ⋮** provide different levels of controls for a list or view. The **List Editor** allows you to edit records in-line. A **personalized list** modifies the layout of a list only for an individual user, should only be used for temporary situations.

For a view the **list collector** can be used to add/remove/reorder fields.
- Related field appear in green (+).
- True/False fields displays as a check box on on form. 
- Choice fields are indicated by dropdown arrows.
- Reference fields are indicated by a magnifying glass icon.


A **form** displays the fields from one record, which can also have *views*. Form configuration involves changing the form layout and related list layout: **Form Builder**, **Form Design**, and **Form Layout**. **Data Dictionary** entries can be added columns fields.

A **table** is a collections of records in the database. With a table a field can *hold a reference* to a record on another table. Two or more tables can be related in a *bi-directional relationship*. Tables can be *joined* using the **Database Views Plugin**. A table can be **extended** into a larger child table. A parent table that is *not an extension* of another table is a **base table** (or source table). Tables that exist in the base default system are called **core tables**, tables creates after by admin or developers are called **custom tables**. A **schema map** is a graphical representation of other tables relating to a specific, this is available to users with personalize_dictionary or admin roles.

The access control list contain an instance's Access Control rules. A **import set** is a tool used to import data from various sources, and map that data into ServiceNow tables. An **import set table** is a staging area for records imported from a data source. A **transform map** is a set of field maps between an import set table and the target table. **Coalescing** a field (or multiple fields) means the fields will be used as a unique key during imports. If the keys match the field(s) on that row is updated. Else a new record is inserted into the database. Coalescing can be done on a single field, multiple fields or conditionally.

The **configuration management database** is a series of tables and fields that contain all of the Configuration Items (CIs) controlled by the company. **Configuration items** can be tangible or intangible devices or applications in the CMDB such as firewalls, computers, email service and services. **Dependency views** provide an interactive graphical interface to visualize relationships between configuration items. A **Common Service Data Model (CSDM)** is a CMDB-based framework that identifies where to place data for products. It contains out-of-the-box CMDB core tables, standard terms, definitions, recommended mappings, and best practices. **ServiceNow Discovery** scans the network inventory devices and applications. **Service Mapping** (Top-down discovery) augments the CMDB with IT relationships and dependencies.

**Knowledge Management** allows users to create, categorize, review approve, and browse important information in a centralized location. An article can only be linked to one knowledge base. **User Criteria** defines conditions control user permissions on knowledge articles. **Knowledge Base: Workflows** - the publishing and retiring for a knowledge article are controlled by workflows

The **Service Catalog** is a robust ordering system for services and products. Service catalog major components:
- Items: includes Hardware, Software, Services, Record Producers
- Record Producers: a form that produces a task record
- Variables: questions/options to specify items
- Variable Sets: a collection of variables sharable between items
- Flows: approval processes and stages to drive the request

**Virtual Agent** is a conversational platform that helps users obtain information, make decisions and perform common task within a messaging interface. 

Automate business logic with **Workflow Studio**. **Triggers** can be record-based, date-based or application-based. **Actions** are operations executed by the system. For each action in a flow workflow studio adds a **data pill** to store the results and can be use in subsequent actions. **Integration Hub** offers several pre-built sets of integration actions (**spokes**) to interact with common third-party applications. **Playbooks** enables owners to author cross-enterprise workflows and create a single unified process.

**Visualizations** allow users to view and analyze ServiceNow Data. **Dashboard** can display multiple Platform Analytics, visualizations and widgets on a single screen that can be shared. **Performance Analytics** provides information about performance iteratively over time.

**Notifications** can be triggered by events in the platform and require no scripting knowledge. **Subscriptions** allow users to be informed of various activity occurring in the platform whether it relates to them or not. Subscriptions support email and also SMS notifications.

**Predictive Intelligence** uses machine learning to set field values during record creation. **Now Assist** console has other options for genAI options. **Sidebar** can be used to real-time collaborate around a Workspace record. Docked chat windows (**Fulfillers**) can access multiple sidebar discussions at the same time. Sidebar is integrated with **activity stream**, i.e. added automatically to the activity stream.

Scripting in ServiceNow or Platform Scripting is the customization of an instance and/or applications using JavaScript. A **User Interface (UI) Policy** is a rule that is applied to a form to dynamically change information or the form itself. UI Policies execute on the client side. UI Policies are used to manage the user experience and data integrity. **Data Policy** is a rule that enforces data consistency by setting fields as mandatory and/or read-only. Data Policy executes on the server side but can also run as a UI Policy on the client side. UI Policies only apply to data entered on a form through a standard browser. **Client Scripts** make real-time changes to the appearance of the user interface especially forms. A **Business Rule** is configured to run for a database action, can be set to run before or after the action has occurred. Business Rules execute on the server side.

**Application scoping** involves identifying and control access to available artifacts and data.  An **Update Set** is a group of configuration change that can be moved from one instance to another. Update sets can be retrieved from a remote instance and updated in a production environment. What is captured in an a update set?: (Process Records not Data)
- Business rules
- Client Scripts
- UI Policies
- Fields
- Forms and Form Sections
- Report Definitions
- Tables
- Views
- List Configurations
- Roles
- Flows/Published Workflows

**Stats Tools** record statistics for system activities that affect performance such as execution of queries, scripts, and transactions. **Automated Test Framework (ATF)** can be used to create and run automated tests on ServiceNow instance after modifying it. Review the **Shared Responsibility Model**