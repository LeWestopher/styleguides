# UXD PR Review Checklist

## Before the PR
Ensure that your changes are:
+ Accurate to design: 
   - Follow the guidelines in the [pixel perfection](https://github.com/DockYard/styleguides/blob/master/ux-dev/pixel-perfection.md) guide
   - Check that copy is accurate with no spelling errors
   - Complies with any applicable style guide
+ Responsive: Check all target viewport sizes based designs and target devices
+ Accessible:
  - Follow guidelines in the [accessibility](https://github.com/DockYard/styleguides/blob/master/ux-dev/accessibility-a11y.md) guide
  - Test for keyboard usability 
  - Test with screen reader
+ Usable: check all related interactive elements for expected functionality, flows, and states
+ Performant: use the browser's performance monitor panel to assess the impact of your changes
+ Compatible:
  - Check all browsers in support target
  - Use an [HTML validator](https://validator.w3.org/)
  - Optional for browsers/devices have different compatibility needs:
    + progressive enhancements
    + fallbacks
    + polyfills
    + `@supports`

## Making the PR
As a general rule, it is not possible to be _too_ detailed in your PR descriptions. Having a PR description template can prompt you to add helpful information. Here is an example template:

```mkd
### In this PR
+ 

### Design specs
+

### How to review
1. 
2. 
3. 

### ENG Todos
[ ] 

### Visuals
| Before | After |
|---|---|
|image/gif1|image/gif2|
```

### Visually capturing what changed
Here are some simple ways to make your visuals of the changes be as helpful as possible:

+ Always include design specs for reference and comparison
+ Screen shots of the app changes:
  - Capture before and after
  - Consider including markup on the screen shots for clarity
+ Gifs of the app changes:
  - Capture before and after
  - Ideal for PRs where the changes include multiple component states, animations/transitions, or interactions
  - [LICEcap](https://www.cockos.com/licecap/) is a free gif recording tool

If you do record gifs, the repetition of the captured loop can sometimes reveal missed details. 

### Keep your whole team in mind
Your PR reviewer is not the only person who will need the information in the PR. Being detailed and descriptive will help to avoid questions down the road from:
+ anyone looking through past changes 
+ team members who are new to the project
+ team members from disciplines outside of UXD and ENG
+ team members who won't have the code diff for context

Depending on your team's tools and practices, it's possible that not everyone who looks at tracked issues will know how (or have access) to reference PRs for information. In those cases you could consider duplicating your PR information into the issue. Or you might prefer to treat the issue as the single source of truth, putting your write-up there and just pointing to the issue in your PR. Either way, make sure the issue and PR are linked.

## Reviewing PRs
As a reviewer, double check that the PR author followed the practices in the "Before the PR" section, as well as the following UXD style guides where applicable:
+ [HTML](https://github.com/dockyard/styleguides/blob/master/ux-dev/html.md)
+ [Class naming conventions](https://github.com/dockyard/styleguides/blob/master/ux-dev/class-naming-conventions.md)
+ [CSS](https://github.com/dockyard/styleguides/blob/master/ux-dev/css.md)
+ [PostCSS](https://github.com/dockyard/styleguides/blob/master/ux-dev/postcss.md)
+ [SEO](https://github.com/dockyard/styleguides/blob/master/ux-dev/seo.md)
+ [SVG](https://github.com/dockyard/styleguides/blob/master/ux-dev/svg.md)

## Notes
Squashing commits is a good way to keep commit history tidy. Since you may need to make changes during review, it's best to save squashing for after the PR is approved and before it's merged.

Final implementation of these practices depends on client conventions and each issue’s scope, but we encourage everyone to use this as a reference for all work and bring as much consistent structure to a project as possible.
