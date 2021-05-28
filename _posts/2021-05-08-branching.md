---
layout: post
title: "Branching"
date: 2021-05-28 22:02:28 -0500
categories: mendix mendix-way
---

# Branching

When it comes to branching in SVN, less is more. Because of the way that SVN treats branches and&mdash;more importantly&mdash;revisions, there are some patterns that you may be familiar with from Git that are ill-advised in SVN.

### The Mendix Pattern

If you're looking for the pattern that the most customers have used to drive successful projects, this is it. One ongoing development line that all developers work on, plus necessary branches for hot fixes, plus the trunk.

![image-20210528165933127](/assets/image-20210528165933127.png)

I've seen customers try other patterns, but none have ever been as successful as this tried-and-true method. Let's explain:

1. Main - *no junk in the trunk*: no development work happens on this line. It is kept up to date with the code from the latest stable release, after the release build is created from the development branch. Policies include:
   1. No development on this line
   2. Only releasable code from Development is merged in here
2. Development - *ongoing development work*: all regular development work happens in this line. Developers are encouraged to update their working copy from this branch regularly, and only commit when they have finished a story and their code is in a ready state. Conflicts here should be resolved immediately. Policies include:
   1. All planned development happens here
   2. Developers update from this line frequently
   3. Builds happen here frequently for PO acceptance and testing
   4. When the accrued changes here become stable enough to release, create a releasable build and merge the code into Main
   5. Resolve conflicts immediately

### What about parallel teams?

Many customers ask how to have parallel teams working on the same project. Very few of them actually have the required level of coordination/planning to do so. 

In general, if you're planning to do parallel teams, you should have clearly dilineated work for each team, with few overlapping sections. If the teams are working on related features, then splitting them into separate teams rather than having them operate as one team will only act to add communication overhead and slow down their delivery time.

If your parallel teams are set up properly, there's no reason why they shouldn't be able to collaborate on a single development branch as stated above, as long as the follow the policies of the two branches.