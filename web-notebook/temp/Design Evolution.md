

## 2.2 Design Evolution 
After low-fidelity testing, we implemented several targeted changes guided by participant feedback and feasibility considerations. Table 1 summarises the three primary updates, followed by detailed narratives that document the cues we received, alternatives we explored, and why the final solution best supports usability and implementation.

| No. | Component / Change | Why We Changed It | Usability / Feasibility Rationale |
|-----|--------------------|-------------------|-----------------------------------|
| 1 | **Single-page architecture with spotlight toggle surfaced in Task 1** | Testers were confused by multiple HTML entry points (“Which file do I open?”) and often missed the original spotlight toggle buried in a sub-menu. Peers suggested converging on one launch path. | One `index.html` reduces onboarding friction and keeps the key adaptive control in immediate view. This supports faster learnability (UQ1) and simplifies deployment since all scripts run in a single document. |
| 2 | **Hero overview cards + hide/show toggle** | Participants praised the contextual cards but complained they blocked the viewport during live demos. They requested a way to collapse the overview quickly. | The `Hide task overview` button delivers just-in-time onboarding and frees screen real estate on demand, improving visibility (Nielsen heuristic) without sacrificing discoverability for new users. |
| 3 | **Unified right-hand drawer integrating spotlight, heatmap, and bandwidth controls** | Early builds scattered controls across tabs/sections. Low-fi sessions revealed users wanted “all knobs in one place” and facilitators needed quick access to diagnostics. | Consolidating controls shortens task-switching time, reduces navigation errors, and made it feasible to add new instrumentation (bandwidth monitor toggle, status badges) without bloating the layout. |

**Table 1. Principal design changes enacted after low-fidelity testing**

### Detailed Rationale
1. **From multi-file prototype to a single-page suite.**  
   - *Feedback source*: Three out of five lo-fi participants paused at the file tree, unsure which HTML file to open. Facilitators also reported anxiety about keeping multiple tabs synchronised during demos.  
   - *Explored options*: We considered adding a launcher page that linked to the original task-specific files but that introduced an extra step and duplicated JS logic.  
   - *Final decision*: Merge all code paths into `index.html` and surface the focus spotlight toggle at the very top of the drawer. Besides reducing cognitive load, this enabled shared state between tasks (e.g., the heatmap array and bandwidth diagnostics), which would have been harder to synchronise across multiple documents.

2. **Hero overview with contextual toggle.**  
   - *Feedback source*: Both peers and class reviewers appreciated the narrative cards but wanted “a way to get them out of the way once we start testing.”  
   - *Usability reasoning*: Leaving the cards permanently visible violated the “visibility of system status” heuristic by hiding the stage whenever the summary was open. Hiding them entirely would make onboarding harder for first-time viewers.  
   - *Implementation notes*: We introduced a hero-level toggle that adds/removes a `task-summary-hidden` class. This works responsively (no layout jank on small screens) and respects motion-reduction preferences (no animated collapses), keeping the experience accessible.

3. **Unifying task controls in a persistent drawer.**  
   - *Feedback source*: Low-fi observers repeatedly asked “Where do I change the radius?” or “Where is the bandwidth panel again?” when controls were scattered across tabs. Facilitators also struggled to monitor diagnostics while guiding participants.  
   - *Usability reasoning*: Centralising controls reduces navigation depth and supports learnability by improving recognition. It also paves the way for keyboard navigation because controls now reside in a predictable order.  
   - *Feasibility*: We refactored the JS to manage task state objects (`focusState`, `trackingTask`, `adaptiveController`) inside one module, avoiding global collisions and simplifying future instrumentation (e.g., logging heatmap datasets or toggling the bandwidth monitor).

### Supporting Adjustments
- **Bandwidth monitor toggle + status pill** — Added after facilitators noted the overlay occasionally occluded the scene; the toggle keeps the UI agile for demos.  
- **Task HUD refinement** — Incorporated persistent score/time feedback based on requests for better situational awareness during the tracking exercise.  
- **Adaptive encoding badge repositioning** — Moved leftwards to avoid collisions with the focus settings button, addressing an occlusion issue observed in hallway tests.

Collectively, these updates address the top pain points surfaced in low-fi sessions: uncertain entry points, obstructed staging area, and dispersed controls. The high-fidelity prototype is now easier to demo, faster to learn, and better aligned with the feasibility constraints of a single-page web deployment.
