# Tey Labs Package Conventions

How Tey Labs packages are named, documented, tested and released. New packages start from these, and existing ones are brought in line as they are touched. [tey/laravel-ddd](https://github.com/teylabs/laravel-ddd) is the reference package.

## Identity

- **Composer:** `tey/<package>`. **GitHub:** `teylabs/<package>`. **PHP namespace:** `Tey\<Package>`.
- **Author:** Jasper Tey, `jasper@teylabs.com`, in `composer.json` and in commits.
- **License:** MIT. `LICENSE.md` reads `Copyright (c) Jasper Tey <jasper@teylabs.com>`.
- **Links** use the canonical `https://github.com/teylabs/<package>` form.
- **No AI attribution** in commits, pull requests, issues or releases.

## Repository Setup

| Item | Convention |
| --- | --- |
| Default branch | `main`, with auto-delete of merged branches |
| Merging | Squash merge, with a clean subject and body |
| Workflows | `run-tests` (PHP × Laravel matrix, Ubuntu and Windows, lowest and stable), `phpstan`, `fix-php-code-style-issues`, `dependabot-auto-merge` |
| Dependabot | GitHub Actions, weekly |
| Security | GitHub private vulnerability reporting on; policy from this repository |
| Community | Discussions on (Q&A and Ideas); issues for reproducible bugs |
| Issue templates | `config.yml` with links to the package's Discussions, security policy and issues; a bug report form |
| Shared files | `SECURITY.md`, `CONTRIBUTING.md` and `FUNDING.yml` come from this repository; don't copy them into packages |

## Tooling

- Tests use Pest on Orchestra Testbench. Static analysis uses PHPStan with Larastan. Code style uses Pint (Laravel preset).
- Composer scripts are `test`, `test-coverage`, `analyse`, `format` and `lint`.
- Supported PHP and Laravel ranges match across packages where possible. A package states its range once, under Installation.

## Writing for Developers

Everything published under Tey Labs (READMEs, docs, changelogs, release notes, issue and discussion replies) is written for a Laravel developer deciding whether a package solves their problem, and then using it. The test: **a developer reads it, gets it, and wants to try it.** The register is Laravel's own documentation.

### Show, Then Explain

1. **Code first.** Show a thing before explaining it. If a section has three paragraphs before its first code block, restructure it.
2. **Snippet, then its result.** What a command or snippet produces sits directly beneath it: the generated file, the folder tree, the output. The result is of *that* snippet, not a more advanced one.
3. **Answer "what do I have when I'm done?" in the first two lines** of every page and every major section.
4. **One obvious path in guides; everything else in reference.** A guide shows the common way. Alternatives, edge cases and every option belong in reference material that the guide links to.

### Words

5. **The reader's vocabulary, not the package's.** Use the industry terms a developer already knows (*modular monolith*, *feature folders*, *activity feed*, *domain*, *namespace*). A term the package coins is introduced once, in plain words, before it is used, and only if the reader needs it to use the package. Internal names (engine terms, class roles, milestone codes) stay out.
6. **Short declarative sentences.** One idea each. Why the API is shaped a certain way usually gets cut.
7. **Say what the code does.** Plain verbs, no anthropomorphism: the package doesn't "refuse", "want" or "know". Write "`mod:model` exits with an error when the file exists", not "mod refuses".
8. **No selling, autobiography or meta-commentary in docs.** Make it look easy by showing it; don't claim it is easy. Don't write about the page itself ("read this once", "the useful column"). Don't warn about confusion: if two terms are easy to mix up, a heading explains the difference.
9. **Describe the current release only.** No history, removed APIs, former names or "new in" notes in the body. Those live in `CHANGELOG.md` and `UPGRADING.md`. Pre-1.0 status is one callout near the top, not a theme.
10. **Canadian spelling** for "-our" words: behaviour, colour, favour. "-ize" is fine (organize, customize). Code identifiers and quoted framework names keep their own spelling.
11. **Name things consistently.** The package is called by its name, never "core" or "the engine". One term per concept across the whole README and docs.

### Code Examples

12. **Copyable code is the strictest thing on the page.** Every snippet runs as written in a fresh Laravel app, and is checked that way before release. An example never contradicts a rule stated elsewhere.
13. **Every snippet says where it goes.** A file comment on the first line (`// app/Providers/AppServiceProvider.php`), or a sentence just before the block. A class snippet opens with `<?php`, its namespace and its `use` block. A facade call shows its `use` line.
14. **Shell examples** go in `bash` blocks, with `#` comments and `# ->` arrows for results. Folder trees go in plain `text` blocks:

    ```bash
    php artisan ddd:model Invoicing:Invoice
    # -> src/Domain/Invoicing/Models/Invoice.php
    ```

15. **Small, realistic examples.** One idea per snippet. Names come from ordinary apps (`Invoice`, `Billing`, `User`), never `Foo` or `Probe`. A long listing is split into steps rather than marked up.
16. **A caveat lives where the mistake is made:** as a comment inside the snippet, or a trailing `#` on a command, not in a paragraph elsewhere.

### Structure

17. **Headings form a table of contents.** Read top to bottom, the headings alone describe the page. Headings are task-shaped ("Defining a Layout", "Caching Discovery") or precise capability names, in **Title Case**, never clever or sentence-shaped, and never numbered.
18. **Tables for anything enumerable:** options, layouts, commands, comparisons. Lists for short inventories. Avoid walls of bullets.
19. **Say it once.** Each fact has one home; other places link to it.
20. **Callouts are rare.** GitHub and Laravel syntax: `> [!NOTE]` for a prerequisite or limit worth noticing while skimming; `> [!WARNING]` only for a mistake that is silent (no error), unguarded (no tool catches it) and in hand (the reader is about to run that exact code).

## README

The README is the package's landing page on GitHub and Packagist. Within one screen, a developer should know **what the package does, what problem it solves for them, and what using it looks like.**

### Landing Section

In this order:

1. **Hero image** (optional): only if it shows the package working, such as a terminal recording or a rendered result. Never decoration.
2. **Title:** `# <Name>: <What It Is> for Laravel`, using the reader's vocabulary, for example "Mod: Modular Development for Laravel". A colon, not a dash: it can be typed on any keyboard.
3. **Badges** (flat-square): Packagist version, tests, code style, total downloads.
4. **Pitch:** two or three sentences. The problem in the reader's words, then what the package does about it. It must stand on its own, without the title: it is what search results, Packagist and link previews show. Start with the package name ("Mod is …"). Then say why a reader needs it: the everyday problem, in plain words, before the solution.
5. **Show it:** the smallest example of the package working, with its result beneath.
6. **Pre-1.0 notice**, when it applies: one `> [!NOTE]`.
7. **Highlights** (optional): three to five bullets, each a capability in plain words, each linking to its section.
8. **Byline** (optional): once a package has meaningful outside contributors, "Built by [Jasper Tey](https://github.com/jaspertey) at [Tey Labs](https://teylabs.com), and made better by [our contributors](…/graphs/contributors)." New and solo-maintained packages leave it out; Credits covers attribution.

**Origin story** (optional): a README is the package's splash page, so it may say where the package came from, in one short paragraph after the landing section. It never appears in docs pages. It follows the shape of the Tey Labs talk abstracts: start from something the reader recognizes, say plainly what fell short (first person is fine), then name what this package is as the result. One paragraph, no history of releases, no selling. Example:

> Mod grew out of building [laravel-ddd](https://github.com/teylabs/laravel-ddd). Most of that package turned out to be plumbing that had little to do with DDD: making Laravel's `make:*` generators write outside `app/`, discovering providers, commands and listeners wherever they live, and keeping a model's factory and policy beside it. Mod is that plumbing, rebuilt from those lessons as its own package, for any layout.

### Body

Sections in this order, leaving out any that don't apply. A **Contents** list goes after the landing section once the README needs one.

| Section | Holds |
| --- | --- |
| Installation | Requirements sentence, `composer require`, upgrade guide link, optional install or publish command |
| Quick Start | The shortest path to something working, with its result |
| Usage | Task-shaped sections, one per thing a developer does |
| Configuration | The config file's options in a table, or a link to the reference |
| Production | Caching, deployment, anything to run on release |
| FAQ | The questions newcomers actually ask, including "How is this different from …?", answered fairly |
| Documentation | Links to `docs/` or the docs site, when they exist |
| Testing | How to run the package's own tests |
| Changelog | Link to `CHANGELOG.md` |
| Contributing | Link to the shared contributing guide |
| Security Vulnerabilities | Link to the security policy |
| Credits | Jasper Tey / Tey Labs, and all contributors |
| License | MIT, with a link to `LICENSE.md` |

Past about 400 lines, reference material moves into `docs/` (for example `docs/configuration.md` and `docs/extending.md`), and the README links to it. Material for people building on the package (extension points, hooks) always lives in `docs/`, not the README.

## Changelog

`CHANGELOG.md`, newest first:

```markdown
## [1.2.3] - 2026-10-08

### Added
### Fixed
### Changed
### Docs
### Chore
### Upgrade notes
```

- Sections appear in that order, and only when they have entries.
- Entries describe what changed for someone using the package. Repository housekeeping (license holder, CI tweaks) stays out unless it affects them.

## Commits and Pull Requests

- Subjects are short and imperative. A conventional prefix (`feat:`, `fix:`, `docs:`, `test:`, `chore:`, `ci:`, `build:`) is welcome.
- Messages are written for public readers: no private tracker ids, internal codenames or local paths.
- One concern per pull request. The description says what changed and why, and how it was tested.

## Releases

1. Merge the pull requests for the release.
2. Commit `Release x.y.z` on `main`: date the `## [x.y.z]` CHANGELOG heading and trim it to user-facing entries.
3. Tag `vx.y.z` (lightweight) on that commit and push the tag.
4. Publish a GitHub release titled `vx.y.z`, marked Latest. Its notes are:
   - an optional `## Headline` and short intro, for feature releases;
   - the CHANGELOG section, verbatim;
   - `---`;
   - GitHub's generated "What's Changed" list and its Full Changelog link.

   A package whose `update-changelog` workflow copies release notes into `CHANGELOG.md` publishes only the generated list.
5. Packagist updates from the GitHub webhook.

Versions follow semantic versioning. Before 1.0, minor releases may change the API, and the README says so.
