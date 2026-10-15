# Sample Test Cases

These are proposed test cases, not proof that tests have already been run. Record actual outcomes after testing your implementation.

## A. Occupancy and alerts
Illustrative thresholds: Green <60%; Yellow 60% to <85%; Red >=85%.

| ID | Input | Expected result |
|---|---|---|
| OCC-01 | 0 people / capacity 100 | 0%, green |
| OCC-02 | 59 / 100 | 59%, green |
| OCC-03 | 60 / 100 | 60%, yellow |
| OCC-04 | 84 / 100 | 84%, yellow |
| OCC-05 | 85 / 100 | 85%, red |
| OCC-06 | 100 / 100 | 100%, red |
| OCC-07 | Capacity 0 | Validation error |
| OCC-08 | Negative capacity | Validation error |
| OCC-09 | Negative people count | Validation error |
| OCC-10 | People count above capacity | Show over-capacity and red; do not silently clamp |

## B. Incident management
| ID | Action | Expected result |
|---|---|---|
| INC-01 | Submit valid incident | Unique ID and record created |
| INC-02 | Omit required fields | Validation error |
| INC-03 | Use unknown zone ID | Clear validation error |
| INC-04 | Change open to assigned | Updated status is saved and displayed |
| INC-05 | Load sample incidents | Clearly labelled simulated |
| INC-06 | Unsupported incident type | Validation error or documented handling |

## C. Route suggestions
| ID | Setup | Expected result |
|---|---|---|
| ROUTE-01 | Use sample route graph | Route A → B → C |
| ROUTE-02 | Mark B-C blocked | Suggested route does not use B-C |
| ROUTE-03 | No available path | Report no route; do not invent one |
| ROUTE-04 | Unknown start/destination | Validation error |
| ROUTE-05 | Missing/stale route data | Warning and human verification |

## D. UI and resilience
| ID | Check | Expected result |
|---|---|---|
| UI-01 | Load valid sample map points | Points appear in correct categories |
| UI-02 | View risk zones | Status has color and readable text |
| UI-03 | Map service unavailable | Clear error/fallback |
| UI-04 | View demo records | Simulated label visible |
| UI-05 | View incidents | Status and zone are readable |
| RES-01 | Backend unavailable | Clear service-unavailable message |
| RES-02 | Crowd data stale | Last update and stale warning shown |

## E. Security
| ID | Check | Expected result |
|---|---|---|
| SEC-01 | Check repository for secrets | No real keys/tokens/passwords committed |
| SEC-02 | Submit malformed API payload | Safely rejected |

## Execution record
Fill this table only after actually running the tests.

| Date | Tester | Environment | Passed | Failed | Notes |
|---|---|---|---|---|---|
| | | | | | |

**Safety note:** These tests cover prototype behavior only and do not certify the system for operational crowd control.
