# Code contribution

The Github repositories are the central system of every contribution to our key components of Bao Finance. From smart contracts to UI, main net products or for our franchises, every code in production is public and is open to improvements and bug fixes by our community.

As such, we want to align with the best practices coming from Github and we will follow their Developer Contribution Guide

![](https://aws1.discourse-cdn.com/standard10/uploads/bao/optimized/1X/01a4ef5b2a12d0f5909c90c3f1ecf410f5477fea\_2\_690x204.png)

1. Take a look at the GitHub Issues pertaining to a particular repository/project that you (the Contributor) would like to contribute to.&#x20;
   * In the case that an issue does NOT exist that handles the Contributor's particular bug-report/proposed-enhancement the Contributor can simply create a new issue outlining as much information as you know regarding the goal of the issue.&#x20;
   * The Contributor is free to include as much implementation information as you think would be helpful, but at this stage, the implementation is simply a suggestion.&#x20;
   * The important thing is that a “Goal” is identified for the issue and a way for us to validate that we have achieved that goal.&#x20;
   * At this stage, it is at the “Discussion” stage.
2. Once a GitHub Issue exists that contains the goal of the bug-report/proposed-enhancement it should be discussed within the Issue as much as possible between the Contributor, any potential Contributors, and the Guardians responsible for that particular repository.&#x20;
   * Communication can happen within Discord if more real-time feedback is required, but the results of those conversations should be documented in the Issue itself.&#x20;
   * The goal is that if the original Contributor decides not to continue work on the Issue, but a new Contributor arrives, they should have all the information they need within the issue. The goal of this communication is to outline the details of how the issue should be solved. Links to code, other documentation, or anything else that can help should be included in the Issue.&#x20;
   * At this stage, it is entirely possible that through further discussion this particular issue is no longer needed. Possibly because of future planned work, or maybe it’s just not worth the effort at this stage. The issue can transition to “Out of Scope” which means all work will stop on the ticket.
   * “Out of Scope” tickets will remain open for further discussion, but after a period of time with no activity, it will be closed.
3. Once an implementation is decided upon the Issue is considered “Ready for Work”. At this point either a project maintainer is assigned to the Issue and is responsible for its completion. Or the Contributor may decide that they would like to tackle the work. Either way, the process is the same.
4. The Contributor or Maintainer will take time to translate the implementation details outlined in the Issue to the actual repository working on their own branch/fork with some reasonable name outlining what it does.&#x20;
   * They are free to open a Draft Pull Request if they would like to work more closely with others on the implementation in public, but it is not necessary.&#x20;
   * Once the Contributor or Maintainer considers the work “Code Complete” and that the original goal for the Issue is met, they can update the Draft Pull Request into a Regular Pull Request and a Reviewer will automatically be assigned.&#x20;
   * Normally discussions may have a couple of Maintainers that are involved in fleshing out the details so reviewers can also be assigned manually by whoever opens the PR.&#x20;
   * The PR should include a link back to the original Issue so that anyone following the Issue is aware of the code changes.
5. Once a reviewer is assigned it is their responsibility to review the code to ensure it meets the project’s standards and to request any changes necessary to do so.&#x20;
   * It is the responsibility of the reviewer to validate that the changes made actually meet the goal of the issue and do so in a way that doesn’t impact anything else.&#x20;
   * The Reviewer and Contributor may go back and forth during the review on changes, but the overall implementation shouldn’t be drastically different from the one that was planned during the discussion.
   * &#x20;Syntax/Testing should all be automated and should not be the focus of the review. If the tests are not passing, no formal review is necessary.&#x20;
   * As part of this process, the reviewer should use their judgment and decide whether or not to run the code locally to verify it.
6. Once the review is completed it can be merged into the `main` branch by the reviewer. This will automatically deploy the changes to the staging environment of the project and allow other members to test the changes without needing to run anything locally.
7. When the project next does its release, the changes merged into the `main` branch will be automatically deployed. When creating the release, the notes should link to any Issues that were worked on at this time. This allows anyone reading the release notes to not just see WHAT was released, but also the underlying code changes/discussion that took place to get the change made.
