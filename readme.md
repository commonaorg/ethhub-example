# EthHub
EthHub is an Ethereum information hub - we provide research and resources to learn about Ethereum.

## Content Standard
Our community uses the Commona content repo standard to collaborate on content. Anyone can add to the docs, submit their blog post, add their project to the directory, or add a new content model by submitting a PR. When a maintainer merges a PR, the frontend of EthHub is rebuilt with the newly added content.

## Guidelines
There are also some basic guidelines that need to be followed when contributing to EthHub:
- All pages should have links to supporting sources/documentation and additional resources
- No marketing or sponsored posts
- No promotion of ICOs/token sales
- No inappropriate content

## Contributing to a Commona
### Markdown
All content is formatted as Markdown. Use this [cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet) to understand GitHub-flavored markdown. Each content file should end with `.md`.

### Images and Files
All images or hosted files should be added to the top-level `assets` folder. 

*Example Image Markdown*

```![EthHub logo](./assets/ethhub.png)```

To move up directories from subfolders, use `../` instead of `./` for each level you need to move up. 

### Page Metadata
You can add titles, descriptions, etc. to an item via frontmatter. 

*Raw Example Frontmatter:*

```
---
title: Documenation page title
description: Description of this page's contents.
order: 20
---
```

Each content model type - documentation, blog posts, directory projects, events, jobs, etc - has it's own frontmatter types, which are described in each content model's readme.

### Section Metadata
To designate what order a section should appear in content models like docs and indicate a proper title for a section, add a `metadata.json` file to each section's folder. 

*Example Metadata.json File*

```
{
  "title": "Use Cases",
  "order": 30
}
```

Note: It's recommended to increment orders by 10 so that you can easily add new sections in later. For example, to add a section between a 10-ordered section and a 20-ordered section, you'd set the new section's order to `15`.

----------------------------------------------

Donations: 0xa19fcdad77c1f0fd184689aca88babcf68010347

**DISCLAIMER: EthHub is a completely independent and open-source initiative founded by Ethereum community members. Nothing contained in this Github repository should be considered financial or investment advice - it is for informational purposes only.**
