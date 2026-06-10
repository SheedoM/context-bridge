# Checkpoint: Credit-Hour Prerequisite Validation

### Original Objective
Implementing a backend validator service and frontend UI module to handle credit-hour prerequisite validation for a university graduation planner. The system must verify that a student has completed the required minimum credit hours and specific course dependencies before allowed to add a designated course to their active graduation plan.

### Tech Stack & Environment
* **Frontend:** Next.js 14 (App Router), React 18, TypeScript, Tailwind CSS, shadcn/ui.
* **Backend:** NestJS 10, TypeScript, Prisma ORM, PostgreSQL.
* **Common:** Class-Validator for DTO validation.

### Relevant File Structure
```text
graduation-planner/
├── apps/
│   ├── web/                     # Next.js frontend
│   │   └── app/
│   │       └── planner/
│   │           ├── components/
│   │           │   └── graduation-planner-board.tsx
│   │           └── services/
│   │               └── planner-api.ts
│   └── api/                     # NestJS backend
│       └── src/
│           ├── courses/
│           │   ├── courses.controller.ts
│           │   ├── courses.service.ts
│           │   └── dto/
│           │       └── validate-prerequisites.dto.ts
│           └── graduation/
│               ├── graduation.module.ts
│               ├── graduation.service.ts
│               └── graduation.validator.ts
```

### Current Data Shapes
```typescript
// apps/api/src/courses/dto/validate-prerequisites.dto.ts
export class ValidatePrerequisitesDto {
  studentId: string;
  courseId: string;
  plannedSemester: string; // e.g., "Fall 2026"
}

// NextJS/NestJS shared types: interfaces.ts
export interface Course {
  id: string;
  code: string; // e.g., "CS401"
  name: string;
  credits: number;
  prerequisites: PrerequisiteGroup[];
}

export interface PrerequisiteGroup {
  id: string;
  type: 'AND' | 'OR';
  courses: string[]; // List of Course IDs
  minCumulativeCredits?: number; // Minimum general credits required before taking this course
}

export interface StudentCompletedCourse {
  courseId: string;
  semesterCompleted: string;
  grade: string; // e.g., 'A', 'B-', 'P' (Pass)
  creditsEarned: number;
}

export interface PrerequisiteValidationResult {
  isEligible: boolean;
  reason?: string;
  missingCourses: string[];
  missingCredits: number;
}
```

### Current Checkpoint & State
* **Prerequisites Validator:** Validation logic implemented successfully in `graduation.validator.ts`. It correctly evaluates both course-specific prerequisites (AND/OR constraints) and general cumulative credit-hour thresholds.
* **Database & ORM:** Prisma schema updated with relations for prerequisites; local PostgreSQL migration run successfully.
* **Planner Dashboard:** UI layout in `graduation-planner-board.tsx` displays semester blocks and course cards, but drag-and-drop actions do not trigger validations.

### Key Decisions & Constraints
* **Semesters Evaluation:** Prerequisite status is calculated by looking at semesters *prior* to the planned semester. Courses scheduled in the same semester as the target course cannot satisfy its prerequisites.
* **Successful Completion:** Any grade other than 'F' (Fail), 'W' (Withdrawn), or 'I' (Incomplete) counts as successful completion.
* **Credit Summing:** Validation of `minCumulativeCredits` sums only the `creditsEarned` of successfully completed courses, ignoring courses currently in progress or planned.

### Immediate Next Steps
1. Connect drag-and-drop trigger in `graduation-planner-board.tsx` to fetch validation status from `planner-api.ts` before updating the planner state.
2. Render alert modal in the frontend dashboard showing a list of unsatisfied prerequisites when `isEligible` is false.
3. Write unit tests in `graduation.validator.spec.ts` to test complex nested AND/OR prerequisite structures.

### Unresolved Errors
* **Frontend Type Error:** In `graduation-planner-board.tsx`, type signature of the fetched planner state differs slightly from backend `Course` type definition due to missing mapper for nested `PrerequisiteGroup`.
