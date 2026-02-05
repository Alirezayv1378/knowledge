# Git Commit Message Guidelines From [Chris Beams](https://chris.beams.io/posts/git-commit/)

## The Seven Rules of a Great Git Commit Message
Below are the seven rules for crafting excellent Git commit messages, along with explanations and examples:

### 1. Separate subject from body with a blank line
   Always include a blank line between the subject line and the body to ensure tools like `git log`, `shortlog`, and `rebase` parse the message correctly.  
   ```
   Add user authentication module

   Implement login and signup functionality using JWT.  
   Update user model to include password hashing.  
   Add tests for authentication endpoints.  
   ```

### 2. Limit the subject line to 50 characters
   Keep the subject line short (ideally 50 characters or less) for readability in Git logs. If you struggle to summarize, you may be committing too many changes at once.  
   ```
   Fix bug in user profile update endpoint
   ```

### 3. Capitalize the subject line  
   Start the subject line with a capital letter for consistency.  
   ```
   Update README with project setup instructions
   ```  
   Instead of:  
   ```
   update README with project setup instructions
   ```

### 4. Do not end the subject line with a period  
   Avoid trailing punctuation in the subject line to save space and maintain a clean format.  
   ```
   Refactor database connection logic
   ```  
   Instead of:  
   ```
   Refactor database connection logic.
   ```

### 5. Use the imperative mood in the subject line
   Write the subject as a command or instruction, so it completes the sentence: "If applied, this commit will [your subject line]." This aligns with Git’s own commit messages.  
   ```
   Remove deprecated API endpoints
   ```  
   Completes: "If applied, this commit will remove deprecated API endpoints."

### 6. Wrap the body at 72 characters
   Keep lines in the body to 72 characters or less for readability in terminals and Git tools.  
   ```
   Improve error handling in payment processing

   Add try-catch blocks to handle payment gateway errors gracefully.  
   Log errors to a file for debugging purposes.  
   Update documentation to reflect new error-handling behavior.  
   ```

### 7. Use the body to explain what and why vs. how
   Focus on *what* changed and *why* it was necessary, not *how* it was implemented (the code explains the how). Include side effects or references to issues if applicable.  
   ```
   Simplify exception handling in serialize module

   Remove unused 'state' and 'exceptmask' variables from serialize  
   module to streamline code. These variables always triggered  
   exceptions, so direct exception throwing is used instead.  
   This reduces code complexity and removes dead code paths.  

   Resolves: #123  
   See also: #456, #789
   ```
