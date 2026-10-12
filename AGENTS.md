# AGENTS

## Project purpose
- Build a polished, single-page portfolio for the fictional Sample Candidate using the supplied resume as the only factual source.
- Publish as a static GitHub Pages site from the repository root at https://samplecandidate.github.io.

## Architecture and stack
- Stack: plain HTML and CSS only; no framework, build step, JavaScript, backend, dependencies, or extra pages.
- Entry points: index.html and styles.css at the repository root.
- Keep the supplied Sample_Candidate_Resume.pdf in place as the downloadable source resume.
- Use semantic sections with stable IDs and in-page navigation; use relative local paths so the site works at the root GitHub Pages URL.
- Use native HTML links for email, the website, and the PDF download.

## Factual-content constraints
- Read the PDF before writing any resume-derived content; treat it as the sole factual source.
- Display the name Sample Candidate and role AI / Software Engineer, and clearly label the portfolio and resume as fictional near the top of the page.
- Include profile, experience, skills, education, highlights, selected projects, and sample publications only as supported by the resume.
- Do not invent or imply employers, dates, credentials, skills, metrics, or achievements absent from the resume.
- Rephrase in first person only when it preserves the resume’s exact meaning.

## Important development constraints
- Do not add a contact form, backend, custom domain, or additional pages.
- Keep the email action primary and the resume PDF download secondary.
- Preserve the PDF as the downloadable source resume and do not move or modify unrelated files.
- Keep the implementation simple, responsive, accessible, and text-focused; no imagery or external asset services.
- Use semantic HTML landmarks, headings, keyboard-visible focus states, and readable contrast.

## Verification expectations
- Verify all claims against the resume before finalizing any content.
- Check that navigation anchors match their section IDs exactly, the PDF link resolves to ./Sample_Candidate_Resume.pdf, and the website link is exactly https://samplecandidate.github.io.
- Confirm the page remains static, no scripts or dependencies were added, and core accessibility and mobile/desktop behavior remain intact.
- If an HTML validator or browser check is available, run it and report the observed result; do not claim checks that were not performed.

## BUILD.md workflow
- BUILD.md is the project tracker.
- CURRENT lists the active increment and its verification status.
- NEXT lists the pending increments in order.
- COMPLETED tracks finished work once verification is complete.
- Update the relevant status only when the increment has been verified against the requirements and the source resume.

## Scope Discipline

The CURRENT increment is a hard implementation boundary.

- Implement only requirements explicitly requested by the current increment.
- Do not implement, scaffold, anticipate, or prepare code for future increments.
- Do not add components, styles, JavaScript, files, dependencies, or content merely because they will be useful later.
- Existing requirements and DESIGN.md describe the overall project, but they do not authorize implementing future work.
- If the current increment does not request something, leave it for a later increment.
- Prefer the smallest change that completely satisfies the current increment.

## Evidence and Trust Rules

Never claim that a file was created, edited, tested, or verified unless the corresponding tool action actually succeeded.

Before marking an increment complete:

1. Confirm every required file exists by reading it with the available file tools.
2. Inspect the actual resulting content, not previously generated chat text.
3. Perform only verification that can actually be observed with available tools.
4. Never claim browser, console, network, visual, or runtime verification unless that check was actually performed.
5. If a required tool call fails or is unavailable, report the increment as BLOCKED. Do not infer success.
6. Never update BUILD.md to COMPLETED without evidence that the implementation exists and satisfies the increment.
7. The CURRENT increment is a hard scope boundary. Do not implement future increments.

## Safety Boundaries

- Work only inside this repository.
- Do not delete files or directories outside this repository.
- Do not install system-level software.
- Do not install packages unless they are genuinely required by the application.
- Do not change Git user.name or Git user.email.
- Local Git commits are allowed as project checkpoints.
- Do not push to a remote repository unless explicitly authorized.
- Never expose or commit passwords, tokens, API keys, or other secrets.
- Ask before destructive operations or actions that modify external systems or accounts.
