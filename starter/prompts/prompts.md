**AI Valdiation**

The AI Validation Agent validates employee onboarding submissions and determines whether the onboarding process can continue automatically or requires manual HR review.

The agent evaluates:

Employee information completeness
Required documentation
Data quality
Potential onboarding risks
Onboarding readiness

The output is consumed by the workflow's decision node to route employees into either the automated onboarding path or the HR review path.

**Prompt**

{
  "type": "object",
  "properties": {
    "isValid": {
      "type": "boolean"
    },
    "validationStatus": {
      "type": "string",
      "enum": ["approved", "needs_review"]
    },
    "missingDocuments": {
      "type": "array",
      "items": {
        "type": "string"
      }
    },
    "dataQualityIssues": {
      "type": "array",
      "items": {
        "type": "string"
      }
    },
    "riskFlags": {
      "type": "array",
      "items": {
        "type": "string"
      }
    },
    "recommendation": {
      "type": "string"
    },
    "confidenceScore": {
      "type": "number"
    }
  },
  "required": [
    "isValid",
    "validationStatus",
    "missingDocuments",
    "dataQualityIssues",
    "riskFlags",
    "recommendation",
    "confidenceScore"
  ]
}

Return ONLY a JSON object matching the schema.
Do not wrap the response in markdown.
Do not include explanations.
Do not return text before or after the JSON.

**Expected Business Outcome**

The AI Validation Agent produces:

Approval or review classification
Missing document identification
Data quality assessment
Risk detection
Recommendations for HR
Confidence scoring

This enables automated workflow routing and reduces manual onboarding review effort.

**Generate Onbaording Plan**

Generate a role-specific onboarding plan tailored to the employee's department, manager, location, and start date.
**Prompt**

Create a comprehensive onboarding plan for:

Employee: {{ $("Employee Intake2").item.json.firstName }} {{ $("Employee Intake2").item.json.lastName }}
Role: {{ $("Employee Intake2").item.json.role }}
Department: {{ $("Employee Intake2").item.json.department }}
Start Date: {{ $("Employee Intake2").item.json.startDate }}
Manager: {{ $("Employee Intake2").item.json.manager }}
Location: {{ $("Employee Intake2").item.json.location }}

Generate a detailed, role-specific onboarding plan including:
- Unique plan ID
- Timeline (typically 2-4 weeks)
- Phases with specific tasks for each week
- Key milestones and checkpoints
- Assigned onboarding buddy
- Required training modules
- Equipment and access needs

Tailor the plan to the specific role and department.

**Business Purpose**

The onboarding planner creates:

Personalized onboarding experiences
Structured onboarding milestones
Department-specific training plans
Resource allocation guidance
Employee success roadmaps

**Generate Welcome Email**

Generate a personalized onboarding welcome email using employee information and onboarding plan details.

**Prompt**

Generate a warm, professional welcome email for:

Employee: {{ $("Employee Intake2").item.json.firstName }} {{ $("Employee Intake2").item.json.lastName }}
Role: {{ $("Employee Intake2").item.json.role }}
Department: {{ $("Employee Intake2").item.json.department }}
Start Date: {{ $("Employee Intake2").item.json.startDate }}
Manager: {{ $("Employee Intake2").item.json.manager }}

Onboarding Plan Summary:
Timeline: {{ $json.output.timeline }}
Buddy: {{ $json.output.assignedBuddy }}
Key Milestones: {{ $json.output.keyMilestones.join(", ") }}

Create an engaging welcome email that:
- Expresses genuine excitement about them joining
- Provides key first-day information
- Mentions their onboarding buddy
- Highlights important milestones
- Sets a positive, inclusive tone
- Includes practical next steps

Return subject and body as structured output.

**Business Purpose**

The welcome email generator:

Personalizes employee communications
Improves onboarding engagement
Reduces HR administrative workload
Creates a consistent onboarding experience

**Prompt Engineering Strategy**

**Structured Outputs**

The validation stage uses strict JSON schemas to ensure reliable workflow automation and decision-making.

**Personalization**

Employee-specific data including:

Name
Role
Department
Manager
Location
Start Date

is incorporated into onboarding plans and communications.

**Human-in-the-Loop Design**

Employees requiring additional review are automatically routed to HR intervention rather than being approved automatically.

**Auditability**

All AI outputs contribute to workflow decisions and are logged through audit nodes to support transparency and traceability.

**Reliability**

Schema-based validation reduces hallucinations and improves downstream automation reliability.

**AI Capabilities Demonstrated**

Data Validation
Classification
Risk Assessment
Workflow Decision Support
Personalized Planning
Content Generation
Communication Automation
Enterprise Workflow Orchestration
