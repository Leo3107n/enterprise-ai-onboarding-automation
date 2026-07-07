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

Create a comprehensive onboarding plan for:

Employee: {{ $("Employee Intake2").item.json.firstName }} {{ $("Employee Intake2").item.json.lastName }}
Role: {{ $("Employee Intake2").item.json.role }}
Department: {{ $("Employee Intake2").item.json.department }}
Start Date: {{ $("Employee Intake2").item.json.startDate }}
Manager: {{ $("Employee Intake2").item.json.manager }}
Location: {{ $("Employee Intake2").item.json.location }}

Requirements:
- Use a 2-4 week onboarding timeline.
- Include at least 2 onboarding phases.
- Include at least 2 key milestones.
- Assign an onboarding buddy.
- Include role-specific training modules.
- Include equipment and access requirements.
- Tailor the plan to the employee's role and department.

Return ONLY valid JSON matching this structure:

{
  "planId": "string",
  "employeeName": "string",
  "department": "string",
  "timeline": "string",
  "phases": [
    {
      "phase": "string",
      "tasks": ["string"]
    }
  ],
  "keyMilestones": ["string"],
  "assignedBuddy": "string",
  "trainingModules": ["string"],
  "equipmentNeeded": ["string"]
}

Do not include markdown.
Do not include explanations.
Do not include any text outside the JSON.


**Generate Onboarding Plan**

Generate a role-specific onboarding plan tailored to the employee's department, manager, location, and start date.

**Prompt**

Create a comprehensive onboarding plan for:

Employee: {{ $("Employee Intake2").item.json.firstName }} {{ $("Employee Intake2").item.json.lastName }}
Role: {{ $("Employee Intake2").item.json.role }}
Department: {{ $("Employee Intake2").item.json.department }}
Start Date: {{ $("Employee Intake2").item.json.startDate }}
Manager: {{ $("Employee Intake2").item.json.manager }}
Location: {{ $("Employee Intake2").item.json.location }}

Requirements:
- Use a 2-4 week onboarding timeline.
- Include at least 2 onboarding phases.
- Include at least 2 key milestones.
- Assign an onboarding buddy.
- Include role-specific training modules.
- Include equipment and access requirements.
- Tailor the plan to the employee's role and department.

Return ONLY valid JSON matching this structure:

{
  "planId": "string",
  "employeeName": "string",
  "department": "string",
  "timeline": "string",
  "phases": [
    {
      "phase": "string",
      "tasks": ["string"]
    }
  ],
  "keyMilestones": ["string"],
  "assignedBuddy": "string",
  "trainingModules": ["string"],
  "equipmentNeeded": ["string"]
}

Do not include markdown.
Do not include explanations.
Do not include any text outside the JSON.


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

- Expresses excitement about the employee joining the company.
- Provides first-day expectations and guidance.
- Introduces the onboarding buddy.
- Highlights key onboarding milestones.
- Creates a welcoming and inclusive tone.
- Includes practical next steps.

Return ONLY valid JSON in the following format:

{
  "subject": "string",
  "body": "string"
}

Do not include markdown.
Do not include explanations.
Do not include any text outside the JSON.

**AI Usage Summary**

**AI Validation Agent**

Employee data validation
Compliance checks
Missing information detection
Risk assessment
Approval/review decision making

**Onboarding Plan Generator**

Personalized onboarding planning
Training recommendations
Timeline creation
Resource allocation
Department-specific onboarding tasks

**Welcome Email Generator**

Personalized communication
Professional email drafting
Onboarding milestone communication
Employee engagement and experience enhancement
