# Tailoring pipeline

When this file is attached (`@promps.md`), tailor a company-specific CV from a **base** resume and a job description pasted in the chat.

## Workflow

1. Use the base the user tagged (`@english/cv.tex` or `@spanish/cv-spanish.tex`). If they only give a language, pick `english/cv.tex` for English and `spanish/cv-spanish.tex` for Spanish. Never start from an old company folder.
2. Create a **new folder** named after the company (lowercase slug: `peya`, `kala`, `stripe`).
3. Copy the base into `{company}/cv-{company}-{english|spanish}.tex`. Optionally save the JD as `{company}/job-description.md`. Add a cover letter only if asked.
4. Run the three prompts below **in order**. Then compile with `pdflatex`.

## Hard rules

- Do **not** invent employers, dates, titles, metrics, or technologies that are not in the base CV. Reorder, rephrase, and emphasize only.
- If a JD keyword is a real gap, leave it out of the resume and mention it in the chat.
- Keep the LaTeX preamble and ATS setup from the base. Keep **1–2 pages**.
- Headline, summary, and skills must match the JD using **real** experience only.
- Put the most relevant jobs on page 1. Reorder bullets; do not fabricate impact.

## Prompt 1 — Recruiter match

Act as a senior recruiter for this exact company. Analyze my resume against this job description and give me a match score out of 100, the top 5 missing keywords, and the 3 red flags a hiring manager would spot in under 10 seconds.

## Prompt 2 — Rewrite experience

Rewrite my experience section to naturally include those keywords and remove the red flags. Use the Google XYZ formula: Accomplish X as measured by Y by doing Z.

Only weave in keywords that are already true in the base CV.

## Prompt 3 — ATS / hiring-manager scan

Now act as an ATS filter and a hiring manager reading 200 resumes in one sitting. Scan my new resume and tell me which sections would get skipped, then rewrite them so they actually stop the scroll.
