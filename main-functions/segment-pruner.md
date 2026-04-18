---
description: >-
  The Segment Pruner takes a segment and reduces it to a smaller definition,
  thereby making it faster and easier to maintain.
---

# Segment Pruner

## Summary

Large segments (e.g. for Bot Filters in Virtual Report Suites) with many conditions can massively slow down your Adobe Analytics reporting performance. The Segment Pruner shows you the smallest possible alternative to a segment without any dreadful manual work.

The Segment Pruner works as follows:

1. It creates alternative smaller temporary versions of a segment by an algorithm that recursively prunes the segment, i.e. it removes one element combination at a time, but only combinations of elements which are themselves "**non-data-changing"**. "Non-data-changing" means the pruned version returns the same data as the original segment.
2. The Pruner checks which of these pruned versions of the segment are **not** data-changing. The **smallest possible, non-data-changing alternative version "wins".**&#x20;
3. The Pruner then creates an alternative segment in your Adobe Analytics account which you can verify by yourself. **Don't worry, it does not change the original segment!**
4. The pruning algorithm works in an efficient manner from largest combination of pruned elements to smallest. The process is stopped when the mathematically smallest possible segment has been reached.
5. For multi-value elements like **"contains any of"**, **"equals any of"** or their negative variants, the Pruner also reduces the list of values to the minimum non-data-changing possible.

## Video Guide

{% embed url="https://youtu.be/V5Cr_BcfmDI" %}

## Step-by-Step Guide

1. If you have not installed the Component Manager yet, [do that](../getting-started-with-the-component-manager/) first. After that, populate the "Report Suites" (Extensions -> AA Component Manager -> Report Suites -> Refresh Report Suites) tab and, ideally, the "[All Components](the-full_comp_import-tab.md)" tab (Component Editor -> Reload Components).&#x20;
2. Run "Extensions -> AA Component Manager -> Component Editor -> Prune Segment". The first time, this will insert the template tab for the Segment Pruner.
3.  Configure the Segment Pruner:<br>

    <figure><img src="../.gitbook/assets/image (188).png" alt=""><figcaption></figcaption></figure>

    1. **Report Suite ID:** Select a Report Suite (for this, Report Suites -> Refresh Report Suites needs to have run at least once)
    2. **Days back:** The Segment Pruner works by comparing alternative shorter versions of the segment to the data that the original segment returned. Enter how many days back the data of alternative segment versions should be compared to the original. Premium clients can select up to 750 days. In the free version, it is up to 30 days. Only full past day are evaluated, today's data will not be evaluated as it may increase during the pruning process.
    3. **Segment ID:** Enter the ID of the segment which should be pruned. You can easily find the ID e.g. in the "full\_comp\_import" tab.
    4. **Metric IDs:** By default, the Segment Pruner checks against Occurrences and Orders. If you prefer other metrics, enter their IDs separated by commas. **Only 2 metrics** are supported.
    5. **Tolerance rows:** By how much can the alternative version of the segment be off compared to the original segment and still considered a valid alternative? Recommendations:
       * We recommend a softer threshold like 0.001% for the first, not-so-important metric (e.g. Occurrences) and a hard threshold (0%) for the second, important metric (e.g. Orders).&#x20;
       * This guarantees that you are not leaving complex conditions in there even though they have nearly no impact on the data.
       * If the segment is large, the Pruner will run a lot of queries and take a while to complete, and if you have data source imports for historic data during that time, the data might change slightly during the run. In that case, all new definitions will be "not identical" if there is no tolerance threshold.
4.  Run the Pruner (Component Editor -> Prune Segment) and wait for the result in the status field. Depending on how big your segment is and how many days back you want to go, it can several minutes to complete. <br>

    <figure><img src="../.gitbook/assets/image (165).png" alt=""><figcaption><p>Summary: Pruning successful! <span data-gb-custom-inline data-tag="emoji" data-code="1f44d">👍</span></p></figcaption></figure>

    1. The final summary gives you two possible outcomes:
       1. No pruning possible: The segment is already in an ideal state and can't be made smaller.
       2.  Pruning was possible (see screenshot). The Pruner created an **alternative, pruned** version of the segment. You can check this version in AA and compare it to the original in a Workspace. Note that the **owner** of the segment is the same as the owner of the original segment, so if you don't see the segment right away in AA, go to Components -> Segments and then select "Other Filters -> Show All" on the bottom left.<br>

           <figure><img src="../.gitbook/assets/image (170).png" alt=""><figcaption><p>Example of what was removed from the segment without changing the data that the segment returns.</p></figcaption></figure>
    2.  If you are happy with the result, edit your original segment, drag in the pruned segment and then delete all existing elements: <br>

        <figure><img src="../.gitbook/assets/image (200).png" alt=""><figcaption></figcaption></figure>

## Limitations

### Execution Time

If the execution takes longer than 9 minutes, it will be aborted.

**Do not restart the Segment Pruner unless you see a message that it completed or that there was an error, or if you don't see anything in the status field for more than 9 minutes.**

If you have very large segments that cannot be pruned within 9 minutes, try the following:

* split the segment into smaller segments and prune those separately first. For example, if you have a large multi-value "contains-any-of" element in your segment, create a segment with just that element and prune that one first, then re-insert the pruned version into the original segment and try again.
* try with a shorter "days back" condition
* if you are a premium client, you can also contact your Datacroft contact to have them run an exceptionally long pruning process manually.

### Supported Segment Types

Supported are all containers, but the most testing was done for "AND" and "OR" containers. Sequential containers should work, too, but are not officially supported.

### How "perfect" is the Segment Pruner?

While the pruner is trying hard, there may occasionally be cases where an even smaller definition would have been possible. If you encounter such a case, please report it to component-manager@datacroft.de so we can improve the algorithm further.

