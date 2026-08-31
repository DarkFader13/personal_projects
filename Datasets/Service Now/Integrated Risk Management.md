> Integrated risk management (IRM) is a set of practices, supported by a risk-aware culture and enabling technologies, that improve decision making and performance through an integrated view of how well an organization manages its unique set of risks.

## GRC Architecture
### Regulatory Requirements

- Organizations must manage complex industry regulations.    
- Regulations vary by geography and industry (e.g., PCI DSS for credit card data).    
- PCI DSS reduces fraud by enforcing stricter data handling practices.    

### Authority Documents & Citations

- Stored in **Authority Document table** (name, version, publish date).    
- Can include regulations, contractual obligations, international standards.    
- Documents broken into **citations** (specific compliance requirements).    
    - Example: PCI citation → visitor authorization before accessing cardholder data.        

### Policies & Control Objectives

- Policies define company culture (security, access, diversity, sustainability).    
- Policies may be driven by citations or internal culture.    
- **Control objectives** are breakdowns of policies.    
- Control objectives should be linked to relevant citations.    
- Compliance is measured at control objective level → rolls up to citations and authority documents (“measure once, satisfy many”).    

### Risk Frameworks & Statements

- **Risk framework** = group of risk statements.    
- **Risk statement** = impact if risk occurs (can be parent/child).    
- Frameworks define which risks/controls are tracked.    

### Entities & Scoping

- **Entity types** = categories (e.g., locations, vendors, processes, departments).    
- **Entities** = unique items under those types (e.g., London HQ, Vendor X).    
- Control objectives and risk statements are **scoped** to entity types.    
- Generates multiple risks/controls per entity (not duplicates → tied to different entities).    

### Monitoring & Testing

- **Test plans** → validate control design & operation (useful for audits).
- **Test templates** → reusable for automation.    
- **Indicators** → monitor risks/controls, collect evidence (manual/basic/scripted).    
- **Issues** → created manually or automatically (e.g., control failure).    
- **Assessments** → control attestations & risk assessments.    

### Policy Exceptions & Risk Response

- Policy exceptions allow temporary exemptions from controls.    
- Can relate to issues or control objectives.    
- **Risk responses**: mitigate, avoid, transfer, or accept.    
- Tasks assigned to manage and track response activities.    

### Controls, Risks, and Compliance

- Controls link directly to risks.    
- Non-compliance of controls affects risk assessment.    
- Helps identify high-risk entities and areas of concern.    

### Audit Management

- Audits leverage prior work in risk/compliance apps.    
- Engagements scoped by **entities** (not entity types).    
    - Example: IT audit of California locations.        
- **Audit tasks** and **test results** integrated into audit.    
- Issues from risk/compliance are reused, with additional audit-specific issues possible.    
- Audit reports created to summarize findings.    

### Advanced Audit Features

- Audit plans        
- Auditable units        
- Milestones        
- Observations        
- Project/portfolio management integration (resource planning)

## Role assignment

> Within IRM, there is a parallel structure across the compliance and risk teams, in which the administrator inherits the manager role and the manager inherits the user role.


**Hierarchy**
- .developer
	- .admin
		- .manager
			- .user
				- .reader

The **compliance** team is responsible for managing policies and internal control procedures that are mapped to the organization’s compliance framework. The **risk** team is responsible for providing structured workflows to identify and manage risks, scheduling risk assessments, monitoring key risk indicators (KRIs), and responding to risk issues. The GRC **business user** role allows AGT employees to complete activities that compliance and risk teams need them to do; even though they are not members of compliance or risk teams. Users with the GRC **business user lite** role can perform only a subset of those tasks

**Three lines of defense model**
- First-Line: Staff in management positions (*process owners*) are primarily responsible for owning and managing risks associated with day-to-day operational activities. They are typically responsible for responding to risk assessments and control attestations. Other first line of defense responsibilities may include the design, operation, and implementation of controls.
- Second-Line: Responsible for identifying *emerging risks* in *daily business operations*. This line fulfills that responsibility by providing *compliance and oversight* in the form of *frameworks, policies, tools, and techniques* to support risk and compliance management.
- Third-Line: assesses *whether the first and second line functions are operating effectively* and are responsible for providing objective and independent assurance. The third line is charged with *reporting to the board and audit committee*

## Workspaces in GRC

### Overview

- Workspaces provide simplified, persona-based user experiences.    
- Each workspace includes:    
    - **Home page** with insights and quick links.        
    - **Single-page view** for critical daily information.       

### Compliance Workspace

- Targeted users:    
    - Corporate compliance managers        
    - IT compliance managers        
    - Corporate compliance analysts        
- Key capabilities:    
    - Track open/overdue issues        
    - Monitor acknowledgment campaigns        
    - Manage policy exceptions        

### Risk Workspace

- Targeted users:    
    - Operational risk managers        
    - IT risk managers        
    - Business operational risk managers        
- Key capabilities:    
    - Track controls by **testing status** and **indicator status**       

### Unified Tasks Page

- Centralized view of all tasks.    
- Features:    
    - Categorization (e.g., by task status).        
    - Filtering by parameters.        
    - Tracking initiated tasks and watchlisted tasks.        

### Issues Overview Page

- Dedicated view of all issues.    
- Provides:    
    - Open, overdue, and upcoming (7-day) issues.        
    - Grouping by state, type, rating, priority.        
    - **Performance trends**: open vs. closed over time.        
### List Page

- List view of GRC objects by user role.    
- Example: compliance manager sees all compliance-related records.    
- Role-based record creation available.

## Entity Framework

### Entities in Service Now

- **Definition**: People, places, objects, or things that are the target of risk and compliance activities.    
- Used to:    
    - Manage risks threatening the organization.        
    - Apply controls for compliance.        
    - Scope audits.        
- Examples:    
    - **People**: department heads, managers, team members.        
    - **Places**: warehouses, distribution sites.        
    - **Objects/Things**: servers, financial systems, business processes.        
    - **Abstracted groupings**: server builds, applications, cost centers.        

### Importance of Entities

- Traditional GRC without entities relies on **sampling** (e.g., a few servers audited).    
- Issues with sampling:    
    - One failed server → entire control fails.        
    - Non-critical or retiring items can skew results.        
    - Missed non-compliant items resurface in later audits.        
- With entities:    
    - Each requirement/control is assigned at the entity level.        
    - Non-compliance is tracked per entity → accountability lies with entity owner.        
    - Continuous monitoring prevents last-minute audit failures.        

### Platform Capabilities

- Entities can leverage existing platform data:    
    - CMDB tables.        
    - HR, Security Ops, or other foundational applications.        
- Entities can be **grouped** by shared characteristics.    
    - Filters define entity grouping → automation maintains membership.        
    - Non-qualifying items automatically removed.

### Entities, entity types, and entity classes
- **Entities** are the objects against which we manage risks that threaten the organization, on which we apply controls to ensure compliance, and that we scope for an audit as part of an engagement. *Entity + control objective = control*
- **Entity types** are dynamic categories containing one or more entities. They are associated with policies, control objectives, risk frameworks, and risk statements.
- **Entity classes** identifies common information about a set of entities that can be used when creating reports and assigning advanced risk assessments. *Every entity is assigned to one entity class*
	- **Entity tiers** are a way for an organization to logically group entity classes and then filter reports by those groupings.

### Entity type scoping
> Entity type scoping is the process of determining which dynamic categories are needed by an organization for continuous monitoring.

- **Operational**: Scoping is done at the *individual object* level, such as a specific user, project, or CI level. This approach is useful for industries or scenarios that can’t have any control failures.
- **Strategic**: Scoping is done at a higher-level, such as using business processes or services. This approach doesn't have the individual level of assurance found at the operational level.
- **Entity filters** automate the process of creating entities. An entity filter looks at existing ServiceNow data in a source table and generates entities that meet entity filter conditions.

### Entity Ownership

> Entity owners are determined on the entity filter. Automation is available for keeping entity owners in sync with a field on the source record. In addition to being able to sync the owner between the source record and the entity, it is also possible to sync the entity owner with the controls and risks related to the entity using auto-update owner 


## Compliance Management
> Corporate compliance means having internal policies and procedures in place to prevent and detect violations of applicable laws, regulations, and ethical standards. Regulations are issued by regulatory bodies for many diverse reasons, such as to regulate the way business is conducted to ensure ethical practices and fair competition.

### Regulations, Standards and Regulations

A **regulation** is a law or rule governing the behavior and practices of an industry or market that is set and maintained by a constituted authority or regulatory body. A **standard** is benchmark circulated by a regulatory agency and created to enforce the provisions of legislation. A **framework** is a group of underlying and interrelated procedures, policies, regulations, guidelines, codes of conduct, and other regulatory documents sourced from legislation and meant to codify and clarify the intent of a law/act/regulation.

### Authority Documents & Citations

**Authority documents** compile the regulatory content that business processes follow for compliance. Authority documents are housed in the ServiceNow instance at the top level of the compliance framework hierarchy. **Citations** map from authority document, and control objectives map from the citations.

### Policies, control objectives, and controls

A **policy** defines an internal practice that an organization or business process must follow to ensure compliance and reduce risk exposure. Policies can be categorized and related to control objectives. A **control objective** is an objective, direction, or standard that acts as guidance for company interactions and operations. Control objectives are often based on citations. A **control** is the implementation of a control objective for a scoped entity:
- Once an entity type is associated with a control objective, controls are generated for each entity in an entity type
- The entity owner is the default control owner
- Fields inherited from the control objective record, such as name and description, are read-only
- Standalone controls that are not related to a control objective can be created; however, it is not recommended. The control MUST be related to a single entity.

A **standard control** is generated for each entity, establishing a *1:1 relationship* between the standard control and an entity. This requires each control to be tested for its entity. A standard control can be converted to a common control. A **common control** can be associated with multiple entities called reliant entities, establishing a *1:M relationship* between the common control and the entities. Common controls cannot be auto-generated; only a standard control can be converted to a common control

### Attestations, indicators, and control test

**Control attestations** are surveys that gather evidence to prove that a control is implemented. The attestation provides documentation that the control owner has a defined method to measure the control. **Indicators** are used to measure if a control is effective or not and are powerful data collectors. They are the manual or automated steps performed to measure the effectiveness of the process, system, or method identified in the control attestation. **Control tests** can be part of an audit or compliance process used to validate if the control method is effectively designed and is operationally effective.

## Risk Management

> Inherent risk: risk level without controls or mitigating actions (Impact x Likelihood). Controls can be preventative, detective, or corrective. Residual risk is the leftover risk after the implementation of controls. Target risk is the desire risk an organization would like to achieve in the future.

A **risk statement** is a general statement about a potential risk that can occur anywhere in the organization. **Risk** is the likelihood of a given threat against a potential vulnerability and the resulting impact of that adverse event on the organization. Risk statements can be organized into **risk frameworks** to group similar risk statements into manageable categories. **Risk library** contains all risk frameworks and risk statements. **Risk register** is the central repository for all potential risks that could occur at anytime, anywhere in the organization. **Mitigating** controls are methods used to reduce the overall likelihood and impact of a threat. **Risk appetite** is the degree of uncertainty (risk) an organization is willing to accept in pursuit of its objectives. **Risk tolerance** is the amount of deviation from an organization’s risk appetite that is accepted to achieve a specific objective based on specified parameters. **Risk threshold** is the level of risk exposure above which risks are addressed, and below which risks may be accepted. A **risk heatmap** is a data visualization tool that graphically represents an organization's risk data. **Indicators** are data collectors that continuously monitor risks and controls. An **issue** is a task that allows end users to track the response to remediate or accept the issue.

### Risk Architecture
The application includes the following key features:

- Scope entities
- Create the risk library and risk register
- Assess and respond to a risk using classic risk assessments. Please note that this capability is limited compared to the advanced risk assessment functionality installed with GRC: Advanced Risk
- Monitor risks with indicator templates and indicators
- Manage issues
- Build and use reports and dashboards

**Advanced risk assessment**

- Configure multiple types of advanced risk assessments with the Advanced Risk Assessment engine
- Automate risk assessment responses using automated factors
- Assess any record in ServiceNow without creating a risk or an entity

**Risk aggregation and appetite**

- Define and visualize a multi-level hierarchy of risk that enables the creation of a centralized risk taxonomy
- Support bottom-up risk assessments and rollup of scores across entity hierarchy, risk hierarchy, or a combination of both.
- Define risk appetite

**Risk events**

- Capture all types of risk events, such as near-misses and actual losses, with financial and non-financial impacts
- Associate risk events to risks and controls and use them to drive quantitative risk assessments and identify control deficiencies