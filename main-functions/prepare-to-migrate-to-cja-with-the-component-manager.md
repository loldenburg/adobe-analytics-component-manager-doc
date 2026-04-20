# Prepare for the Migration from Adobe Analytics to Customer Journey Analytics with the Component Manager
Outline for presentation

## Intro: A failed migration
**"Where is my dashboard? Why are the numbers so different? What should I believe now? Where is that segment I used in AA?"**

If you have messed up your migration, an explosion like this is likely.

It is the worst thing that can happen migration-wise: Frustrated early adopters telling everybody in the org how bad the new CJA experience is, that you have to build everything again — but even then, you can't, because dimensions x, y, z are missing in CJA.

So make your end users your migration priority — and that counts for migrations to CJA just the same as to any other tool. CJA is both great and tricky in that sense. The interface is nearly identical to AA, so while that helps users avoid a steep learning curve, it can also fool them into believing everything will work the same as in AA. It won't. Not even close.

The Component Manager helps prevent such migration failures.

Remember: **You can never make a second first impression.**

## What is the Component Manager?
[TODO: add Component Manager intro content from basic intro slides]

## Example Client Scenario
- Wants to migrate to CJA
- Many years of AA usage: tens of thousands of segments, Calculated Metrics, Workspaces, Users, etc.

**=> Impossible to migrate everything**, even 10% of that with reasonable effort.

**=> Migrating everything is also nonsense** — why would you want the >50% of your AA setup that nobody uses anymore to end up in CJA?

== Can't we use Adobe's "**Component Migration Tool**" 

The Component Migration Tool (see https://developer.adobe.com/analytics-apis/docs/2.0/guides/endpoints/compmigration/ or the post by Alana Davis from Concord: https://www.concordusa.com/blog/streamlining-your-journey-to-customer-journey-analytics-a-guide-to-adobe-analytics-component-migration-tool) e.g. creates workspaces, calc metrics, segments and date ranges in CJA based on AA workspaces, but...

  - ... for that to work properly, you need a one-to-one match of AA components to XDM fields in the CJA Data View. 
  - In many cases, such a matching makes no sense because what requires 3 different eVars in AA is often doable with one XDM field in CJA which you then curate to be provided as 3 dimensions in the CJA interface
  - Even if you match everything, certain AA logic will be migratable, but simply won't work in CJA, e.g., segment conditions where the underlying eVar is based on the AA Visitor profile
  - Some component types are simply not supported at all and need to be removed from the Workspace before being able to migrate it, e.g. Analytics 4 Target, "Page Summary" panels

But more importantly, 
  - You should use the CJA migration also as the long-awaited opportunity to get rid of legacy AA thinking models (eVars/props/etc.) 
  - Chicken-and-egg problem: It requires you to already have created a near-full configuration in CJA to have sth to map to - but for that, you need to know what you actually need in CJA 
  - In short: The migration tool helps with the actual migration step, but it still does not tell you WHICH workspaces, segments, calculated metrics etc. you **should** migrate 

Last but not least, expert practitioners like my friend Patrick Hegnauer (https://experienceleague.adobe.com/en/perspectives/cja-readiness-three-key-considerations-before-migrating-to-cja) recommend against the migration tool: "We avoided using the Component Migration Tool and instead built a new, streamlined setup. [...] We reviewed and refined segments, metrics, and other components to prevent legacy elements from being carried over."

His key reasoning also is: With the Component Migration Tool, you are cementing the old AA Logic (thinking in eVars and props) in the new system.

So: "Even if you choose to go with Adobe's Component Migration Tool, you need a hard selection of **what** to migrated - so even then, the Component Manager will help you tremendously.

## Strategy: Use the Component Manager to clean up first, then identify what is worth migrating
This is crucial — a migration from AA to CJA is a giant, expensive project.

Everything you can leave out of the migration lowers the migration costs across the board: tracking concept, dev implementation, AEP & CJA configuration, testing, report/workspace setup, user onboarding and training, etc.

## Side note: What do I mean by "migration"?
- A migration is **not** a one-by-one "as-is" replacement of each AA element or Workspace.
- Workspaces, Segments, Calc Metrics, and Dimensions do not need to be built or named exactly the same way in CJA.
- But CJA must offer an **equivalent** for the important AA elements — one that gives users the same data and information as the original in AA.

So the question is: **What is most useful for our users in AA?** — and then: how do we offer an equivalent in CJA?

## Part 1: Clean up Workspaces and Components

### Step 1: Identify and delete dead Workspaces

### Step 2: Identify and delete dead components

### Step 3: Harmonize duplicate components using the Component Replacer
Otherwise you may miss the true importance of some segments that exist under 10 different names with identical definitions — or end up migrating the same thing five times.

## Part 2: Identify the components used in the Workspaces worth migrating

Even after deleting thousands of dead Workspaces and components, plenty will remain — far too many to migrate all of them.

You will also need to keep some Workspaces alive in AA during the transition period when both AA and CJA run in parallel.

**So how do you prioritize which segments, date ranges, and calc metrics should really be considered for rebuilding in CJA?**

### Step 4: Create a copy of the "workspaces" tab
Give the new tab any name you like, e.g., `wsp_to_limit_comp_usage`.

### Step 5: Filter the workspace list in this new tab to only the "relevant" workspaces — those worth migrating
**Example:** "All with at least x Views in the last y days, minus those with certain tags or prefixes, plus some manual selections."

You can also involve your users: send an email to the owners of the relevant workspaces with a link to the list so they can mark or prioritize those that absolutely need a CJA equivalent.

<figure><img src="../.gitbook/assets/image (268).png" alt=""><figcaption></figcaption></figure>

### Step 6: In the `config` tab, set `limit_workspaces_for_comp_usage` to the name of the relevant workspace tab
(In our example: `wsp_to_limit_comp_usage`)

<figure><img src="../.gitbook/assets/image (267).png" alt=""><figcaption></figcaption></figure>

### Step 7: Set `run_with_hard_refresh` to `TRUE`
This resets previous Component Usage data and enables a full one-time scan of all your Workspaces on the next Component Usage update run. It automatically jumps back to `FALSE` after the run.

### Step 8: Run "Component Usage Update" again
The `matching_projects_count` column in the `all_comp_usage` tab will now count matches only within the "relevant" Workspaces:

<figure><img src="../.gitbook/assets/image (270).png" alt=""><figcaption></figcaption></figure>

**=> These components are the ones worth considering for a CJA migration.**

See also: https://docs.datacroft.de/main-functions/the-component-usage-tab#limit-workspaces-for-component-usage
## Part 3: eVars / props / Success Events / Classifications — revise the basic ingredients

While CJA should not contain elements called "eVars/props & Success Events", the data stored in an AA eVar will likely become a CJA dimension. So the usage of AA dimensions, classifications, and Success Events is a strong indicator of what data will be valuable in CJA.

- If a variable is popular → it should be part of the CJA arsenal.
- If a variable is barely used → you have a strong case for reducing the tracking and configuration complexity of CJA.

**This is crucial.** It is difficult to remove Success Events, eVars, or Classifications from AA because doing so can have all kinds of side effects, so most companies rarely clean up — and tech debt keeps growing. The migration is likely your only chance in a decade to **really** clean up. The fewer basic ingredients you need, the less complex your overall CJA setup can become.

### Step 9: Identify relevant eVars, props, Classifications and Success Events in the Component Usage tab
The cleanup and workspace-limiting work from Parts 1 and 2 also surfaces the usage of dimensions, classifications, and metrics (eg Success Events):
- Low usage → can they be left out of your CJA tracking plan?
- High usage → are they part of the CJA tracking plan? If not, consider adding them.

## Part 4: Users

### Step 11: POCs with Power User Allies — instead of a Big Bang Rollout
The Component Manager's Account Usage tab shows your most active AA users. These are your most important migration stakeholders.

As mentioned, frustrated early adopters can be catastrophic. Mitigate this by involving your power users early. Work together with them on a migration POC for some of their key Workspaces.

Don't make them feel overlooked. Make them your allies.

### Step 12: Finishing it up
When CJA becomes the recommended tool for everyone and the end-of-life of your AA is approaching, use the Component Manager to identify users who are still active in AA. Why are they still there? Did you miss something important? Can you offer them targeted CJA onboarding?

## Key Takeaways

- Migration is architecture work, not relocation. Whatever you don't clean up before the migration, you'll carry with you for the next ten years.

- Adobe's Component Migration Tool can only migrate what you've selected beforehand — the selection is the actual work. The Component Manager helps with that - in a data-driven, user-centric manner.

- Power Users decide whether the migration succeeds. Lose them early, and the migration is politically dead."