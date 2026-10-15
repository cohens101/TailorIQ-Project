# TailorIQ — Engineering case study

## The problem

Tailoring my own resume to different job postings was repetitive. The underlying experience remained the same while each posting prioritized different strengths. I wanted a faster way to show relevant experience without overstating qualifications.

## The product

I built a one-click resume-tailoring workflow: upload a DOCX or text-based PDF, paste a job posting, let AI propose grounded improvements, review the result, then download Word or PDF.

The main priority is the resulting resume—not a match score.

## What made it difficult

### Parsing unpredictable source formats

Resumes use tables, columns, stacked promotions, consulting engagements, part-time work, career breaks, and inconsistent headings. PDFs can split a single responsibility across lines.

A significant learning point: extracting every word is not sufficient. The application also has to preserve **which organization each job belongs to**, and which duties, dates, and qualifiers belong to each role.

### Keeping generated claims grounded

General-purpose AI can make a resume sound better while unintentionally inventing skill proficiency or overstating accomplishments.

I integrated Anthropic Claude for source-linked rewrites and built validation around existing experience. Uncertain edits can retain the original wording instead of creating facts.

### Exporting the actual artifact

A clean preview does not mean a safe resume. The native Word and PDF must preserve the same responsibilities, education, dates, and employment structure. The implementation includes final document checks and Quality Check behavior designed to prevent material omissions.

## Stack

- Next.js 16, React 19, TypeScript, Tailwind CSS 4
- Anthropic Claude API with structured output validation
- Mammoth, unpdf, docx, pdf-lib
- GitHub and Railway for source and deployment
- Cursor for AI-assisted development and debugging

## How I evaluated it

I used fictional resumes, realistic job descriptions, automated regression tests, actual AI calls, independent acceptance feedback, and document inspections.

The central insight was that **resume fidelity is more important than fluent wording or a high-looking match score**.

## Product choices

- One-click tailoring
- Education below Professional Summary
- Resume Length preference: 1 Page / 2 Pages / Auto
- Supporting Resume Quality Check and Match Analysis
- No automatic keyword bolding

## Scope

This is a controlled-beta project; applicants should always review output before submission. This repository documents the project without exposing private implementation or applicant records.

[Project overview](../README.md) · [Architecture](ARCHITECTURE.md)
