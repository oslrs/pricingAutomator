# OSL's pricingAutomator

The purpose of the pricingAutomator is to automate 50%+ of pricing at OSL's Pricing & Communications department.

Assuming pricing takes 4 hours/day, that amounts to 2 hours/day saved... or 10 hours/week saved... or *520 hours/year saved*.

*The value add increases when you consider decrease in pricing tickets too... Harder to measure that though...*

## Pseudocode

Here's the pseudocode for this project:

1. Compare changes between carrier-provided grid & master grid:
    * Convert carrier-provided grid into SQL table
    * Compare SQL table with master SQL table
    * Return the differences
2. `Human step`: Evaluate that the carrier changes are correct or as intended:
    * **If changes are incorrect**: User manually edits changes
    * **If changes are correct**: User presses button to move to the next step
3. Overwrite changes into relevant cells of master SQL table
4. Output checklist of required gift card changes
5. `Human step`: Program gift card changes in RQ
6. Output import-ready CSVs of RQ price sheets
7. `Human step`: Import CSVs into RQ price sheets
8. Output & schedule pricing email:
    * Output pre-populated price flags for each region:
        * Evaluate whether changes are flag-impacting (check WAS to NOW)
        * Insert flag-impacted device into price flag template
        * If device has already been added, skip insert
        * Convert populated price flag template into PDF
        * Attach to pricing email
    * Output regional grids:
        * Pull region from each carrier
        * Create custom spreadsheets for each region that contain every carrier for that region