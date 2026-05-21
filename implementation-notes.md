# Implementation Notes

## Repository location

- The session started in `C:\Users\gianm\Dropbox\sbmp_spain`, which is the `gianmarcoruzzier1/sbmp_spain` repository on `master`.
- The requested Pages repository, `gianmarcoruzzier1/jmp_draft`, was not present locally under Dropbox.
- I cloned `https://github.com/gianmarcoruzzier1/jmp_draft.git` branch `gh-pages` to `C:\tmp\jmp_draft-gh-pages` and made the implementation there.

## Specification source

- The objective named `google_scholar_research_page_canonicalization_plan_updated.md`.
- The available local specification file was `google_scholar_research_page_canonicalization_plan_goal_updated.md`; its contents matched the requested canonicalization plan and were used as the authoritative implementation specification.

## Deterministic choices

- `specialized-banks-monetary-policy.pdf` is an exact copy of `draft_sbmp_gr_webpage.pdf`.
- `draft_sbmp_gr_webpage.pdf` was retained unchanged for backward compatibility.
- The abstract in `index.html` was copied from the current PDF text extracted with `pdftotext`.
- `citation_publication_date` was set to `2025/09`, matching the plan and the PDF text: "This version: September 2025."
- `sitemap.xml` and `robots.txt` were added because they were strongly recommended in the plan and absent from the repository.

## Tradeoffs

- I did not alter the old PDF because the plan says not to rewrite paper content and to leave the old PDF unchanged if source regeneration is unavailable.
- I did not add redirects because GitHub Pages cannot issue a true HTTP 301 for this old PDF without additional hosting configuration, and the plan requires the old PDF URL to remain available.
- I initially did not commit, push, or deploy until the user explicitly authorized it. After authorization, I committed and pushed the `gh-pages` changes.
- I did not scrape Google Scholar or edit Google Sites.
- The plan's validation commands were translated to PowerShell equivalents where needed because this session is running in PowerShell on Windows.
- A Playwright render check was attempted through the available Node runtime, but `playwright` is not installed there. I did not install new browser dependencies because the requested success checks are file and metadata based.

## Live URL check

- Before deployment, `curl.exe -I https://gianmarcoruzzier1.github.io/jmp_draft/` returned HTTP 200 but served the old PDF auto-redirect page.
- Before deployment, `curl.exe -I https://gianmarcoruzzier1.github.io/jmp_draft/specialized-banks-monetary-policy.pdf` returned HTTP 404 because the new stable PDF had not been deployed.
- After the user authorized commit and push, commit `18985476a2bc12eb54788cb9b3a18e9471d30541` was pushed to `origin/gh-pages`.
- After deployment, `curl.exe -I https://gianmarcoruzzier1.github.io/jmp_draft/` returned HTTP 200 with content length 5687, matching the new canonical landing page.
- After deployment, `curl.exe -I https://gianmarcoruzzier1.github.io/jmp_draft/specialized-banks-monetary-policy.pdf` returned HTTP 200.
- After deployment, `curl.exe -I https://gianmarcoruzzier1.github.io/jmp_draft/draft_sbmp_gr_webpage.pdf` returned HTTP 200, confirming the old PDF URL remains publicly available.
