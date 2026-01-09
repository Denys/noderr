# Tutorial 5: Advanced Prompts & Workflows

> **Master Specialized Noderr Workflows for Complex Operations**

---

## Overview

| | |
|---|---|
| **Difficulty** | Advanced |
| **Time Required** | 35-45 minutes |
| **Prerequisites** | Completed Tutorials 1-4 |

### Learning Objectives

By the end of this tutorial, you will:

- Know when to use specialized prompts vs. the main loop
- Execute security audits effectively
- Perform architecture health reviews
- Handle critical issues and emergency fixes
- Use refactoring workflows properly
- Plan major features with strategic prompts

---

## Introduction

The main development loop (LOOP_1A through LOOP_3) handles standard feature development. But software engineering involves more than building features:

- **Audits**: Is the system secure? Is the architecture healthy?
- **Emergency Fixes**: Something broke in production
- **Refactoring**: Component needs restructuring
- **Strategic Planning**: How do we approach a major feature?

Noderr provides specialized prompts for each scenario. This tutorial teaches you when and how to use them.

---

## Prompt Categories Overview

```
NODERR PROMPTS
│
├── MAIN LOOP (Standard Development)
│   ├── LOOP_1A: Propose Change Set
│   ├── LOOP_1B: Draft Specifications
│   ├── LOOP_2A: Implement Change Set
│   ├── LOOP_2B: Verify Implementation
│   └── LOOP_3: Finalize & Commit
│
├── SESSION MANAGEMENT
│   ├── Start_Work_Session
│   ├── Resume_Active_Loop
│   ├── Install_And_Reconcile
│   └── Post_Installation_Audit
│
├── AUDITS & REVIEWS
│   ├── Holistic_Integration_Audit
│   ├── Advanced_Security_Audit
│   ├── Architecture_Health_Review
│   └── Onboarding_Audit_Verification
│
├── SPECIALIZED OPERATIONS
│   ├── Execute_Micro_Fix
│   ├── Refactor_Node
│   ├── Handle_Critical_Issue
│   └── Spec_Verification_Checkpoint
│
└── STRATEGIC PLANNING
    ├── Feature_Idea_Breakdown
    ├── Pre_Flight_Feature_Analysis
    ├── Strategic_Blueprint_Designer
    ├── Expand_Completed_Project
    └── Major_Mid_Project_Feature_Addition
```

---

## Part 1: Audit & Review Prompts

### Holistic Integration Audit

**When to Use:**
- After completing multiple features
- Before a major release
- When experiencing mysterious bugs
- Periodically (every 2-4 weeks on active projects)

**What It Does:**
- Reviews all NodeIDs for consistency
- Checks architecture diagram matches reality
- Verifies specifications are up-to-date
- Identifies orphaned or disconnected components
- Flags potential integration issues

**Prompt:** `NDv1.9__Holistic_Integration_Audit.md`

**Example Output:**

```
## Holistic Integration Audit Report

### Architecture Consistency
- Diagram NodeIDs: 24
- Implemented NodeIDs: 26
- ISSUE: 2 implemented nodes not in diagram
  - SVC_CacheService (added but not documented)
  - API_HealthCheck (added but not documented)

### Specification Status
- Total specs: 22
- Up-to-date: 18
- STALE: 4 specs don't match implementation
  - SPEC_API_GetProducts: Missing pagination params
  - SPEC_SVC_OrderService: New method not documented
  - SPEC_UI_ProductCard: Props changed
  - SPEC_DB_Orders: New index not documented

### Dependency Analysis
- Circular dependency detected:
  SVC_UserService → SVC_OrderService → SVC_UserService

### Tracker Accuracy
- Tracker shows 20 VERIFIED
- Actual verified (with tests): 18
- ISSUE: 2 nodes marked verified but missing tests
  - API_UpdateUser
  - SVC_EmailService

### Recommendations
1. Add missing NodeIDs to architecture diagram
2. Update 4 stale specifications
3. Resolve circular dependency in services
4. Add tests for nodes marked as verified
```

**Your Action:**
Create tasks to address each finding, then use the main loop to fix them.

---

### Advanced Security Audit

**When to Use:**
- Before deploying to production
- After adding authentication/authorization
- When handling sensitive data
- After security incident
- Periodically (monthly for sensitive apps)

**What It Does:**
- Reviews authentication implementation
- Checks authorization patterns
- Identifies injection vulnerabilities
- Reviews data exposure risks
- Checks secrets management
- Validates input sanitization

**Prompt:** `NDv1.9__Advanced_Security_Audit.md`

**Example Output:**

```
## Security Audit Report

### Authentication
✓ JWT tokens properly signed
✓ Token expiration enforced
⚠ MEDIUM: No rate limiting on login endpoint
✗ HIGH: Refresh tokens don't invalidate on password change

### Authorization
✓ Role-based access control implemented
✓ Resource ownership validated
⚠ MEDIUM: Admin routes not logging access

### Injection Vulnerabilities
✓ SQL queries use parameterized statements
✓ NoSQL queries properly escaped
✗ HIGH: API_Search allows regex injection

### Data Exposure
✓ Passwords never returned in responses
⚠ MEDIUM: User emails exposed in public product reviews
✓ Sensitive fields excluded from logs

### Input Validation
✓ Request body validation on all endpoints
⚠ LOW: File upload doesn't validate MIME type
✓ XSS prevention on user-generated content

### Secrets Management
✓ No hardcoded secrets in codebase
✓ Environment variables for configuration
⚠ MEDIUM: .env.example contains real-looking values

### Summary
- HIGH severity: 2
- MEDIUM severity: 4
- LOW severity: 1

### Priority Fixes
1. [HIGH] Invalidate refresh tokens on password change
2. [HIGH] Sanitize regex in API_Search
3. [MEDIUM] Add rate limiting to login
4. [MEDIUM] Mask emails in public reviews
```

**Your Action:**
Address HIGH severity issues immediately using `Handle_Critical_Issue` or the main loop.

---

### Architecture Health Review

**When to Use:**
- Project feels "messy" or hard to work with
- Before major refactoring
- When onboarding complains about complexity
- When adding features becomes increasingly difficult

**What It Does:**
- Analyzes coupling between components
- Identifies complexity hotspots
- Reviews separation of concerns
- Checks for architectural anti-patterns
- Measures component cohesion

**Prompt:** `NDv1.9__Architecture_Health_Review.md`

**Example Output:**

```
## Architecture Health Review

### Coupling Analysis
- Average dependencies per node: 3.2 (healthy: <4)
- Most coupled node: SVC_OrderService (8 dependencies)
- Least coupled nodes: UI components (1-2 dependencies)

### Complexity Hotspots
1. SVC_OrderService: 8 deps, 15 methods, HIGH complexity
   - Recommendation: Split into OrderCreation, OrderFulfillment
2. API_Checkout: Handles 6 different operations
   - Recommendation: Split into focused endpoints

### Separation of Concerns
⚠ UI_ProductCard contains business logic (price calculation)
⚠ API_GetUser performs caching (should be service layer)
✓ Services properly abstract database operations

### Anti-Patterns Detected
- God Service: SVC_OrderService does too much
- Leaky Abstraction: DB queries in API layer (API_Search)
- Feature Envy: UI_Cart accesses order service directly

### Cohesion Score
- High cohesion: 16 nodes
- Medium cohesion: 6 nodes
- Low cohesion: 2 nodes (SVC_OrderService, SVC_UtilityService)

### Recommendations
1. Split SVC_OrderService into focused services
2. Move business logic from UI_ProductCard to SVC_PricingService
3. Create SVC_CacheService to centralize caching
4. Rename SVC_UtilityService to specific purpose or split
```

**Your Action:**
Use `Refactor_Node` for individual components or the main loop for larger restructuring.

---

## Part 2: Specialized Operations

### Execute Micro Fix

**When to Use:**
- Bug affects single NodeID
- Fix is small and isolated
- No architectural impact
- Quick turnaround needed

**What It Does:**
- Targets single component
- Skips full Change Set analysis
- Quick verification
- Minimal documentation overhead

**Prompt:** `NDv1.9__Execute_Micro_Fix.md`

**Example Interaction:**

```
You: The login button doesn't disable while submitting

AI: ## Micro Fix Analysis

Target: UI_LoginForm
Issue: Button remains enabled during API call
Impact: Single component, no dependencies affected

## Fix Applied
- Added isSubmitting state
- Disabled button when isSubmitting=true
- Reset state on success/error

## Verification
✓ Button disables on submit
✓ Button re-enables on error
✓ Existing tests still pass
✓ Added test for disabled state

## Commit
[fix-20250109-160000] Fix login button not disabling during submit

- UI_LoginForm: Add isSubmitting state to disable button
```

**When NOT to Use:**
- Fix requires changes to multiple NodeIDs
- You're unsure of the scope
- Changes affect interfaces or dependencies

---

### Refactor Node

**When to Use:**
- Component needs restructuring
- Extracting common functionality
- Changing component interface
- Splitting oversized component

**What It Does:**
- Analyzes current implementation
- Proposes refactoring approach
- Identifies affected dependents
- Maintains backward compatibility (if requested)
- Updates all affected specs

**Prompt:** `NDv1.9__Refactor_Node.md`

**Example Interaction:**

```
You: Refactor SVC_OrderService - it's doing too much

AI: ## Refactoring Analysis

### Current State: SVC_OrderService
- Methods: 15
- Dependencies: 8 downstream, 4 upstream
- Responsibilities:
  - Order creation
  - Order validation
  - Payment processing
  - Inventory management
  - Email notifications
  - Order history

### Proposed Refactoring

Split into focused services:

| New Service | Responsibilities | Methods |
|-------------|-----------------|---------|
| SVC_OrderCreation | Create, validate orders | 4 |
| SVC_OrderPayment | Payment processing | 3 |
| SVC_OrderFulfillment | Inventory, shipping | 4 |
| SVC_OrderNotification | Emails, alerts | 2 |
| SVC_OrderHistory | Query, reporting | 2 |

### Impact on Dependents
- API_CreateOrder: Update to use SVC_OrderCreation
- API_ProcessPayment: Update to use SVC_OrderPayment
- API_GetOrders: Update to use SVC_OrderHistory
- UI_OrderStatus: No change (uses API layer)

### Migration Strategy
1. Create new services with extracted code
2. Update SVC_OrderService to delegate to new services
3. Update API layer to use new services directly
4. Remove delegation layer from SVC_OrderService
5. Delete SVC_OrderService

Proceed with refactoring?
```

**Your Action:**
Approve the plan, then AI executes as a Change Set through the main loop.

---

### Handle Critical Issue

**When to Use:**
- Production is down or severely impacted
- Security vulnerability discovered
- Data corruption occurring
- Time-sensitive fix needed

**What It Does:**
- Rapid analysis focused on fix
- Minimal process overhead
- Quick implementation path
- Post-fix documentation

**Prompt:** `NDv1.9__Handle_Critical_Issue.md`

**Example Interaction:**

```
You: CRITICAL: Users can access other users' orders by changing the URL ID

AI: ## Critical Issue Response

### Issue Classification
- Type: Security - Broken Access Control
- Severity: CRITICAL
- Affected: API_GetOrder, API_UpdateOrder, API_DeleteOrder

### Root Cause
Order endpoints validate order exists but don't verify
ownership against authenticated user.

### Immediate Fix
```typescript
// Before
const order = await OrderService.findById(orderId);
if (!order) return res.status(404).send();

// After
const order = await OrderService.findById(orderId);
if (!order) return res.status(404).send();
if (order.userId !== req.user.id) return res.status(403).send();
```

### Applied To
✓ API_GetOrder
✓ API_UpdateOrder
✓ API_DeleteOrder
✓ API_GetOrderItems

### Verification
✓ Cannot access other user's order (returns 403)
✓ Can still access own orders
✓ Admin can still access all orders
✓ Added regression tests

### Commit
[fix-20250109-CRITICAL] Fix broken access control on order endpoints

SECURITY: Orders were accessible by any authenticated user.
Added ownership validation to all order endpoints.

### Post-Incident Tasks
1. [ ] Audit logs for unauthorized access attempts
2. [ ] Review other endpoints for similar issue
3. [ ] Add authorization tests to CI pipeline
4. [ ] Update security documentation
```

**After the Fix:**
- Create follow-up tasks for post-incident items
- Run security audit to check for similar issues
- Update relevant specifications

---

## Part 3: Strategic Planning Prompts

### Feature Idea Breakdown

**When to Use:**
- Evaluating a new feature idea
- Estimating complexity before committing
- Understanding what would be involved
- Product planning discussions

**What It Does:**
- Analyzes feature requirements
- Identifies affected components
- Estimates complexity
- Highlights risks and dependencies
- Suggests implementation approach

**Prompt:** `NDv1.9__Feature_Idea_Breakdown.md`

**Example Interaction:**

```
You: What would it take to add real-time notifications?

AI: ## Feature Breakdown: Real-Time Notifications

### Feature Analysis
Enable users to receive instant notifications for events
like new messages, order updates, and system alerts.

### Technical Requirements
- WebSocket connection management
- Event publishing system
- Notification storage and retrieval
- User preference management
- Mobile push integration

### Architecture Impact

#### New Components (7)
| NodeID | Type | Complexity |
|--------|------|------------|
| SVC_WebSocketManager | Service | High |
| SVC_EventPublisher | Service | Medium |
| SVC_NotificationService | Service | Medium |
| API_WebSocket | API | High |
| API_Notifications | API | Low |
| UI_NotificationCenter | UI | Medium |
| DB_Notifications | Database | Low |

#### Modified Components (4)
| NodeID | Changes |
|--------|---------|
| SVC_OrderService | Emit events on status change |
| SVC_MessageService | Emit events on new message |
| UI_Header | Add notification icon |
| STATE_AppContext | Add notification state |

### Risks
1. WebSocket scaling in production
2. Mobile push certification requirements
3. Event ordering and delivery guarantees
4. Notification fatigue for users

### Dependencies
- WebSocket library (socket.io or ws)
- Push notification service (Firebase/APNs)
- Message queue for event distribution

### Suggested Approach
1. Start with polling-based notifications (simpler)
2. Add WebSocket upgrade path
3. Layer in push notifications last

### Complexity Assessment
- Estimated Change Set: 11 NodeIDs
- Classification: MAJOR feature
- Recommended: Pre-Flight Analysis before implementation
```

**Your Action:**
Use this to make informed decisions about whether/when to implement.

---

### Pre-Flight Feature Analysis

**When to Use:**
- Before starting a major feature (10+ NodeIDs)
- Complex integrations
- Features touching multiple system areas
- When you want detailed planning before LOOP_1A

**What It Does:**
- Deep analysis of requirements
- Detailed component specifications outline
- Risk identification and mitigation
- Implementation sequence planning
- Test strategy recommendations

**Prompt:** `NDv1.9__Pre_Flight_Feature_Analysis.md`

**Example Output:**

```
## Pre-Flight Analysis: Real-Time Notifications

### Detailed Requirements
[Comprehensive requirements breakdown...]

### Implementation Phases

#### Phase 1: Foundation (3 NodeIDs)
- DB_Notifications: Schema and indexes
- SVC_NotificationService: Core CRUD operations
- API_Notifications: REST endpoints for history

#### Phase 2: Real-Time Infrastructure (3 NodeIDs)
- SVC_WebSocketManager: Connection handling
- API_WebSocket: WebSocket endpoint
- SVC_EventPublisher: Event distribution

#### Phase 3: Integration (4 NodeIDs)
- UI_NotificationCenter: Notification UI
- UI_Header: Notification icon integration
- SVC_OrderService: Event emission
- SVC_MessageService: Event emission

#### Phase 4: Polish (1 NodeID)
- STATE_AppContext: Notification state management

### Risk Mitigation
[Detailed risk analysis and mitigation strategies...]

### Test Strategy
[Comprehensive testing approach...]

### Ready for Implementation
Proceed to LOOP_1A with Phase 1 Change Set.
```

---

### Major Mid-Project Feature Addition

**When to Use:**
- Adding significant feature to in-progress project
- Feature affects existing incomplete work
- Need to integrate with ongoing development

**What It Does:**
- Analyzes current project state
- Identifies conflicts with in-progress work
- Proposes integration strategy
- Manages WorkGroupID coordination

**Prompt:** `NDv1.9__Major_Mid_Project_Feature_Addition.md`

---

## Practical Exercise

### Your Task

Your e-commerce project has been running for a few months. Perform a health check and address findings.

### Scenario

You have:
- 30 NodeIDs implemented
- Last audit was 6 weeks ago
- Users reporting occasional slow responses
- Team finds it hard to add new features

### Instructions

1. **Run Architecture Health Review**
   - Use `NDv1.9__Architecture_Health_Review.md`
   - Note complexity hotspots

2. **Run Holistic Integration Audit**
   - Use `NDv1.9__Holistic_Integration_Audit.md`
   - Note stale specs and inconsistencies

3. **Run Security Audit**
   - Use `NDv1.9__Advanced_Security_Audit.md`
   - Note any HIGH severity issues

4. **Prioritize Findings**
   - Critical security issues first
   - Then architecture problems
   - Then documentation updates

5. **Plan Remediation**
   - Use main loop for fixes
   - Use Refactor_Node for restructuring

### Checklist

- [ ] Architecture review completed
- [ ] Integration audit completed
- [ ] Security audit completed
- [ ] Findings prioritized
- [ ] Remediation tasks created

---

## Common Issues & Solutions

| Issue | Cause | Solution |
|-------|-------|----------|
| Audit too slow | Large codebase | Run focused audits on specific areas |
| Too many findings | Technical debt accumulated | Prioritize ruthlessly, fix over time |
| Refactoring breaks things | Missing dependencies | Use Refactor_Node to identify all impacts |
| Critical fix incomplete | Rushed implementation | Follow up with proper verification |
| Planning takes too long | Over-analysis | Time-box planning, start implementation |

---

## Key Takeaways

- **Use audits proactively** - Don't wait for problems
- **Match prompt to situation** - Micro-fix for small, main loop for features
- **Critical issues need speed** but still need verification
- **Refactoring requires planning** - Use the dedicated prompt
- **Strategic prompts save time** - Better to plan than rework

---

## Next Steps

Learn how to add Noderr to existing projects:

**[Tutorial 6: Retrofitting Existing Projects](06-retrofitting-projects.md)** - Bring Noderr methodology to legacy codebases.

---

## Quick Reference

### Prompt Selection Guide

| Situation | Prompt |
|-----------|--------|
| Standard feature | LOOP_1A → LOOP_3 |
| Quick bug fix | Execute_Micro_Fix |
| Security review | Advanced_Security_Audit |
| Architecture assessment | Architecture_Health_Review |
| System consistency check | Holistic_Integration_Audit |
| Production emergency | Handle_Critical_Issue |
| Restructure component | Refactor_Node |
| Evaluate new feature | Feature_Idea_Breakdown |
| Plan major feature | Pre_Flight_Feature_Analysis |
| Add feature mid-project | Major_Mid_Project_Feature_Addition |

### Audit Frequency Recommendations

| Audit Type | Frequency |
|------------|-----------|
| Security | Monthly or after auth changes |
| Architecture | Bi-weekly or when "feels messy" |
| Integration | After major features, before releases |
