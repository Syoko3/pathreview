## Week 7 — Issue selection

**Issue link:** https://github.com/ascherj/pathreview/issues/147

**Issue title:** Resume section detection fails on text with leading whitespace

**Tier:** [X] Tier 1  [ ] Tier 2  [ ] Tier 3

**"Is this right for me?" checklist reasoning:**
I selected the Tier 1 resume parser bug because it aligns well with my skill level for a first-time open-source contribution, and it has no open blockers, dependencies, or prohibitive contributor competition. I understood that the _detect_sections() function in ingestion/parsers/resume_parser.py incorrectly handles leading indentation/whitespace, causing empty sections to be detected. Fixing this will allow resume sections to be parsed accurately. I confirmed the file locations and reproduced the issue by running pytest on tests/unit/test_resume_parser.py. Three test cases, which were test_parse_single_column_resume_text, test_parse_resume_no_work_experience, and test_detect_sections, failed as expected due to this bug. Given the isolated nature of the bug and the clear test failures, I am confident I can resolve this ahead of the Week 9 deadline.

**Problem summary:**
The issue is the failure of the parser's section detection logic in ingestion/parsers/resume_parser.py. It expects the section headers to start exactly at the very beginning of the line. Because text extracted from PDFs preserves leading indentation or whitespaces, these headers are missed entirely, resulting empty sections detected. A successful fix will modify the regex patterns to allow leading whitespace before a header name, so that the parser can correctly identify and extract resume sections even when they are indented.

**Branch name:** fix/147-leading-whitespace

**Setup confirmation:** [X] App runs locally at localhost:5173

**Cohort ledger:** [X] Issue added to cohort ledger

---

## Week 8 — Reproduction & solution planning

**Reproduction commit link:** https://github.com/Syoko3/pathreview/commit/1840b5738e8615099fe5e0be56bc7415ac64db5f

**Reproduction summary:**
I reproduced the issue by creating the detect_sections_bug.py to test the reproduction bug logic, and mark the _detect_sections() as a bug in ingestion/parser/resume_parser.py and the related failing tests in tests/unit/test_unit_parser.py. When I run the _detect_sections_bug.py, it returns an empty list, but the expected output has to return "Education" and "Skills" as the list. I also ran the unit tests for the parser again, and confirmed that section headers with leading whitespaces are not detected, so _detect_section() of resume_parser.py will return as an empty list.

**PLAN.md link:** https://github.com/Syoko3/pathreview/blob/fix/147-leading-whitespace/PLAN.md

**Walkthrough video (recommended):** [link to your Loom video, ≤2 min — recommended, not graded]

**Blockers or open questions:**

---

## Week 9 — Solution building & PR submission

### Check-in 1 (mid-week)

**Current progress:**
I implemented the fix of the _detect_sections() of the ingestion/parsers/resume_parser.py by updating the regex of the section header patterns. After that, I confirmed the bug is fixed by running the unit test of the resume parser (tests/unit/test_resume_parser.py) to verify the three related failing tests are passed. I also ran the reproduction script and verified that the sections are correctly detected. I added the test cases for the leading whitespaces and the edge cases (.e.g. non-indented headers, substring words, etc.) in the test file, and verified that these tests also passed. I finished all of the sub-tasks from PLAN.md.

**Next steps:**
I have to open the draft pull request on GitHub and document pre-existing make check / make test-unit baseline failures in the PR description. I have to share the Draft PR link to the peer/mentor, and address any review feedback. I have to look the PR thread every day at least once. After addressing any review feedback, I have to update `JOURNAL.md` with Check-in 2, and mark PR as "Ready for review".

**Blockers:**

---

### Check-in 2 (end of week)

**PR link:** [link to your submitted pull request]

**Branch:** [the branch name you worked on, e.g. `fix/123-short-description`]

**What you built:**
[1–3 sentences summarizing what your fix does and how it works]

**Tests added or updated:**
[Which test files did you touch? What do they cover?]

**Self-review confirmation:** [ ] make check passes  [ ] make test-unit passes

**Draft PR feedback received from:** [name or Slack handle, or "none"]