---
kind: pr
target_repo: emilk/egui_plot
base: main
head: xc4pr:fix/248-boxed-zoom-press-origin
verified_commit: 57adf2542b69eace8682df4e57738a4dd1667818
draft: true
issue: https://github.com/emilk/egui_plot/issues/248
---

# Title

Start boxed zoom rectangle at the press position

# Body

* Closes <https://github.com/emilk/egui_plot/issues/248>
* [x] I have followed the instructions in the PR template

egui only reports a drag once the pointer has moved past the click threshold, so storing `response.hover_pos()` at drag start put the first corner of the zoom box a few points away from where the button was pressed. This stores `pointer.press_origin()` instead (as axis-drag zoom already does), converted to layer-local coordinates like `hover_pos()`. Added a kittest that drags with the secondary button and checks the resulting bounds; it fails without the change. `./scripts/check.sh` passes.
