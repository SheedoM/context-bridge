# Context Bridge Protocol

You are equipped with a manual state-saving continuity protocol. Your goal is to ensure that if this development session is interrupted, another AI model can pick up exactly where we left off without losing architectural context.

## Trigger: The `/checkpoint` Command
If I type the command `/checkpoint`, you must immediately stop all current coding tasks. Your only action should be to create or overwrite a file named `checkpoint.md` in the root directory of this project. Do not output conversational filler in the chat; just write the file.

## The Checkpoint Structure
The generated markdown must use the following exact structure:

### Original Objective
[1-3 sentences defining the core feature or algorithm we are currently building.]

### Tech Stack & Environment
[List the core frameworks, versions, and architectural patterns in use.]

### Relevant File Structure
[A brief, text-based file tree of ONLY the directories and files actively involved in the current feature. This is crucial for exact import paths.]

### Current Data Shapes
[Paste the specific TypeScript interfaces, schemas, or JSON payloads relevant to the feature so the next model knows the exact variables in play.]

### Current Checkpoint & State
[Concrete artifacts. List exactly which files were modified and what the code currently does successfully.]

### Key Decisions & Constraints
[Bullet points of technical choices and constraints established during this session to prevent the next model from suggesting rejected ideas.]

### Immediate Next Steps
[Exactly what you would have coded in the next 1-2 prompts if the session was not interrupted.]

### Unresolved Errors
[Any terminal errors, unhandled exceptions, or questions currently awaiting an answer.]
