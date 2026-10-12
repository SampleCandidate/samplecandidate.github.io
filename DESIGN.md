# Portfolio Website Implementation Design

## Goal

Build a polished, single-page portfolio for the fictional Sample Candidate using the supplied resume as the only factual source. The site will be a static GitHub Pages site published from the repository root at `https://samplecandidate.github.io`.

## Technical approach

- Use plain HTML and CSS. Do not add a framework, build step, JavaScript, dependencies, backend, contact form, or additional pages.
- Keep the site entry point at `index.html`, styles in `styles.css`, and the supplied `Sample_Candidate_Resume.pdf` at the repository root. Preserve the PDF as the downloadable source resume.
- Use in-page links to navigate between semantic sections. Use relative paths for local assets so the site works at the root GitHub Pages URL.
- Use native HTML links for email, the website, and the PDF download. The email link must use the address printed in the resume; the website link must be `https://samplecandidate.github.io`; the PDF link must resolve to `./Sample_Candidate_Resume.pdf`.
- Use a restrained blue-forward visual style, system fonts, and CSS media queries for responsive layout. Avoid imagery and external font or asset services.
- Use semantic HTML landmarks and headings, descriptive link text, visible keyboard focus, and sufficient text/background contrast.

## Content and accuracy rules

- Read the supplied PDF before writing any resume-derived content. Treat it as the sole factual source.
- Include the profile, experience, skills, education, highlights, selected projects, and sample publications requested by `REQUIREMENTS.md`.
- Do not invent or imply employers, dates, credentials, skills, project details, publications, metrics, or achievements. Rephrasing in a first-person voice is acceptable only when it preserves the resume's meaning.
- Display the name **Sample Candidate** and role **AI / Software Engineer**. Clearly label the person and resume as fictional near the top of the page, and repeat the fiction notice beside the PDF download.
- Use concise, readable copy and make professional experience prominent. The email contact action is primary; the resume download is secondary.

## Repository structure after implementation

```text
index.html
styles.css
Sample_Candidate_Resume.pdf
REQUIREMENTS.md
DESIGN.md
README.md
```

Do not add other files unless an existing project constraint makes them necessary.

## Implementation stages

### Stage 1 — Establish the page and essential actions

Create a usable, semantic page shell first, then add the identity, fiction notice, and working primary/secondary actions.

### Stage 2 — Add resume content faithfully

Populate the requested content sections in deliberate priority order: profile and experience first, then skills and education, then highlights, projects, and sample publications.

### Stage 3 — Present and verify the complete site

Apply the visual system to all sections, adapt it for mobile, and verify the content, links, keyboard behavior, and root-path assumptions against the requirements.

## Coding increments

Give a coding agent only one increment prompt at a time. Each prompt below is standalone; it identifies the source of truth, constrains scope, and defines checks before the agent reports completion. Do not begin a later increment until the current one passes its verification.

### Increment 1.1 — Create the static page shell

```text
Read REQUIREMENTS.md and inspect the existing repository before changing files. The supplied Sample_Candidate_Resume.pdf is the sole factual source for resume content; do not make up candidate details.

Objective: establish the smallest working static-site foundation for the portfolio. Create a root-level index.html and styles.css. In index.html, add standard document metadata, a semantic page header, a main landmark, and empty, clearly identified sections with stable IDs for profile, experience, skills, education, highlights, projects, and publications. Add a simple navigation list whose links target those section IDs. Add a footer. Use headings and semantic elements, but do not add resume claims, contact details, calls to action, or visual styling beyond basic readable defaults.

Constraints: use plain HTML and CSS only; no framework, build system, JavaScript, dependencies, external assets, or additional pages. Do not modify or move the supplied PDF or unrelated files. Keep all local paths suitable for publication from the repository root.

Verify: inspect the resulting files; confirm every navigation href matches exactly one section ID, all required section IDs exist, the page has valid basic document structure, and no scripts or dependencies were introduced. If an HTML validator or browser is available, use it and report the observed result. Do not claim checks that were not performed.
```

### Increment 1.2 — Add identity, fiction label, and actions

```text
Read REQUIREMENTS.md and inspect the current index.html and styles.css. Read the supplied Sample_Candidate_Resume.pdf before using any resume-specific contact detail. Build on the existing static page; do not replace its working section navigation.

Objective: make the top of the page identify the candidate and role, clearly label the portfolio as fictional, and provide working email and resume actions. Display “Sample Candidate” and “AI / Software Engineer”. Use the email address printed in the resume for the primary email link. Link the secondary PDF action to ./Sample_Candidate_Resume.pdf, label it clearly as a PDF resume, and place a concise fictional-demo notice beside it. Add a website link targeting https://samplecandidate.github.io.

Constraints: the resume is the sole factual source. Do not invent a phone number, contact details, biography, or other claim. Keep the fiction notice visible near the top. Do not add a form, backend, JavaScript, dependencies, or another page. Keep the download secondary to email.

Verify: compare the displayed email with the PDF; inspect href values for mailto:, the exact website URL, and the relative PDF path; confirm the PDF file exists in the repository root; confirm the fiction notice appears both near the top and beside the download; and confirm existing navigation still targets its sections.
```

### Increment 2.1 — Add profile and lead with experience

```text
Read REQUIREMENTS.md and inspect the current page. Read Sample_Candidate_Resume.pdf and use it as the only source for all resume facts. Build on the existing page and keep the current navigation, identity, fiction label, contact action, and download working.

Objective: add the resume-supported profile and professional experience. Place experience immediately after the introductory area so it is the leading substantive content. Preserve role/employer names, dates, descriptions, and results as stated in the PDF. Rephrase selectively in a personable first-person voice only where that does not change or extend the source meaning.

Constraints: do not add claims, metrics, dates, credentials, skills, or accomplishments absent from the resume. Do not omit material context in a way that changes a claim. Keep the content concise and readable; do not add visual embellishments or new technology.

Verify: check each profile and experience statement against the PDF, including names, dates, metrics, and outcomes; confirm experience follows the introduction and precedes the remaining resume sections; confirm section navigation still works. Report any PDF text that is unreadable rather than guessing.
```

### Increment 2.2 — Add skills and education

```text
Read REQUIREMENTS.md and inspect the current index.html. Read Sample_Candidate_Resume.pdf and use it as the sole factual source. Build on the working page without changing its existing identity, actions, navigation, profile, or experience.

Objective: populate the existing skills and education sections using only information explicitly present in the resume. Group information for easy recruiter scanning without implying proficiency levels, credentials, or relationships that the source does not state.

Constraints: do not infer skills from job descriptions, add degrees or dates, normalize details in a way that changes their meaning, or create unsupported categories. Keep semantic headings and the existing section IDs stable. Do not add scripts, dependencies, or new pages.

Verify: compare every listed skill and education detail with the PDF; confirm the Skills and Education navigation links still land on the right sections; confirm the existing experience and contact/download links remain unchanged and functional by inspection.
```

### Increment 2.3 — Add highlights, projects, and sample publications

```text
Read REQUIREMENTS.md and inspect the current page. Read Sample_Candidate_Resume.pdf and use it as the only factual source. Build on the current working site and preserve all existing section IDs, navigation, identity, and actions.

Objective: populate the existing highlights, projects, and publications sections with the corresponding resume content, including sample publications as identified by the source. Present the material clearly and distinguish projects from publications.

Constraints: include only details stated in the PDF. Do not invent project outcomes, links, publication venues, authors, dates, metrics, or descriptions. Do not turn plain-text references into guessed URLs. Keep the existing sections and navigation intact; do not add another page, scripts, or dependencies.

Verify: trace every statement and detail in these three sections to the PDF; confirm sample publications are not presented as independently verified credentials; confirm each section is reachable from navigation and earlier content and calls to action remain present.
```

### Increment 3.1 — Apply the visual system and responsive layout

```text
Read REQUIREMENTS.md and inspect the complete current index.html and styles.css. Build on the existing static implementation; preserve all content, links, and section IDs.

Objective: style the complete page as a clean, restrained, recruiter-friendly portfolio with a professional blue-forward palette. Make the candidate identity, role, fiction notice, and email action clear in the first view; keep experience visually prominent. Add a comfortable text measure, clear heading hierarchy, consistent spacing, and responsive layout for mobile and desktop.

Constraints: use CSS in styles.css and native/system fonts. Do not add a portrait, fabricated imagery, external services, frameworks, JavaScript, dependencies, or unnecessary decoration. Maintain readable contrast, visible keyboard focus, and usable navigation at narrow widths. Do not hide or reorder content in a way that harms access or recruiter scanning.

Verify: inspect the CSS and HTML for preserved content and working anchor targets. If browser preview is available, inspect the page at a narrow mobile viewport and a desktop viewport, and test the navigation, focus visibility, and text legibility. Fix any overflow or obscured content found. State exactly which viewport and interaction checks were actually performed.
```

### Increment 3.2 — Run acceptance checks and polish

```text
Read REQUIREMENTS.md and inspect the finished index.html, styles.css, and repository contents. Read Sample_Candidate_Resume.pdf for any final content comparison. Do not redesign the site or add new features.

Objective: perform a focused final acceptance pass and fix only defects that prevent the existing implementation from meeting REQUIREMENTS.md.

Check: all requested resume sections are present; professional experience leads the substantive content; all claims are traceable to the PDF; the fictional-demo notice is visible near the top and next to the PDF download; the email action uses the resume address; the website link is exactly https://samplecandidate.github.io; the PDF download points to ./Sample_Candidate_Resume.pdf; and section links target the correct sections. Check semantic structure, keyboard operability, visible focus, contrast, and responsive usability on mobile and desktop.

Constraints: retain the plain static HTML/CSS approach, avoid new dependencies and unrelated edits, and do not publish or push anything. Do not claim browser, visual, or runtime checks unless performed.

Verify: inspect the changed files and confirm the PDF is present at the linked path. Use the available HTML validation or browser preview for checks it supports; if a browser is available, test keyboard navigation and inspect both a mobile-sized and desktop-sized viewport. Report checks that could not be performed instead of assuming they passed. Summarize any fixes and the actual verification evidence.
```
