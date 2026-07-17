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