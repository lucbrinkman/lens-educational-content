# Lens Academy Educational Content

Course modules and lessons for the Lens Academy AI Safety curriculum.



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

( :  is replaced in the notes with # )

#### Module note
Any number of 
\# Text:
\# Learning Outcome:

Example:
```md
# Text:
content::
Lorum Ipsum

# Learning Outcome:
[[link to Learning Outcome note]]

# Learning Outcome:
[[link to 2nd learning outcome note]]

```

#### Learning Outcome note
```md
## Test:
[[Link to Test note]]
## Lens:
[[link to Lens note]]
## Lens: (optional)
[[Link to 2nd Lens note]]
```

#### Lens note
```md
### Video: or Article:
source:: [[link to video_transcript or article note]]

#### Text
content::
Lorum Ipsum

#### Video-excerpt or Article-excerpt
(optional) from::
(optional) to::

#### Text
content::
Lorum Ipsum

#### Chat
instructions::
You're an AI tutor
```


### Repo folder structure
```
├── modules/          # Lesson content (markdown)
├── courses/          # Course definitions (which lessons, in what order)
├── articles/         # Article source texts
└── video_transcripts/ # Video transcript source texts
```

## Validation

All modules and courses are validated on PR:
- Required frontmatter (`slug`, `title`)
- Valid section types (`Video`, `Article`, `Text`, `Chat`)
- Required fields per section type
- Wiki-links must use relative paths (`[[../video_transcripts/...]]`)
- Wiki-link targets must exist

foo bar

test edit 2
