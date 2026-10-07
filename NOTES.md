# Patch Notes

## Summary of Changes

- Fixed the SQL search filter by grouping title and description conditions correctly with parentheses.
- Fixed frontend pagination so a new search or status filter resets to page 1.
- Replaced in-memory backend pagination with database-level pagination using `Pageable` and a count query.
- Removed the artificial `Thread.sleep()` delay from task requests.
- Replaced `System.out.println()` with SLF4J logging for task search information.

## What I Chose Not to Change

I did not rewrite the application or make unrelated architectural changes because the exercise was time-boxed. I also did not modify dependencies or run automatic dependency upgrades because they were outside the main bug-fixing scope.

## Biggest Remaining Risk

The search query uses `LOWER(...) LIKE '%term%'`, which may become slow as the task table grows because leading-wildcard searches may not use normal database indexes efficiently.

## Tools / AI Used

I used ChatGPT to help inspect the code, identify potential bugs, understand the root causes, and review the fixes. I manually applied the changes in VS Code and tested the API and frontend locally to verify the results.