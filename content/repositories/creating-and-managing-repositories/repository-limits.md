---
title: Repository limits
intro: 'Learn about limitations for repositories.'
versions:
  fpt: '*'
  ghes: '*'
  ghec: '*'
topics:
  - Repositories
---

Certain types of repository resources can be quite large, requiring excessive processing on {% data variables.product.github %}. Because of this, limits are set to ensure requests complete in a reasonable amount of time.

Most of the limits below affect both {% data variables.product.github %} and the API.

## Text limits

{% data variables.product.prodname_dotcom %} displays formatted previews of some files, such as Markdown and Mermaid diagrams. {% data variables.product.prodname_dotcom %} always attempts to render these previews if the files are small (generally less than 2 MB), but more complex files may time out and either fall back to plain text or not be displayed at all. These files are always available in their raw formats, which are served through `{% data variables.product.raw_github_com %}`; for example, `https://{% data variables.product.raw_github_com %}/octocat/Spoon-Knife/master/index.html`. Click the **Raw** button to get the raw URL for a file.

## Diff limits

Because diffs can become very large, we impose these limits on diffs for commits, pull requests, and compare views:

* In a pull request, no total diff may exceed _20,000 lines that you can load_ or _1 MB_ of raw diff data.
* No single file's diff may exceed _20,000 lines that you can load_ or _500 KB_ of raw diff data. _Four hundred lines_ and _20 KB_ are automatically loaded for a single file.
* The maximum number of files in a single diff is limited to _300_.
* The maximum number of renderable files (such as images, PDFs, and GeoJSON files) in a single diff is limited to _25_.

Some portions of a limited diff may be displayed, but anything exceeding the limit is not shown.

## Commit listings limits

The compare view and pull requests pages display a list of commits between the `base` and `head` revisions. These lists are limited to **250** commits. If they exceed that limit, a note indicates that additional commits are present (but they're not shown).

The maximum count of commits displayed on the Commits tab is **10,000**. Use other tools such as `git rev-list --count mybranch` to count and enumerate a high volume of commits when needed.

{% ifversion fpt or ghec or ghes > 3.16 %}

## Rebase limits

Merging a pull request using the "Rebase and merge" option is limited to **100** commits.  If you have a pull request with more than 100 commits, you need to create a merge commit, squash and merge, or split the commits up into multiple pull requests.

{% endif %}

## Organization and account limits

Organizations and accounts may not exceed **100,000** repositories. When an account surpasses **50,000** repositories, a banner will appear, noting the approaching limit. Additionally, administrators will receive email notifications, and the audit log will update every additional 5,000 repositories created. See [AUTOTITLE](/repositories/creating-and-managing-repositories/about-repositories#about-repository-ownership).

## Integrations and {% data variables.product.prodname_github_apps %}

When building an integration on {% data variables.product.github %}, store user-generated data in their own {% data variables.product.github %} accounts rather than centralizing it in your account. This ensures users retain full control over their work and helps you avoid exceeding repository limits.
