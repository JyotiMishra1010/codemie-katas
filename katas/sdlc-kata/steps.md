# End-to-End AI SDLC Demo

Build a complete AI-native end to end SDLC using CodeMie Assistants that collaborate across different project phases. In this kata, you will create and configure multiple AI assistants that simulate a real end-to-end delivery pipeline where information flows seamlessly between Business Analysis, Architecture, Quality Assurance, Development, and Code Review stages.

## Overview / Goal

![AI Native Delivery: End-to-End flow](https://codemie-ai.github.io/codemie-katas/katas/sdlc-kata/images/agent_understanding.png)

Here is the video link to understand more about the flow.

(https://videoportal.epam.com/video/e7n3lDna)

The diagram above illustrates how CodeMie Agents (such as **CLARA** for Business Analysis, **ARCHIE** for Solution Architecture,  **TESSA** for QA,and **CR** for codereview) collaborate in a real end-to-end AI-native delivery flow. Each agent:    

* Reads inputs from real systems (call transcripts, Jira, Git).
* Uses human feedback checkpoints at key decisions.
* Passes context forward to the next agent — eliminating manual re-entry between phases.

In this kata, you will replicate the pattern by using one Assistant per phase, defining clear inputs/outputs for each, and orchestrating a manual handoff that mirrors this flow.

---

## Prerequisites

1. **Log in to CodeMie**

   * Open your browser and navigate to (https://codemie.lab.epam.com)
   * Sign in with your EPAM credentials (use SIGN IN WITH EPAM SSO option)
   * After login, verify you see the main CodeMie dashboard

**Note**: If you are in a region that requires EPAM VPN, ensure your VPN is connected

---

## Tools / Access needed

* CodeMie: ability to create and edit Assistants (Assistants only; no workflows required in this kata).

---

### Integrations Setup Guide

1. Here we are integrating Jira so the assistant can directly access project tickets. This enables it to view, update, and work on issues seamlessly throughout the workflow.

![CodeMie workspace selection](https://codemie-ai.github.io/codemie-katas/katas/sdlc-kata/images/codemie_integration.png)

- Go to Integrations
- Click on Create
- Select type: Jira
- Alias jira_intg
- Fill in required details:
- Link :-https://jiraeu.epam.com
- Token

```
To create a token for Jira:

1. Go to the Jira site: (https://jirau.epam.com)
2. Navigate to your profile.
3. Open API Authentication.
4. Click on Create New Token.
5. Select read & write Generate and copy the token for further use.
```

![CodeMie workspace selection](https://codemie-ai.github.io/codemie-katas/katas/sdlc-kata/images/jira_token.png)

- Click Test (top-right) to validate
- Click Save

---

2. Here we are integrating the Git repository so the assistant can directly access the codebase. This enables it to create new branches, manage commits, and perform all necessary Git operations seamlessly.

**Git Integration ("Demo Purpose")**
- Go to Integrations
- Click on Create
- Select type: Git
- Alias Demo_purpose
- Fill in required details:
- Link (repo link)
- Token name & Token

```
### Generate Personal Access Token in Gitepam (https://git.epam.com)

1. Open [GitBud EPAM](https://git.epam.com/) and sign in to your account.
2. Click on your profile icon (top-left corner).
3. Select **Preferences**.
4. In the left sidebar, click **Access Tokens**.
5. Under **Personal Access Tokens**, click **Add new token** / **Create token**.
6. Enter a token name: `kt`
7. Set an **Expiration date** as required.
8. Under permissions/scopes, select **all permissions**.
9. Click **Create personal access token**.
10. Copy and store the token securely (it will be shown only once).
```
- Click Test (top-right) to validate
- Click Save

---

# To use the assistant 

To use the assistant, you need to create all the required integrations. You can use the links provided below to start using the assistant.

(https://codemie-ai.github.io/codemie-katas/katas/sdlc-kata/images/Assitant_on_marketplace-1.png)



### Clara:- https://codemie.lab.epam.com/assistants/ai_sdlc_kata/clara_sjzgihxdslaxpjv
### Configure the Clara Assistant with Your Jira Integration

1. Open the provided link. It will take you to the **Clara Assistant Configuration** page.

2. Scroll down to the bottom of the page.

3. Locate the **Generic Jira** section.

4. From the dropdown, select the Jira integration you created earlier (named **`jira_intg`**).

5. Click **Save** to apply the configuration.


### Tessa:- https://codemie.lab.epam.com/assistants/ai_sdlc_kata/tessa_vmwzqyauoioyvnd


1. Open the provided link. It will take you to the **Tessa Assistant Configuration** page.

2. Scroll down to the bottom of the page.

3. Locate the **Generic Jira** section.

4. From the dropdown, select the Jira integration you created earlier (named **`jira_intg`**).

5. Click **Save** to apply the configuration.


### Archie:- https://codemie.lab.epam.com/assistants/ai_sdlc_kata/archie

### Configure the Archie Assistant

1. Open the provided link. It will take you to the **Archie Assistant Configuration** page.

2. Scroll down to the bottom of the page.

3. In the **GitLab** section, select the `Demo_Purpose` that you created earlier for this purpose.

4. Locate the **Generic Jira** section and select the Jira integration you created earlier, named **`jira_intg`**.

5. Click **Save** to apply the configuration changes.


### CR:- https://codemie.lab.epam.com/assistants/ai_sdlc_kata/cr

### Configure the CR Assistant

1. Open the provided link. It will take you to the **CR Assistant Configuration** page.

2. Scroll down to the bottom of the page.

3. In the **GitLab** section, select the `Demo_Purpose` project that you created earlier.

4. In the **Git** section, select the same `Demo_Purpose` that you created earlier.

5. Click **Save** to apply the configuration changes.

---

### Flow Explanation
* **CLARA (BA)** → Converts raw inputs into structured user stories in Jira
* **TESSA (QA)** → Prepares test cases before development begins
* **ARCHIE (SA)** → Translates stories into architecture + implementation plan (plan.md)
* **Development Tools**→ Implements feature using plan.md (Copilot / Claude / etc.)
* **CR (Code Review)** → Ensures quality, security, and best practices

---

# End-to-End Validation Flow 

For example, here using transcript.pdf file.

**transcript.pdf file content**: This transcript PDF contains a summarized discussion of a project meeting focused on integrating an FTP/SFTP data source into CodeMie. It covers technical requirements, UI design considerations, security measures, implementation timelines, resource planning, and action items for delivering the feature and demo.

###  CLARA (Business Analysis)

**Objective:** Convert raw inputs (chat + transcript) into structured, testable user stories.

**Input Prompt:**

> "I've attached a transcript of our recent convo with CodeMie team about new feature, can you analyze it and extract a user story?"

attach transcript pdf.

**Expected Output:**

* Well-defined **User Story**
* **Acceptance Criteria (5–8 points)**
* **Assumptions & Affected Areas**
* **Clarification questions** (if required)
* Jira ticket creation (**after approval**)

**Validation Check:**

* Story is clear, structured, and testable
* Acceptance criteria are unambiguous
* Transcript insights are properly captured

---

### 2 ARCHIE (Solution Architecture)

**Trigger:** After successful Jira ticket creation

**Input Prompt:**

> "lets create the implementation plan for this"

**Expected Output:**

* **Research Summary** (codebase + documentation)
* Identified **existing patterns/components**
* **plan.md** (created in repo, not shown in chat)
* **Feature branch creation**
* **Pull Request (PR) created**
* Jira updated with PR link

**Validation Check:**

* Plan aligns with CodeMie architecture
* Proper branch naming convention followed
* PR created successfully

---

### 3 TESSA (QA)

**Input Prompt:**

> "Please create the test cases and add in Jira stories"

**Expected Output:**

* **10–12 structured test cases**
* Covers:

  * Functional scenarios
  * Edge cases
  * Negative scenarios
* Includes:

  * Steps
  * Expected results
* Properly mapped to acceptance criteria
* Added to Jira story

**Validation Check:**

* All acceptance criteria are covered
* Includes boundary & negative cases
* Ready to validate development output

---

### 4 DEVELOPMENT (External Tools)

**Objective:** Implement feature using plan generated by ARCHIE.

**Tools You Can Use:**

* GitHub Copilot
* Claude
* Any other preferred development tool

**Steps:**

1. Take the **plan.md** generated by ARCHIE
2. Provide it to your coding assistant (e.g., Copilot)
3. Instruct it to implement the feature based on the plan
4. Complete development in your repository
5. Ensure:

   * Feature branch is used
   * Code follows best practices
   * PR/MR is created with Jira reference

**Validation Check:**

* Code aligns with plan.md
* Proper Git workflow followed
* PR created successfully

---

## 5 CR (Code Review)

**Input Prompt:**

> "Review PR: [PR Number]"

**Expected Output:**

* **Single consolidated review comment**
* Covers:

  * Code quality
  * Security
  * Maintainability
  * Best practices
* Comment posted in GitLab
* Marked as **CreatedByAgent**

**Validation Check:**

* Only one comment created
* Covers both code + documentation
* Clear approval or change suggestions


![CodeMie workspace selection](https://codemie-ai.github.io/codemie-katas/katas/sdlc-kata/images/agent_understanding.png)


For more clarification: (https://codemie.lab.epam.com/#/share/conversations/GdNuDFVu2W45)

---

### Integration Validation

* **Jira** → Stories, updates, linking
* **Git** → Branches, commits, PRs

### Key Outcome

* No manual copying of data between phases
* Each assistant uses previous output directly
* Fully connected AI-native SDLC workflow

---

# Troubleshooting / Common Issues

### 1. Jira Issues

**Problem:** Ticket not created/updated

**Fix:**

* Check token validity
* Verify project key (**EPMCDMETST**)
* Ensure required permissions are granted
---

## Contact

For any queries regarding this kata , feel free to ping:

- Poonam Nawandar
- Imtiyaz Alamshah
- Jyoti Mishra
