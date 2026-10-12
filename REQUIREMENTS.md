# Portfolio Website Requirements

## Project

Turn `Sample_Candidate_Resume.pdf` into a polished, single-page portfolio website for the fictional **Sample Candidate**. The site should present the resume content clearly to recruiters and hiring managers while labeling the candidate and all resume content as fictional.

## Audience and goals

- Primary audience: recruiters and hiring managers.
- Position the candidate as an AI / Software Engineer with a broad professional profile.
- Lead with professional experience and results.
- Make it easy to contact the candidate; email is the primary call to action.
- Provide a downloadable copy of the source resume as a secondary action.
- Give the fictional resume content a polished, coherent personal-brand presentation.

## Content and accuracy

- Use the resume as the sole factual source.
- Do not add or imply credentials, employers, dates, skills, project details, publications, metrics, or accomplishments not stated in the resume.
- Rephrase resume content in a personable first-person voice where appropriate, without changing or extending its meaning.
- Use **Sample Candidate** as the displayed name and **AI / Software Engineer** as the professional identity.
- Include the profile, experience, skills, education, highlights, selected projects, and sample publications.
- Keep the fiction notice concise and visible near the top of the page. Repeat the notice next to the resume download so visitors understand that the downloadable resume is also fictional.
- Use the resume's email address for the contact action.
- Replace the resume's `samplecandidate.example` website link with the target GitHub Pages URL: `https://samplecandidate.github.io`.

## Structure and behavior

- Build a focused, single-page site with clear navigation to its content sections.
- Make contact by email the primary call to action, using the resume email address.
- Provide a working download link to `Sample_Candidate_Resume.pdf`, labeled as a PDF resume and accompanied by the fictional-demo notice.
- Navigation, email, website, and download links must work and have descriptive labels.
- Do not add a contact form, backend, or additional pages.

## Visual direction

- Clean, restrained, and recruiter-friendly.
- Use a professional blue-forward palette.
- Keep the presentation text-focused; do not add a portrait or fabricate imagery.
- Ensure the first view clearly identifies the candidate and role, communicates the fictional-demo status, and makes the contact action easy to find.

## Technical constraints

- Use a simple, low-maintenance static implementation suitable for GitHub Pages; avoid a framework or build system unless the existing project requires one.
- Target the standard GitHub Pages site URL `https://samplecandidate.github.io`; no custom domain is planned.
- The site must work when published at the repository's root URL.
- Do not add dependencies or services that require a server-side runtime.
- The layout must adapt to mobile and desktop screen sizes.
- Use semantic structure, keyboard-accessible navigation and actions, visible focus states, and readable color contrast.

## Acceptance criteria

1. The site presents a clear, professional AI / Software Engineer profile and makes experience the leading content.
2. All selected resume sections are represented, and every claim is traceable to the resume.
3. The fictional-demo label is visible near the top and repeated alongside the downloadable resume.
4. The primary contact action opens an email to the address printed in the resume.
5. The resume PDF can be downloaded from the page.
6. The listed website link targets `https://samplecandidate.github.io`, not the resume's placeholder domain.
7. Section navigation and all calls to action work using keyboard as well as pointer input.
8. The static site renders and remains usable at the standard GitHub Pages URL on mobile and desktop.
