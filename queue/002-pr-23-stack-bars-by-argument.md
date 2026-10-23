---
kind: pr
target_repo: emilk/egui_plot
base: main
head: xc4pr:fix/23-stack-bars-by-argument
verified_commit: af96f142ac4857671e39a02870fb7c8e62474edc
draft: true
issue: https://github.com/emilk/egui_plot/issues/23
---

# Title

Stack bars on the bars with the same argument

# Body

* Closes <https://github.com/emilk/egui_plot/issues/23>
* [x] I have followed the instructions in the PR template

`BarChart::stack_on` paired bars by index, so charts with a different number of bars (e.g. after filtering out empty entries) were stacked on the wrong bars. Bars are now matched by `argument`, checking the same index first so the usual case stays linear. Charts whose bars line up by index behave as before. Behavior change: arguments are compared exactly, and a bar with no matching argument in the other charts is no longer stacked. Added a unit test that fails without the change; `./scripts/check.sh` passes.
