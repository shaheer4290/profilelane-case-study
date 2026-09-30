# ProfileLane — Architecture

## Overview

ProfileLane is a web application that converts CV PDFs into structured, hosted portfolios. The system consists of four main layers: frontend, backend, AI extraction, and hosting.

## System Components

### Frontend (Next.js)

- User dashboard for uploading CVs and reviewing drafts
- Public profile pages rendered from structured data
- Form-based editing of AI-extracted content
- Built with Next.js, React, and TypeScript

### Backend (Node.js)

- Handles file uploads and temporary storage
- Orchestrates the AI extraction pipeline
- Manages user accounts, profiles, and publishing state
- Serves public profile pages on subdomains

### AI Extraction Layer

- Accepts PDF input and extracts raw text
- Sends structured prompts to an AI model to identify CV sections
- Maps extracted content into a fixed schema: experience, education, skills, projects
- Applies validation and fallback handling for malformed or unusual CVs

### Hosting

- Each user profile is published to a personal subdomain
- Subdomain routing resolves the requested profile and serves the rendered page
- No manual infrastructure setup required by the user

## Data Flow

1. User uploads a CV PDF via the dashboard
2. Backend extracts text from the PDF
3. Text is sent to the AI model with a structured prompt
4. AI returns a draft profile: experience, education, skills, projects
5. Backend validates the response and stores it as a draft
6. User reviews and edits the draft in the dashboard
7. On publish, the profile is rendered and served on the user's subdomain

## Stack Rationale

**Why Next.js:** Server-side rendering for public profiles, strong SEO, and a single framework for both dashboard and public pages.

**Why Node.js:** Natural fit with Next.js, strong ecosystem for PDF parsing and AI model integration, and good support for async processing.

**Why subdomain routing:** Gives each user a clean, personal URL without requiring DNS configuration on their side.

## Diagram

A simplified flow:
User → Upload PDF → Backend → Text Extraction → AI Model → Structured Draft → User Review → Publish → Public Subdomain
