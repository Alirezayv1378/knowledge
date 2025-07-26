# Notes from The Missing README

- **Full Title:** The Missing README: A Guide for the New Software Engineers.
- **Authors:** Chris Riccomini & Dmitry Ryaboy

## Chapter 3: Working with code

### Technical Debt

- When you addressing technical debt, do not base your appeal on a value judgement ("this code is old and ugly"). Focus on the cost of the debt and the benefits of fixing it.

### Changing Code

- When refactoring an existing codebase, use this approach:
  1. Identify change points.
  2. Find test points.
  3. Break dependencies (changing code structure so that it is easier to test).
  4. Write tests (add tests to validate existing behavior).
  5. Make changes and refactor.
