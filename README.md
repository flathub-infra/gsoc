- [About us](#about-us)
- [Prerequisites](#prerequisites)
- [Project proposals](#project-proposals)
  - [Overview](#overview)
  - [Where to submit proposals](#where-to-submit-proposals)
  - [Proposal outline](#proposal-outline)
- [Ideas for discussion](#ideas-for-discussion)
  - [Replace Flatpak External Data Checker with Renovate](#replace-flatpak-external-data-checker-with-renovate)
  - [Next.js app router](#nextjs-app-router)
  - [Flathub rating system](#flathub-rating-system)
  - [Explore backend CMS](#explore-backend-cms)
  - [Beginner tutorials](#beginner-tutorials)

# About us

We're Flathub, an organization focusing on delivering Flatpak packages to the masses. We're not working on the Flatpak itself, but on things that are related to tooling for the ecosystem and other improvements for users of the Flatpak ecosystem.

Flathub owns multiple parts of code that might be relevant for a GSoC project:

- [Flathub Website](https://github.com/flathub-infra/website/)
- [Flathub Documentation](https://github.com/flathub-infra/documentation)
- [Flatpak external data checker](https://github.com/flathub-infra/flatpak-external-data-checker)
- [Flatpak builder lint](https://github.com/flathub-infra/flatpak-builder-lint)
- [IDE Flatpak Wrapper](https://github.com/flathub-infra/ide-flatpak-wrapper)
- [Electron Sample App](https://github.com/flathub/electron-sample-app)

We also might consider projects that are not directly related to Flathub, but to the Flatpak ecosystem in general. Have a look at the repositories of the [Flatpak organization](https://github.com/flatpak) for inspiration.

If we're selected as a mentoring organization for 2024, students will need to read the overview of a good project proposal, follow the outline for proposals when applying, and review the list of project ideas detailed below. Students are welcome to propose new ideas, not mentioned on the list and are encouraged to be as creative as they like.

If you want to work on any of these, please reach out. We don't care about your gender, skin color, religion, etc. pp.
All are welcome <3

# Prerequisites

Heavily depends on the project, but in general:
Some coding skills, basic familiarity with Git, solid understanding and interest in programming. Ability to quickly understand existing code is beneficial.

# Project proposals

## Overview

Qualifications for a good Summer of Code proposal:

- Discrete, well-defined, modular
- Comprised of a series of measurable sub-goals
- Based on open specs that are available free of charge
- Based on complete specs

An example of a good proposal is the implementation of a new feature or function that is not available yet.

An example of a less desirable proposal is one that's not as measurable, such as refactoring something.

To re-iterate:

- Localized/isolated code projects = good
- Global code refactoring = bad
- A project should have a set of subgoals, so even if the end goal turns out to be too big some of the parts will be of benefit.
- Not too big! This is an important problem when choosing a project, while it is fun to think about solving a grand project, it's not always realistic. It's better to finish a smaller project than to start a grand one.

## Where to submit proposals

In addition to submitting to the [Google Summer of Code website](https://summerofcode.withgoogle.com/), you are highly encouraged to submit your idea/proposal to this repo via issues for discussion. History has shown that students who reach out early to refine and focus the scope of their project are more likely to be selected and successful.

## Proposal outline

Please use this template for your proposal:

```
PROJECT TITLE GOES HERE

    Name:
    Nick in Matrix:
    Summary: A somewhat small but explanatory walkthrough of the project. It should not be overly detailed, just enough to understand the problem trying to be fixed and how this project opts to solve it.
    How will I achieve this: Explain how the project will be done, what technologies are needed, and how to implement them.
    What will the project focus on: Explain what the project will focus on and what the important parts of the project are.
    Benefits: Who will benefit from this project and why. Think about what a user or developer may need or do to benefit from it. Why does it benefit many users.
    Timeline: Set some subgoals and try to put dates to these, this is mostly to help you to not over/under estimate, how long it will take you.
    Goals: What is the goal of the project. A project may not always solve the problem entirely as it may take too much time. Think hard about what can be accomplished during a summer with your skills and deduct from that quite a bit. If the project can't be done after this, perhaps it's better to opt for a smaller one or one with subgoals.
    Requirements: What is needed to complete the project, what code language knowledge, what hardware, etc.
```

# Ideas for discussion

## Replace Flatpak External Data Checker with Renovate

[Flatpak External Data Checker](https://github.com/flathub-infra/flatpak-external-data-checker) is a tool maintained and operated by the Flathub team to help keep apps on Flathub up-to-date. Using annotations in the build manifest for each app, it monitors for new releases of each app and its bundled dependencies, and opens pull requests as needed to update them.

While this tool has been useful in helping Flathub scale to its current size, it has limitations. It tends to open many overlapping pull requests when several modules of an application are updated at once; the build manifest annotations it consumes are somewhat ad-hoc and idiosyncratic; there are limits to what it can check and update; and and so on.

We would like to explore a different approach of using an existing tool for automated dependency updates: [Renovate](https://github.com/renovatebot/renovate). This might improve the control that app developers have over the process; address some of the unusual and unwanted behaviours of the current tool; and reduce the ongoing work to maintain a Flatpak-specific tool.

This project would likely involve working out the best way to add Flatpak manifest support to Renovate, researching the annotations used on Flathub today to ensure that most modules could still be monitored by Renovate, and potentially adding additional data sources to Renovate, such as support for [release-monitoring.org](https://release-monitoring.org/) and GNOME modules, both of which are widely used on Flathub today.

This would likely mean implementing at least two data sources, a [manager](https://github.com/renovatebot/renovate/blob/main/docs/development/adding-a-package-manager.md?rgh-link-date=2024-02-05T23%3A06%3A47Z) and maybe a binary, that writes hashes to flatpak manifests, to lock them.

Possible mentors: @razzeee, @wjt

Difficulty: Hard

Project size: Big

## Next.js app router

As the current next.js app was created with the old [pages router](https://nextjs.org/docs/pages), we want to change to the new [app router](https://nextjs.org/docs/app).

[First we should do all that we can incrementally adopt](https://nextjs.org/docs/app/building-your-application/upgrading/app-router-migration)

Then we need to move everything over, without loosing any features.

Possible mentor: @razzeee

Difficulty: Hard

Project size: Medium

## Flathub rating system

Flathub is a community-driven app store. We would like to have a rating system for apps on Flathub. This would allow users to rate apps, from KDE Discover, GNOME Software or others and show the ratings on Flathub. This would also allow us to sort apps by rating on Flathub.

This might be done in a different stack or as a part of the Flathub website. Details depend on the proposal.

There is previous art, by the name of [ODRS](https://odrs.gnome.org/), but it probably needs to be redone from scratch.
If we could keep the database (but move it to postgres) and also keep the api (probably import the openAPI spec file) that would be huge.

Possible mentor: @razzeee

Difficulty: Hard

Project size: Big

## Explore backend CMS

It might be nice to use a CMS to be easily able to handle pages and other data. We could explore https://payloadcms.com/ or https://strapi.io/ and see if we can get it nicely integrated.

1. Move static pages into the CMS and figure out how to handle translations of those pages
2. Try importing app data and statistics and render those pages with data from the CMS too

Possible mentor: @razzeee

Project size: Medium/Big

## Beginner tutorials

Flatpak is a relatively new technology and there are not many tutorials out there. We would like to have some more tutorials for beginners at https://docs.flatpak.org that explain how to use Flatpak and how to package applications for Flathub. It would make most sense to start with tuturials for popular languages or frameworks.

Possible mentor: @razzeee

Difficulty: Easy

Project size: Medium
