# ProfileLane — AI-Powered Portfolio Generator

Turn a CV PDF into a live, hosted portfolio in minutes.

**Live product:** https://profilelane.com
**Example profile:** https://shaheer.profilelane.com

---

## The Problem

Portfolio builders force users to retype everything that's already on their CV. Most people already have a resume — they don't need another blank form to fill in.

ProfileLane starts from the document you already have.

## How It Works

1. Upload a CV PDF
2. An AI model extracts experience, education, skills, and projects into structured fields
3. The user reviews and edits the draft
4. Publish to a personal subdomain

## Architecture

- **Frontend:** Next.js
- **Backend:** Node.js
- **AI layer:** Model-based CV extraction with validation and fallback handling
- **Hosting:** Subdomain-based hosting for each user profile

See architecture.md for the full system design.

## Technical Challenges

- Reliable extraction from unstructured PDFs of varying formats
- Structuring inconsistent CV content into a fixed schema
- Building a review flow so users confirm AI output before publishing

See technical-challenges.md for details.

## Status

Live. Onboarding first users manually to ensure quality.

## Note on Source Code

The source code is private because ProfileLane is a commercial product. This repository documents the architecture and technical decisions behind the product.

---

## Repository Contents

- README.md — project overview
- architecture.md — system design and data flow
- technical-challenges.md — engineering problems and solutions
- screenshots/ — product screenshots
