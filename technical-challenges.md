# ProfileLane — Technical Challenges

This document describes the main engineering problems encountered while building ProfileLane, and the approaches taken to solve them.

## Challenge 1: Unstructured PDF Input

CVs arrive in wildly different formats. Some are clean, generated PDFs. Others are scans, exports from Word, or templates with unusual layouts.

**What fails:** Direct text extraction often produces garbled output, especially from multi-column layouts or PDFs with embedded images.

**Approach:** 
- Extract text with a focus on preserving section boundaries
- Run extraction through the AI model with a prompt that asks for best-effort structuring rather than exact parsing
- Route edge cases into the review flow so the user can fix issues rather than the system silently failing

## Challenge 2: Structuring Inconsistent Content

There is no standard format for a CV. Section names vary ("Experience" vs "Work History" vs "Professional Background"), date formats differ, and some CVs mix sections together.

**Approach:**
- Map free text into a fixed schema: experience, education, skills, projects
- Use the AI model to classify sections, then apply validation rules to reject low-confidence results
- Present the structured draft as editable fields so users can correct misclassifications

## Challenge 3: AI Reliability

AI models produce plausible output that isn't always correct. In a product where users publish the result publicly, unreviewed AI output is a liability.

**Approach:**
- **Validation:** Check the AI response against expected schema and required fields
- **Fallbacks:** If the model returns malformed output or times out, fall back to a minimal draft rather than failing
- **Review-before-publish:** Every AI-generated draft must be reviewed by the user before it goes live. Nothing publishes automatically.

## Lesson Learned

AI proposes, humans decide. This is the same principle I apply to AI-assisted development in daily work — use the model as a force multiplier, but keep the human accountable for the final result.
