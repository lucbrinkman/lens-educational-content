# Lens Academy Educational Content

Course modules and lessons for the Lens Academy AI Safety curriculum.⁠

## Read-only:
- Staging (automatically synced from Obsidian with 10s delay): https://github.com/lucbrinkman/lens-educational-content/tree/staging
- Production: https://github.com/lucbrinkman/lens-educational-content/tree/main

## Workflow

```
Obsidian → Relay → staging branch → PR → main branch → Production
```

1. **Edit in Obsidian** - All content is authored in Obsidian
2. **Auto-sync to staging** - Relay automatically syncs changes to the `staging` branch
	- The staging branch is used directly by our staging website. Changed made in Obsidian should be reflected on the website after 20s or so.
3. **Create PR** - Manually open a pull request from `staging` to `main`
4. **Validation** - GitHub Actions validates lesson format and wiki-links
5. **Merge to main** - Once checks pass, squash and merge to `main`
6. **Production** - The `main` branch is used directly by the production website..

## Important

- **Never commit directly to the Lens Educational Content repo on Github** - All changes must come through Relay.
- That includes pushing to the staging branch and any other branches.

## Structure
### Course structure
**Course** - list of
: **Module** - list of
:: **Learning outcome** - where each has three params
::: 1. Name of outcome
::: 2. **Test** - how we'll assess whether the person learned the objective
::: 3. **Lens** - a learning flow which has
:::: A. One **Resource** {article, video, a section from one of them, or a little app to teach something}
:::: B. **Prompt(s)** for the AI tutor to talk to the student (optional)
:::: C. Some extra bits like framing texts etc (optional)

This is implemented as shown below:
#### Modules
e.g. `Lens Educational Content/Modules/module.md`
Required frontmatter: `slug`, `title`

Any number of
\# Text Page:
\# Learning Outcome:

Wiki-links must use relative paths (e.g. `[[../video_transcripts/...]]`) and targets must exist.

Example:
```md
# Text Page:
content::
Lorum Ipsum

# Learning Outcome:
[[link to Learning Outcome note]]

# Learning Outcome:
[[link to 2nd learning outcome note]]
```

#### Learning Outcomes
e.g. `Lens Educational Content/Learning Outcomes/learning-outcome.md`

Any number of
\## Test:
\## Lens:

Example:
```md
## Test:
[[Link to Test note]]

## Lens:
[[link to Lens note]]

## Lens: (optional)
[[Link to 2nd Lens note]]
```

#### Lenses
e.g. `Lens Educational Content/Lenses/lens.md`

Valid section types: `Video`, `Article`, `Text`, `Chat`

Any number of
\### Video: or Article:
\#### Text:
\#### Video-excerpt or Article-excerpt:
\#### Chat:

Each section type has required fields (see example below).

Example:
```md
### Video: or Article:
source:: [[link to video_transcript or article note]]

#### Text
content::
Lorum Ipsum

#### Video-excerpt or Article-excerpt
(optional) from:: 1:18
(optional) to:: 15:38

#### Text
content::
Lorum Ipsum

#### Chat
instructions::
You're an AI tutor
```

test edit via normal Edit tool (file opened in Obsidian)

