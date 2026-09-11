# Project Guidelines

This file defines the default working agreement for coding agents in this repository. Keep it concise, current, and committed to version control. Add narrower `AGENTS.md` files in subdirectories only when those areas genuinely need different rules.

## Project context

Before making changes, inspect the repository and determine:

- the framework, language, package manager, and runtime versions;
- the relevant scripts in `package.json` or equivalent task files;
- where pages, components, content, configuration, styles, tests, and static assets live;
- the existing naming, formatting, design-system, and testing conventions.

Prefer repository evidence over assumptions. If this section has not been customized, infer the setup from the codebase and continue without blocking on routine questions.

When this template is added to a project, record any non-obvious facts below:

- **Primary stack:** _Add when known_
- **Package manager:** _Add when known_
- **Development command:** _Add when known_
- **Required validation:** _Add when known_
- **Deployment target:** _Add when known_
- **Important directories or constraints:** _Add when known_

## Working principles

- Make the smallest coherent change that fully solves the request.
- Preserve existing behavior unless the requested change intentionally alters it.
- Follow established project patterns before introducing new abstractions or tools.
- Fix root causes rather than masking symptoms.
- Keep code simple, readable, and maintainable. Avoid speculative architecture and premature optimization.
- Reuse existing components, utilities, styles, tokens, and dependencies before creating alternatives.
- Do not modify unrelated files or undo changes you did not create.
- If requirements are ambiguous, inspect the surrounding implementation first. Ask only when different interpretations would materially change the result.

## File organization

- Put code, content, configuration, tests, and assets in their established project locations.
- Keep reusable UI in components and page-specific implementation close to the page or feature that owns it.
- Keep structured content in the project’s content or data layer rather than embedding large datasets in components.
- Store repeatable content records—such as publications, projects, team members, testimonials, FAQs, or resource links—in a separate typed content collection or data module, even when the initial list is small. Render those records from components instead of hardcoding them in page markup so they remain easy to update, validate, sort, and reuse; follow the framework’s established content system when one exists.
- Centralize shared constants and configuration; do not duplicate magic values across files.
- Prefer small, focused modules with clear ownership. Split files when responsibilities become genuinely distinct, not solely to reduce line count.
- Preserve public APIs and directory structure unless a change is necessary and its impact is understood.

## TypeScript and JavaScript

- Use TypeScript when the project supports it and preserve or improve strictness.
- Prefer explicit domain types and narrow unions over `any`, unchecked casts, or overly broad object shapes.
- Validate data at external boundaries such as APIs, forms, environment variables, CMS content, and persisted storage.
- Handle loading, empty, success, and error states where applicable.
- Avoid hidden side effects, mutable global state, and duplicated business logic.
- Use the project’s existing import aliases, module conventions, formatter, and linter.
- Do not suppress type or lint errors without documenting a concrete reason.

## Framework conventions

- Follow the framework’s current patterns already present in the repository.
- Keep server-only code and secrets out of browser bundles.
- Prefer server rendering and static output where they meet the requirement; add client-side JavaScript only for real interactivity.
- For Astro projects, keep components static by default, use hydration directives deliberately, and place content in content collections when appropriate.
- For React or similar UI frameworks, keep components focused, avoid unnecessary state and effects, and prefer derived values over synchronized state.
- Do not replace the router, state-management approach, styling system, build tool, or content layer without explicit approval.

## UI and styling

- Match the existing visual language before inventing new patterns.
- Reuse design tokens for color, typography, spacing, radii, shadows, and motion. Introduce new tokens only when they represent a reusable design decision.
- Build responsive layouts from the smallest viewport upward and verify common mobile, tablet, and desktop widths.
- Avoid brittle fixed dimensions when content or viewport size can vary.
- Preserve clear visual hierarchy, readable line lengths, consistent spacing, and predictable interaction states.
- Provide intentional hover, focus, active, disabled, loading, empty, and error states where relevant.
- Respect `prefers-reduced-motion`; motion should clarify interaction rather than distract.
- Avoid one-off CSS overrides, excessive specificity, and `!important` unless required to work around a documented constraint.

## Accessibility

- Target WCAG 2.2 AA for user-facing interfaces.
- Use semantic HTML before ARIA. Add ARIA only when native semantics are insufficient.
- Ensure all interactive elements work with a keyboard and have a visible focus state.
- Use real buttons and links for actions and navigation; do not make non-interactive elements behave like controls.
- Give form controls programmatic labels, useful instructions, and accessible error messages.
- Provide meaningful alternative text for informative images and empty alt text for decorative images.
- Maintain sufficient color contrast and never rely on color alone to communicate meaning.
- Preserve logical heading order, landmark structure, reading order, and adequate target sizes.
- Announce important asynchronous updates when screen-reader users would otherwise miss them.

## Content, SEO, and localization

- Keep user-facing copy clear, concise, and consistent with the project’s voice.
- Do not invent factual claims, testimonials, metrics, legal text, contact details, or business information.
- Preserve content separately from presentation when the project has a content layer.
- Use a single clear page title and description, a logical heading hierarchy, canonical metadata where needed, and meaningful link text.
- Preserve structured data, social metadata, robots rules, and sitemap behavior when changing page templates.
- Do not concatenate user-facing sentences in ways that make future localization difficult.

## Performance

- Prefer the simplest solution that meets the experience requirement without unnecessary client JavaScript.
- Optimize images with appropriate dimensions, formats, responsive sources, and lazy loading where suitable; avoid layout shifts.
- Keep critical UI responsive and avoid expensive work during render, scroll, resize, or input events.
- Do not add a dependency for functionality that is small, stable, and straightforward to implement locally.
- Treat material bundle-size, rendering, query-count, and asset-weight regressions as defects.
- Measure before making complex performance optimizations.

## Security and privacy

- Never commit secrets, credentials, private keys, access tokens, or real customer data.
- Keep secrets in the project’s established environment mechanism and document required variable names in the appropriate example file.
- Treat all external input as untrusted. Validate, sanitize, encode, or parameterize it at the correct boundary.
- Do not weaken authentication, authorization, content-security policies, validation, or dependency safeguards to make a feature work.
- Avoid logging sensitive or personally identifiable information.
- Use third-party services and tracking only when they are already approved for the project or explicitly requested.

## Dependencies and configuration

- Reuse installed packages and platform capabilities before adding dependencies.
- Add a production dependency only when it provides clear value over a small local implementation and is compatible with the project.
- Do not change package managers, lockfile formats, runtime versions, compiler settings, or deployment configuration incidentally.
- Keep lockfile changes scoped to intentional dependency changes.
- Explain any new dependency, migration, or significant configuration change in the final handoff.

## Validation

- Validate every change in proportion to its risk.
- Use the repository’s own scripts and package manager. Do not guess commands when they can be discovered.
- At minimum, run the relevant formatter or formatting check, lint, type check, and focused tests when available.
- Run the production build for changes that can affect compilation, routing, rendering, content schemas, or deployment.
- For UI changes, inspect the result at relevant viewport sizes and check keyboard interaction, focus states, overflow, and obvious accessibility issues.
- Add or update tests for changed behavior and regressions when the repository has a testing pattern.
- Do not claim a check passed unless it was actually run. Report skipped or failing checks with the reason and relevant error.

## Documentation

- Update documentation when setup, commands, environment variables, architecture, public APIs, or user-visible behavior changes.
- Write comments for intent, constraints, or non-obvious tradeoffs—not to narrate self-explanatory code.
- Keep examples executable and paths and commands accurate.
- Record durable project-specific conventions in this file instead of relying on chat history.

## Git and change management

- Review the working tree before editing and preserve unrelated user changes.
- Keep diffs focused; do not reformat unrelated files.
- Do not commit, push, create branches, open pull requests, deploy, or publish unless explicitly requested.
- Never use destructive Git operations or rewrite shared history without explicit approval.
- When asked to commit, use a concise message that describes the user-visible or architectural outcome.

## Completion standard

Before finishing:

- confirm the requested outcome is complete rather than only partially implemented;
- review the diff for accidental, generated, debug, secret, or unrelated changes;
- run the relevant validation commands;
- verify documentation and examples remain accurate;
- summarize what changed, what was validated, and any remaining risks or follow-up work.
