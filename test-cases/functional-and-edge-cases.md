Functional, Regression & Edge-Case Test Suite
Application Under Test: Web Learning Platform (learnaitutor.com)
Scope: Diagnostic Recommendations, Adaptive Difficulty, Mastery Preservation & Session State

TC-001 | Diagnostic Flow | Verify recommended lessons exist and are active
Type: Positive
Preconditions: Student completes diagnostic assessment
Steps:
1. Complete diagnostic test.
2. View recommended lessons list.
3. Click each recommended lesson.
Expected Result: Only approved, live, and accessible lessons are recommended; no missing or archived topics appear.

TC-002 | Prerequisite Logic | Block advanced topic when prerequisite is incomplete
Type: Negative
Preconditions: Student is enrolled in Class 7 with incomplete Class 6 foundation topic
Steps:
1. Navigate to a Class 7 topic requiring a prerequisite.
2. Attempt to start assessment directly.
Expected Result: System enforces relevant prerequisite validation without blocking unrelated topics.

TC-003 | Adaptive Difficulty | Maintain difficulty state across consecutive questions
Type: Functional
Preconditions: Active practice session at Medium difficulty
Steps:
1. Answer 2 consecutive Medium questions correctly.
2. Observe next question difficulty.
3. Refresh page mid-session.
Expected Result: Difficulty progresses appropriately and does not unnecessarily reset back to Easy after refresh or next attempt.

TC-004 | Mastery History | Preserve prior mastery when a later practice score is lower
Type: Edge Case
Preconditions: Student previously achieved Mastered status (90%) on a topic
Steps:
1. Retake practice quiz on the same topic.
2. Submit with a lower score (50%).
3. Check topic mastery and score history.
Expected Result: Best score (90%) and prior mastery history remain preserved; latest score (50%) is tracked separately without wiping historical records.

TC-005 | Dashboard Metrics | Exclude incomplete/abandoned quizzes from completed count
Type: Boundary
Preconditions: Student has 0 completed quizzes
Steps:
1. Start a quiz.
2. Answer 1 question and close browser tab.
3. Log back in and check dashboard stats.
Expected Result: Quiz is tracked as started/in-progress, not counted as a completed quiz on the dashboard.

TC-006 | Data Isolation | Prevent horizontal access to another student's records
Type: Security / Access
Preconditions: Two valid student accounts (Student A & Student B)
Steps:
1. Log in as Student A.
2. Attempt to request Student B's progress/memory ID via URL or API.
Expected Result: Access is denied (403 Forbidden / 404 Not Found); Student A cannot view Student B's learning history.
