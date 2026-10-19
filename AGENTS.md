<!-- LOVABLE:BEGIN -->
> [!IMPORTANT]
> This project is connected to [Lovable](https://lovable.dev). Avoid rewriting
> published git history — force pushing, or rebasing/amending/squashing commits
> that are already pushed — as it rewrites history on Lovable's side and the
> user will likely lose their project history.
>
> Commits you push to the connected branch sync back to Lovable and show up in
> the editor, so keep the branch in a working state.
<!-- LOVABLE:END -->

## UYUM architecture
- Questionnaire items live in `src/content/items.json` (fixed IDs 1–45, tr/fa/en); all other copy lives in per-language JSON under `src/content/` with identical structure — keep structures in sync across languages so the UI never falls back.
- Scoring is deterministic in `src/lib/engine.ts` (covered by `engine.test.ts`); never add an overall compatibility score or AI-decided outcomes.
- Assessment state is a flat answers map persisted to localStorage (pre-product simulation); a real two-device flow would need a backend.
- Assessment progression is centralized in `src/lib/assessment-navigation.ts` and tested separately from scoring; safety flags select safety content without trapping submitted partners on a disabled navigation button.
