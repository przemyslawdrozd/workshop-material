# GitHub Copilot Certification - Practice Test 2 (Interactive Format)

## Advanced Features and Enterprise Usage

## Instructions

- 30 questions total
- Time Limit: 45 minutes
- Passing score: 80% (24 correct answers)
- Choose the best answer for each question

---

### 1. What is the primary advantage of GitHub Copilot Business over GitHub Copilot Individual?

| Option | Answer                                         | Correct                   |
| ------ | ---------------------------------------------- | ------------------------- |
| A      | Faster code suggestions                        | <input type="checkbox" /> |
| B      | More programming languages supported           | <input type="checkbox" /> |
| C      | Enterprise-grade privacy and security features | <input type="checkbox" /> |
| D      | Better integration with VS Code                | <input type="checkbox" /> |

<details>
<summary>Pokaż poprawną odpowiedź</summary>

**Correct answer:** C. Enterprise-grade privacy and security features

**Why:** GitHub Copilot Business provides enterprise-grade privacy features, including no training on business data, audit logs, and administrative controls.

</details>

---

### 2. Which file would you create to exclude specific patterns from GitHub Copilot suggestions?

| Option | Answer                           | Correct                   |
| ------ | -------------------------------- | ------------------------- |
| A      | `.copilot-ignore`                | <input type="checkbox" /> |
| B      | `.github/copilot-exclusions.yml` | <input type="checkbox" /> |
| C      | `copilot-config.json`            | <input type="checkbox" /> |
| D      | `.copilotignore`                 | <input type="checkbox" /> |

<details>
<summary>Pokaż poprawną odpowiedź</summary>

**Correct answer:** B. `.github/copilot-exclusions.yml`

**Why:** The `.github/copilot-exclusions.yml` file is used to configure content exclusions at the repository level.

</details>

---

### 3. What does the `copilot:disable-next-line` comment accomplish in your code?

| Option | Answer                                            | Correct                   |
| ------ | ------------------------------------------------- | ------------------------- |
| A      | Prevents Copilot from suggesting similar patterns | <input type="checkbox" /> |
| B      | Excludes the next line from Copilot training data | <input type="checkbox" /> |
| C      | Disables Copilot for the entire file              | <input type="checkbox" /> |
| D      | Marks the line as sensitive data                  | <input type="checkbox" /> |

<details>
<summary>Pokaż poprawną odpowiedź</summary>

**Correct answer:** B. Excludes the next line from Copilot training data

**Why:** The `copilot:disable-next-line` comment excludes the immediately following line from being used in Copilot's training data and suggestions.

</details>

---

### 4. In GitHub Copilot Chat, which prompt would be MOST effective for generating unit tests?

| Option | Answer                                                              | Correct                   |
| ------ | ------------------------------------------------------------------- | ------------------------- |
| A      | "write tests"                                                       | <input type="checkbox" /> |
| B      | "generate unit tests for this function with edge cases and mocking" | <input type="checkbox" /> |
| C      | "test this code"                                                    | <input type="checkbox" /> |
| D      | "make tests for function"                                           | <input type="checkbox" /> |

<details>
<summary>Pokaż poprawną odpowiedź</summary>

**Correct answer:** B. "generate unit tests for this function with edge cases and mocking"

**Why:** Specific, detailed prompts that include context like "edge cases and mocking" produce better, more comprehensive results.

</details>

---

### 5. What is the maximum context window that GitHub Copilot typically considers when making suggestions?

| Option | Answer                                  | Correct                   |
| ------ | --------------------------------------- | ------------------------- |
| A      | Current line only                       | <input type="checkbox" /> |
| B      | Current function                        | <input type="checkbox" /> |
| C      | Current file plus recently opened files | <input type="checkbox" /> |
| D      | Entire project directory                | <input type="checkbox" /> |

<details>
<summary>Pokaż poprawną odpowiedź</summary>

**Correct answer:** C. Current file plus recently opened files

**Why:** Copilot considers the current file and recently opened files to provide contextually relevant suggestions.

</details>

---

### 6. Which keyboard shortcut accepts a GitHub Copilot suggestion in VS Code?

| Option | Answer                        | Correct                   |
| ------ | ----------------------------- | ------------------------- |
| A      | Ctrl+Enter (Cmd+Enter on Mac) | <input type="checkbox" /> |
| B      | Tab                           | <input type="checkbox" /> |
| C      | Ctrl+Space (Cmd+Space on Mac) | <input type="checkbox" /> |
| D      | Enter                         | <input type="checkbox" /> |

<details>
<summary>Pokaż poprawną odpowiedź</summary>

**Correct answer:** B. Tab

**Why:** The Tab key is the standard shortcut to accept a Copilot suggestion in VS Code.

</details>

---

### 7. What happens when you enable "public code suggestions" in GitHub Copilot settings?

| Option | Answer                                                  | Correct                   |
| ------ | ------------------------------------------------------- | ------------------------- |
| A      | Your code becomes publicly available                    | <input type="checkbox" /> |
| B      | Copilot can suggest code similar to public repositories | <input type="checkbox" /> |
| C      | All suggestions are based only on open source code      | <input type="checkbox" /> |
| D      | Copilot shares your code with other users               | <input type="checkbox" /> |

<details>
<summary>Pokaż poprawną odpowiedź</summary>

**Correct answer:** B. Copilot can suggest code similar to public repositories

**Why:** When enabled, Copilot can suggest code that might be similar to publicly available code repositories.

</details>

---

### 8. In a team environment, how should you handle Copilot suggestions that might contain hardcoded secrets?

| Option | Answer                                                           | Correct                   |
| ------ | ---------------------------------------------------------------- | ------------------------- |
| A      | Use them as-is since Copilot filters secrets                     | <input type="checkbox" /> |
| B      | Always review suggestions and replace with environment variables | <input type="checkbox" /> |
| C      | Disable Copilot in security-sensitive files                      | <input type="checkbox" /> |
| D      | Report the suggestions to GitHub                                 | <input type="checkbox" /> |

<details>
<summary>Pokaż poprawną odpowiedź</summary>

**Correct answer:** B. Always review suggestions and replace with environment variables

**Why:** Always review suggestions and replace any hardcoded values with secure alternatives like environment variables.

</details>

---

### 9. Which of the following is NOT a valid way to provide context to GitHub Copilot?

| Option | Answer                                       | Correct                   |
| ------ | -------------------------------------------- | ------------------------- |
| A      | Writing descriptive comments                 | <input type="checkbox" /> |
| B      | Using meaningful variable names              | <input type="checkbox" /> |
| C      | Including example inputs/outputs in comments | <input type="checkbox" /> |
| D      | Adding random text to increase file size     | <input type="checkbox" /> |

<details>
<summary>Pokaż poprawną odpowiedź</summary>

**Correct answer:** D. Adding random text to increase file size

**Why:** Random text doesn't provide meaningful context. Copilot works best with clear, descriptive code and comments.

</details>

---

### 10. What is the recommended approach when Copilot suggests code that you don't fully understand?

| Option | Answer                                                  | Correct                   |
| ------ | ------------------------------------------------------- | ------------------------- |
| A      | Accept it anyway since Copilot is usually correct       | <input type="checkbox" /> |
| B      | Reject it and write the code manually                   | <input type="checkbox" /> |
| C      | Research and understand the suggestion before accepting | <input type="checkbox" /> |
| D      | Modify it randomly until it works                       | <input type="checkbox" /> |

<details>
<summary>Pokaż poprawną odpowiedź</summary>

**Correct answer:** C. Research and understand the suggestion before accepting

**Why:** Always understand code before accepting it. This ensures code quality and helps you learn.

</details>

---

### 11. In GitHub Copilot for Business, audit logs capture:

| Option | Answer                                     | Correct                   |
| ------ | ------------------------------------------ | ------------------------- |
| A      | Only accepted suggestions                  | <input type="checkbox" /> |
| B      | All suggestions shown to users             | <input type="checkbox" /> |
| C      | User engagement data and policy violations | <input type="checkbox" /> |
| D      | Source code from suggestions               | <input type="checkbox" /> |

<details>
<summary>Pokaż poprawną odpowiedź</summary>

**Correct answer:** C. User engagement data and policy violations

**Why:** Audit logs track user engagement, policy compliance, and security events, not the actual code content.

</details>

---

### 12. Which prompt engineering technique is MOST effective for generating database queries?

| Option | Answer                                                                                                              | Correct                   |
| ------ | ------------------------------------------------------------------------------------------------------------------- | ------------------------- |
| A      | "write SQL"                                                                                                         | <input type="checkbox" /> |
| B      | "SELECT \* FROM table"                                                                                              | <input type="checkbox" /> |
| C      | "Write a SQL query to find all users who registered in the last 30 days, include their email and registration date" | <input type="checkbox" /> |
| D      | "database query needed"                                                                                             | <input type="checkbox" /> |

<details>
<summary>Pokaż poprawną odpowiedź</summary>

**Correct answer:** C. "Write a SQL query to find all users who registered in the last 30 days, include their email and registration date"

**Why:** Specific prompts with clear requirements (timeframe, fields needed) generate more accurate and useful queries.

</details>

---

### 13. What is the primary purpose of GitHub Copilot's content filtering?

| Option | Answer                                              | Correct                   |
| ------ | --------------------------------------------------- | ------------------------- |
| A      | Improve code quality                                | <input type="checkbox" /> |
| B      | Prevent copyright violations                        | <input type="checkbox" /> |
| C      | Filter out sensitive data and inappropriate content | <input type="checkbox" /> |
| D      | Reduce suggestion response time                     | <input type="checkbox" /> |

<details>
<summary>Pokaż poprawną odpowiedź</summary>

**Correct answer:** C. Filter out sensitive data and inappropriate content

**Why:** Content filtering helps prevent suggestions containing sensitive data, secrets, or inappropriate content.

</details>

---

### 14. In which scenario should you use GitHub Copilot Chat instead of inline suggestions?

| Option | Answer                                            | Correct                   |
| ------ | ------------------------------------------------- | ------------------------- |
| A      | Simple code completion                            | <input type="checkbox" /> |
| B      | Explaining complex algorithms or debugging issues | <input type="checkbox" /> |
| C      | Variable name suggestions                         | <input type="checkbox" /> |
| D      | Syntax correction                                 | <input type="checkbox" /> |

<details>
<summary>Pokaż poprawną odpowiedź</summary>

**Correct answer:** B. Explaining complex algorithms or debugging issues

**Why:** Copilot Chat is ideal for explanations, debugging help, and complex problem-solving conversations.

</details>

---

### 15. What does GDPR compliance mean for GitHub Copilot users?

| Option | Answer                                                      | Correct                   |
| ------ | ----------------------------------------------------------- | ------------------------- |
| A      | Code suggestions are stored indefinitely                    | <input type="checkbox" /> |
| B      | Users have rights to access, correct, and delete their data | <input type="checkbox" /> |
| C      | All European users must use Copilot Business                | <input type="checkbox" /> |
| D      | Code is automatically shared with EU authorities            | <input type="checkbox" /> |

<details>
<summary>Pokaż poprawną odpowiedź</summary>

**Correct answer:** B. Users have rights to access, correct, and delete their data

**Why:** GDPR provides users with rights over their personal data, including access, rectification, and erasure rights.

</details>

---

### 16. Which comment style provides the BEST context for Copilot suggestions?

| Option | Answer                                                                                          | Correct                   |
| ------ | ----------------------------------------------------------------------------------------------- | ------------------------- |
| A      | `// TODO: fix this`                                                                             | <input type="checkbox" /> |
| B      | `// Calculate the monthly payment for a loan given principal, interest rate, and term in years` | <input type="checkbox" /> |
| C      | `// This is important`                                                                          | <input type="checkbox" /> |
| D      | `// Code goes here`                                                                             | <input type="checkbox" /> |

<details>
<summary>Pokaż poprawną odpowiedź</summary>

**Correct answer:** B. `// Calculate the monthly payment for a loan given principal, interest rate, and term in years`

**Why:** Detailed, descriptive comments that explain the purpose and requirements help Copilot generate better suggestions.

</details>

---

### 17. In a multi-file project, how does Copilot understand relationships between files?

| Option | Answer                                                   | Correct                   |
| ------ | -------------------------------------------------------- | ------------------------- |
| A      | By analyzing import statements and recently opened files | <input type="checkbox" /> |
| B      | By scanning the entire project directory                 | <input type="checkbox" /> |
| C      | By reading the README file                               | <input type="checkbox" /> |
| D      | It doesn't consider other files                          | <input type="checkbox" /> |

<details>
<summary>Pokaż poprawną odpowiedź</summary>

**Correct answer:** A. By analyzing import statements and recently opened files

**Why:** Copilot analyzes imports, dependencies, and recently opened files to understand project context.

</details>

---

### 18. What is the recommended practice for using Copilot with test-driven development (TDD)?

| Option | Answer                                                         | Correct                   |
| ------ | -------------------------------------------------------------- | ------------------------- |
| A      | Write tests after implementation                               | <input type="checkbox" /> |
| B      | Let Copilot write both tests and implementation                | <input type="checkbox" /> |
| C      | Write failing tests first, then use Copilot for implementation | <input type="checkbox" /> |
| D      | Avoid using Copilot for testing                                | <input type="checkbox" /> |

<details>
<summary>Pokaż poprawną odpowiedź</summary>

**Correct answer:** C. Write failing tests first, then use Copilot for implementation

**Why:** TDD best practice is to write failing tests first, then use Copilot to help implement the functionality to make tests pass.

</details>

---

### 19. Which organization setting would prevent Copilot from using public code patterns in suggestions?

| Option | Answer                           | Correct                   |
| ------ | -------------------------------- | ------------------------- |
| A      | `public_code_suggestions: false` | <input type="checkbox" /> |
| B      | `allow_public_code: false`       | <input type="checkbox" /> |
| C      | `block_public_suggestions: true` | <input type="checkbox" /> |
| D      | `private_mode: true`             | <input type="checkbox" /> |

<details>
<summary>Pokaż poprawną odpowiedź</summary>

**Correct answer:** A. `public_code_suggestions: false`

**Why:** Setting `public_code_suggestions` to false prevents Copilot from suggesting code similar to public repositories.

</details>

---

### 20. When should you manually exclude content using `copilot:disable` comments?

| Option | Answer                                                     | Correct                   |
| ------ | ---------------------------------------------------------- | ------------------------- |
| A      | Never, rely on automatic filtering                         | <input type="checkbox" /> |
| B      | For any proprietary algorithms or sensitive business logic | <input type="checkbox" /> |
| C      | Only for password variables                                | <input type="checkbox" /> |
| D      | For all database-related code                              | <input type="checkbox" /> |

<details>
<summary>Pokaż poprawną odpowiedź</summary>

**Correct answer:** B. For any proprietary algorithms or sensitive business logic

**Why:** Manual exclusions should be used for proprietary algorithms, sensitive business logic, or confidential information.

</details>

---

### 21. What is the correct syntax to disable Copilot for an entire code block?

| Option | Answer                                                      | Correct                   |
| ------ | ----------------------------------------------------------- | ------------------------- |
| A      | `// copilot:disable-block`                                  | <input type="checkbox" /> |
| B      | `/* copilot:disable-start */ ... /* copilot:disable-end */` | <input type="checkbox" /> |
| C      | `// copilot:disable-start` ... `// copilot:disable-end`     | <input type="checkbox" /> |
| D      | `// copilot:off` ... `// copilot:on`                        | <input type="checkbox" /> |

<details>
<summary>Pokaż poprawną odpowiedź</summary>

**Correct answer:** C. `// copilot:disable-start` ... `// copilot:disable-end`

**Why:** Use `// copilot:disable-start` and `// copilot:disable-end` comments to exclude entire code blocks.

</details>

---

### 22. In enterprise environments, what is the recommended approach for handling Copilot-generated code in security-critical applications?

| Option | Answer                                                            | Correct                   |
| ------ | ----------------------------------------------------------------- | ------------------------- |
| A      | Trust Copilot completely                                          | <input type="checkbox" /> |
| B      | Disable Copilot entirely                                          | <input type="checkbox" /> |
| C      | Review all suggestions through security and code review processes | <input type="checkbox" /> |
| D      | Only use suggestions for non-critical features                    | <input type="checkbox" /> |

<details>
<summary>Pokaż poprawną odpowiedź</summary>

**Correct answer:** C. Review all suggestions through security and code review processes

**Why:** All code, including Copilot suggestions, should go through proper security review and code review processes.

</details>

---

### 23. Which type of data does GitHub Copilot NOT collect?

| Option | Answer                         | Correct                   |
| ------ | ------------------------------ | ------------------------- |
| A      | Suggestion acceptance rates    | <input type="checkbox" /> |
| B      | Complete source code files     | <input type="checkbox" /> |
| C      | Error messages and diagnostics | <input type="checkbox" /> |
| D      | Feature usage patterns         | <input type="checkbox" /> |

<details>
<summary>Pokaż poprawną odpowiedź</summary>

**Correct answer:** B. Complete source code files

**Why:** Copilot doesn't collect complete source files, only the necessary context for generating suggestions.

</details>

---

### 24. What is the primary benefit of using descriptive function and variable names when working with Copilot?

| Option | Answer                                                            | Correct                   |
| ------ | ----------------------------------------------------------------- | ------------------------- |
| A      | Faster code execution                                             | <input type="checkbox" /> |
| B      | Better context understanding leading to more accurate suggestions | <input type="checkbox" /> |
| C      | Reduced memory usage                                              | <input type="checkbox" /> |
| D      | Improved IDE performance                                          | <input type="checkbox" /> |

<details>
<summary>Pokaż poprawną odpowiedź</summary>

**Correct answer:** B. Better context understanding leading to more accurate suggestions

**Why:** Descriptive names provide better context, helping Copilot understand your intent and generate more accurate suggestions.

</details>

---

### 25. In GitHub Copilot Chat, what does the `/explain` command do?

| Option | Answer                                         | Correct                   |
| ------ | ---------------------------------------------- | ------------------------- |
| A      | Explains how Copilot works                     | <input type="checkbox" /> |
| B      | Provides detailed explanation of selected code | <input type="checkbox" /> |
| C      | Shows keyboard shortcuts                       | <input type="checkbox" /> |
| D      | Explains the current project structure         | <input type="checkbox" /> |

<details>
<summary>Pokaż poprawną odpowiedź</summary>

**Correct answer:** B. Provides detailed explanation of selected code

**Why:** The `/explain` command in Copilot Chat provides detailed explanations of selected code snippets.

</details>

---

### 26. Which practice BEST demonstrates responsible AI usage with Copilot?

| Option | Answer                                                         | Correct                   |
| ------ | -------------------------------------------------------------- | ------------------------- |
| A      | Accepting all suggestions without review                       | <input type="checkbox" /> |
| B      | Using suggestions only for boilerplate code                    | <input type="checkbox" /> |
| C      | Understanding, reviewing, and testing all accepted suggestions | <input type="checkbox" /> |
| D      | Sharing all suggestions with team members                      | <input type="checkbox" /> |

<details>
<summary>Pokaż poprawną odpowiedź</summary>

**Correct answer:** C. Understanding, reviewing, and testing all accepted suggestions

**Why:** Responsible AI usage involves understanding, reviewing, and testing all code before implementation.

</details>

---

### 27. What should you do if Copilot suggests code that appears to violate your organization's coding standards?

| Option | Answer                                                         | Correct                   |
| ------ | -------------------------------------------------------------- | ------------------------- |
| A      | Accept it and fix it later                                     | <input type="checkbox" /> |
| B      | Report it as a bug to GitHub                                   | <input type="checkbox" /> |
| C      | Reject the suggestion and follow your organization's standards | <input type="checkbox" /> |
| D      | Use it but don't tell anyone                                   | <input type="checkbox" /> |

<details>
<summary>Pokaż poprawną odpowiedź</summary>

**Correct answer:** C. Reject the suggestion and follow your organization's standards

**Why:** Always prioritize your organization's coding standards and best practices over AI suggestions.

</details>

---

### 28. In terms of intellectual property, who owns the code generated by GitHub Copilot?

| Option | Answer                                   | Correct                   |
| ------ | ---------------------------------------- | ------------------------- |
| A      | GitHub/Microsoft                         | <input type="checkbox" /> |
| B      | OpenAI                                   | <input type="checkbox" /> |
| C      | The developer who accepts the suggestion | <input type="checkbox" /> |
| D      | It's shared ownership                    | <input type="checkbox" /> |

<details>
<summary>Pokaż poprawną odpowiedź</summary>

**Correct answer:** C. The developer who accepts the suggestion

**Why:** The developer who accepts and implements Copilot suggestions owns the resulting code, subject to applicable licenses.

</details>

---

### 29. What is the recommended way to handle Copilot suggestions in open source projects?

| Option | Answer                                            | Correct                   |
| ------ | ------------------------------------------------- | ------------------------- |
| A      | Always accept them since they're from AI          | <input type="checkbox" /> |
| B      | Review for license compatibility and code quality | <input type="checkbox" /> |
| C      | Avoid using Copilot in open source                | <input type="checkbox" /> |
| D      | Use them only for documentation                   | <input type="checkbox" /> |

<details>
<summary>Pokaż poprawną odpowiedź</summary>

**Correct answer:** B. Review for license compatibility and code quality

**Why:** Review suggestions for license compatibility, code quality, and alignment with project goals and standards.

</details>

---

### 30. Which metric is MOST important for measuring Copilot effectiveness in a development team?

| Option | Answer                                               | Correct                   |
| ------ | ---------------------------------------------------- | ------------------------- |
| A      | Number of suggestions generated                      | <input type="checkbox" /> |
| B      | Speed of code completion                             | <input type="checkbox" /> |
| C      | Developer productivity and code quality improvements | <input type="checkbox" /> |
| D      | Percentage of suggestions accepted                   | <input type="checkbox" /> |

<details>
<summary>Pokaż poprawną odpowiedź</summary>

**Correct answer:** C. Developer productivity and code quality improvements

**Why:** The most important metrics are overall developer productivity gains and improvements in code quality and delivery speed.

</details>
