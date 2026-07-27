# Okta Certified Administrator — Hands-On Configuration Exam Study Guide

Source: https://certification.okta.com/page/okta-administrator-hands-on-configuration-exam-study-guide

## Prerequisites
- An active, unexpired **Okta Professional Certification** (you already have this ✅)
- Completion of recommended training or self-study

## Exam Overview

| Part | Format | Time |
|---|---|---|
| Part I | 35 Discrete Option Multiple-Choice (DOMC) questions | 45 minutes |
| Part II | 4 Performance-Based, Hands-on Use Cases | 120 minutes |

- Total exam time: 165 minutes, no scheduled break, timer doesn't pause.
- Fee: USD $250 (USD $100 per retake)
- Proctored via ProctorU by Meazure Learning
- Part II: Okta Help Center access allowed; email access allowed **only** for verification codes.
- Exam is based on the **Okta Identity Engine** (not Classic Engine).

---

## Part I Subject Areas (DOMC Questions)

### 1. Identity and Access Management — 36%

**Active Directory Integration**
- Enable/manage delegated authentication with AD and LDAP using Okta agents
- Okta AD/LDAP agent architecture and best practices
- Okta agent service account permissions (agents + password reset)
- Okta/AD password policy requirements
- User activation options when using AD as a source
- Difference between AD groups and Okta groups

**Single Sign-On (SSO) Federation**
- Configure Okta as a Service Provider
- SAML assertion structure/understanding
- OIN app configuration
- Org2Org use cases

**Desktop SSO Deployment Federation**
- Deploying Agentless Desktop SSO

**Architecture**
- Configuring RADIUS applications
- High availability requirements for advanced agents (RADIUS, MFA, OPP)

---

### 2. User Lifecycle Management — 29%

**Profile Sourcing and Write-Back Concepts**
- HR as a source; benefits of groups/group rules with external sources
- When profile sourcing is used
- Value of writing data back to directories/apps from Okta
- Working with multiple profile sources
- Okta lifecycle management requirements + writing to applications
- Okta Workflows for advanced lifecycle management use cases

**Provisioning**
- Lifecycle management methods against apps (APIs, SCIM, SAML JIT, password sync, Org2Org)
- Typical flow: user registration/onboarding, updates, deprovisioning
- Full vs. incremental imports (users and groups)
- Group Push to provisioning-enabled third-party apps

---

### 3. Security — 20%

**Okta Security Policy and Enforcement Framework**
- Managing authenticators and profiles
- Configuring global session policies
- Authenticators, authentication methods, AAL (Authentication Assurance Level), app-level policies
- Device concepts: device context, device binding, registered vs. managed devices, EDR signals
- Adaptive MFA policies
- Authorization servers
- Network zones: dynamic zones, IP zones, blocklist zones

---

### 4. Monitoring and Troubleshooting — 9%

**Logging and Reporting**
- Understanding Okta logging (System Log)
- Filtering the Okta syslog for events
- Interpreting Okta log files

---

### 5. API Functions — 6%

**Token Management**
- Creating API tokens with correct permissions

**API Extended Functions**
- Importance of API rate limiting

---

## Part II Subject Areas (Hands-On Configuration Tasks)

### 1. User Management — 26%
- Import users from a CSV file
- Activate users
- Create a custom user type and assign users to it
- Add a custom attribute to a user type
- Assign users to a group by rule

### 2. Application Setup — 31%
- Add a SAML 2.0 app integration
- Map Okta attributes to application attributes
- Create and map a custom attribute

### 3. Administrator Roles — 20%
- Create a custom admin role
- Assign users to the admin role
- Activate users with correct admin role
- Create an API token

### 4. Security Enforcement — 23%
- Set up an authenticator
- Set up an MFA enrollment policy
- Modify the default global session policy
- Create an authentication policy for MFA
- Test the authentication policy

---

## Preparation Resources (by topic)

- **AD/LDAP**: Active Directory JIT provisioning, Password authenticator, delegated authentication, AD agent install/management, DMZ server ports, service account permissions
- **SSO/Federation**: Identity Providers, SAML app integrations, CASB config guide, OIN app config, Org2Org integration
- **Desktop SSO**: Active Directory Desktop Single Sign-on
- **RADIUS**: RADIUS server best practices, password sync to AD
- **Lifecycle Mgmt**: Manage profiles, group rules, Okta Expression Language, attribute-level sourcing, Group Push, Okta Workflows for Lifecycle Management
- **Provisioning**: Provision applications, Import users, Directory integrations, Group Linking
- **Security**: MFA, Okta Verify authenticator, Global session policies, Behavior Detection, Authentication policy rules, Device registration, Authorization Servers, API Access Management, Network Zones, dynamic zones
- **Monitoring**: System Log, Useful System Log Queries, LDAP integration troubleshooting, AD agent variable definitions, MFA for Windows Credential Provider troubleshooting
- **API**: API token management, Burst rate limits, Rate limits overview
- **Part II tasks**: CSV import, Activate user accounts, Custom user types, Create group rules, SAML app integrations via AIW, Profile Editor attribute mapping, Custom admin roles, Set up administrators

## Other Resources
- Okta Help Center (knowledge library, articles, videos)
- Okta Content Library (white papers)
- Okta Community (Q&A, discussions)
- Standard & Premier Practice Exams (paid) — simulate DOMC + hands-on format
- Okta Administrator Series Learning Plan (learning.okta.com)

## Important Notes
- Exam dumps are **prohibited** — using them can invalidate scores, revoke certification, or result in testing bans.
- Only approved resources: this study guide, official practice exams, Okta-authorized training.
