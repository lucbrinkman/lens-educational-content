# Lens Academy Educational Content

Course modules and lessons for the Lens Academy AI Safety curriculum.

## Workflow

```
Obsidian → Relay → staging branch → PR → main branch → Production
```

1. **Edit in Obsidian** - All content is authored in Obsidian
2. **Auto-sync to staging** - Relay automatically syncs changes to the `staging` branch
	- The staging branch is used directly by our staging website. Changed made in Obsidian should be reflected on the website after 20s or so. ( #todo: add webhooks that make this actually so)
3. **Create PR** - Manually open a pull request from `staging` to `main`
4. **Validation** - GitHub Actions validates lesson format and wiki-links
5. **Merge to main** - Once checks pass, squash and merge to `main`
6. **Production** - The `main` branch is used directly by the production website

## Important

- **Never commit directly to the Lens Educational Content repo on Github** - All changes must come through Relay.
- That includes pushing to the staging branch and any other branches.

## Structure

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
