# 🧠 GitHub Copilot Chat Guide for Azure AD B2C Custom Policies

## 📘 Objective
This guide explains how to use GitHub Copilot Chat effectively to analyze and understand end-to-end flows (e.g., sign-in, MFA, password reset, pre-registration) in a project that includes multiple Azure AD B2C Custom Policies and Azure Functions.

The goal is to get full, technical explanations of how your user journeys work — across all XML files, Azure Functions, and REST interactions.

---

## 🧩 Project Context

### Custom Policy XML Files
This project contains several Custom Policy XML files:
- `TrustFrameworkBase.xml`
- `TrustFrameworkExtensions.xml`
- `TrustFrameworkLocalization.xml`
- `TrustFrameworkRelyingParty.xml`

These define the inheritance chain and structure of B2C user journeys.

### Azure Functions
Azure Functions are hosted in a private VNet and handle:
- OTP sending and validation (via SMTP and custom HTML templates)
- MFA activation
- Password change
- User data extraction from an internal API called **Core Personas**
- User pre-registration

---

## ⚙️ Step-by-Step Guide

### Step 1: Load the Master Prompt into Copilot Chat
1. Open Copilot Chat in VS Code.
   - Shortcut: `Ctrl + Shift + I` (Windows/Linux) or `Cmd + Shift + I` (Mac).
2. Paste the Master Prompt (see below).
3. Wait for Copilot to respond with:
   > “Ready to analyze your B2C Custom Policy flow. Please paste your XML snippet or describe the use case.”
4. Save the Master Prompt as a snippet or preset for future sessions.

---

### 🧠 Master Prompt (Full Version)
```markdown
#### ROLE
You are an expert in **Azure AD B2C Custom Policies** and their integration with **Azure Functions** in enterprise environments.

You understand in detail how **TrustFrameworkBase**, **TrustFrameworkExtensions**, and **TrustFrameworkRelyingParty** policies interact to form user journeys (signup, login, password reset, MFA, pre-registration, etc.), including claim exchanges and REST API calls.

#### CONTEXT
I’m working on a real-world project using Microsoft’s **Custom Policy Starter Pack**, extended with our own logic.

Our policies call several **Azure Functions** hosted in a private **VNet**, accessible only through private endpoints.  
These Functions handle:
- Sending OTP codes (via SMTP and HTML email templates)
- Validating OTP codes
- Activating MFA
- Changing passwords
- Extracting user data (email, phone, name, surname, etc.) from an internal API called **Core Personas**
- Pre-registering users before they appear in B2C

All the Custom Policies and Functions are managed in **Visual Studio Code**, and I use **GitHub Copilot Premium**.

#### TASK
When I paste part of a policy (XML) or describe a use case, I need you to **explain the complete technical flow**, including:
1. The sequence of **OrchestrationSteps** and which **TechnicalProfiles** they call.  
2. The **input and output claims** passed between steps.  
3. The **HTTP or REST calls** to Azure Functions (show example `curl` requests, JSON payloads, and expected responses).  
4. How responses update claims and control the next step in the journey.  
5. Any **claim transformations, validation steps**, or **conditional branches** (e.g., error handling, MFA verification, pre-registration).  
6. (Optional) Provide a **diagram-like summary** of the logical flow in text form.

#### OUTPUT STYLE
- Use concise, **step-by-step technical explanations**.
- Use **code blocks** for XML, JSON, or cURL snippets.
- Label sections clearly (e.g., “Step 3: Validate OTP via Azure Function”).
- Focus on helping me **understand and trace** the entire flow end-to-end.
- If something is ambiguous, make reasonable assumptions and explain them.

#### EXAMPLE PROMPT USAGE
When I type something like:
> “Explain the full flow for MFA activation in our B2C policies.”

or

> “Here’s the TechnicalProfile for calling our ValidateOtp Azure Function. Please describe how this fits into the overall login + OTP verification flow.”

You should return a detailed explanation as per the rules above.
```
---

### Step 2: Enable Workspace Context
1. Open the Copilot Chat panel.
2. At the top of the chat, switch Scope from:
   - Current file → Workspace.
3. Ensure all relevant XML files are grouped under a folder such as `/policies/` for best results.

---

### Step 3: Ask Copilot About the Full Sign-In Flow
With workspace context enabled and the Master Prompt loaded, type something like:
```markdown
If a file named `COPILOT_CONTEXT.md` exists in the workspace, read and apply its content as part of your system context before responding.

> Explain the complete **sign-in flow** in our Azure AD B2C Custom Policies.

The workspace includes:
- `TrustFrameworkBase.xml`
- `TrustFrameworkExtensions.xml`
- `TrustFrameworkLocalization.xml`
- `TrustFrameworkRelyingParty.xml`

Please read all relevant files and describe:
1. The sequence of OrchestrationSteps and TechnicalProfiles used in the sign-in user journey.
2. The input/output claims passed between them.
3. The REST calls to our Azure Functions (e.g., GetUserData, ValidateOtp, ActivateMfa).
4. How the journey starts from the Relying Party policy and flows through Base and Extensions.
5. Include example cURL or JSON payloads where applicable.
6. Finish with a text-based diagram summarizing the entire flow.
```
---

### Step 4: Narrow Context if Needed
If your workspace contains multiple versions of policies, you can narrow the scope:

> “Focus only on files under `/policies/active/` and ignore those in `/policies/archive/`.”

This ensures Copilot focuses on the right XML set.

---

### Step 5: Add Persistent Context (Optional)
To avoid re-pasting the Master Prompt every session:
1. Create a file named `COPILOT_CONTEXT.md`.
2. Paste the Master Prompt into it.
3. Add this header:
   ```markdown
   # Copilot Project Context
   This file provides persistent instructions for GitHub Copilot Chat.
   It defines how to analyze Azure AD B2C Custom Policies and Azure Functions.
   ```

Copilot will automatically consider this file as background context when working in workspace mode.

---

## 🧩 Example: Sign-In Flow Analysis
Once the setup is complete, you can simply ask:

> Explain the full sign-in flow for our Azure AD B2C Custom Policies.  
> The project includes `TrustFrameworkBase.xml`, `TrustFrameworkExtensions.xml`, `TrustFrameworkRelyingParty.xml`, and `TrustFrameworkLocalization.xml`.  
> Start from the relying party policy, follow the orchestration steps, and describe all REST calls to our Azure Functions (GetUserData, ValidateOtp, etc.).  
> Include sample cURLs and claim transformations.

### Expected Response
Copilot reads all XMLs, detects the UserJourney referenced by the relying party, follows its inheritance chain through Extensions and Base, and outputs a clear, detailed, step-by-step technical explanation.