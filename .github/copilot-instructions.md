# Repository about AI Examples

- This repository does not contain programming code explicitly, so, unless you are asked, you should avoid writing code.

- The main contents of the repository are the examples, which are documented as markdown files. All new added examples should follow the provided template (./template.md at the root of the repository). You can use the `./human/new_epiworld_model.md` as a reference.

- Whenever you are adding a new example, make sure to fill out all the metadata fields in the template, including the authorship.

- Examples created by you should be added to the `./ai` directory. Everytime that you add a new example, ensure that you update the list of contents under `./ai/README.md`. and `./README.md`, adding a link to the new example.

## Guidelines for Creating Examples

- **Date formatting**: Always use the `date` command to get the current date and format it as YYYY-MM-DD in the metadata section. Do not use arbitrary dates.

- **"What worked well" section**: This section should focus on factors from the user, repository, or environment that enabled success, such as:
  - Clear instructions or requirements provided by the user
  - Good examples available in the repository for reference
  - Well-organized repository structure
  - Clear and comprehensive documentation (like copilot-instructions.md)
  - The task being well-suited to AI capabilities (common in training data)
  - Effective feedback processes and communication
  
  Avoid focusing primarily on AI capabilities or performance. Instead, highlight what external factors set up the AI for success.

- **"What did not work well" section**: This section should focus on actual mistakes, glitches, or things the AI missed that required human intervention to fix. Look for evidence of this in:
  - User commits that modified the AI's work
  - User comments that pointed out issues or corrections needed
  - Follow-up issues or PRs that addressed problems in the AI's implementation
  - Specific errors or misunderstandings in the AI's approach
  
  Avoid describing task complexity, scope, or normal development considerations as "what did not work well." Having no significant issues is perfectly acceptable for straightforward tasks.