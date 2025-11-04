# 2. Prototype Overview

## 2.1 System Description
The current prototype (“Gaze Interaction Prototype Suite”) delivers three gaze-inspired interaction concepts inside a single HTML experience:

- **Gaze-Adaptive Player** – A focus spotlight follows the viewer’s point-of-regard, sharpening the focal region while softly blurring the periphery.  
- **Attention Heatmap Dashboard** – A timed tracking task collects cursor/gaze events, awards points for hits, and renders a cumulative heatmap overlay.  
- **Adaptive Bandwidth Controller** – A control deck lets facilitators simulate network conditions, toggle adaptive streaming, and inspect bandwidth usage vs. availability.

Key characteristics:
- Entirely self-contained in `index.html`; no external build step or backend.  
- Right-side drawer unifies controls (toggles, sliders, diagnostics) for all three tasks.  
- Hero landing screen doubles as onboarding copy and can collapse to maximise the stage.  
- Accessibility considerations include keyboard-focusable toggles, ARIA labels, and stateful badges (e.g., adaptive encoding indicator, bandwidth “Stable/Buffering” pill).

---

## 2.2 Design Evolution (with rationale)
| No. | Change Summary | Why We Changed It | Usability / Feasibility Rationale |
|-----|----------------|-------------------|-----------------------------------|
| 1 | **Merged multi-page flow into one entry point** and surfaced the spotlight toggle in Task 1. | *Feedback*: Lo-fi testers were unsure which `.html` file to start with (“Do I open task1, task2?”). Team members advocated for “single file, single toggle” to reduce onboarding friction. | A unified `index.html` eliminates file confusion and places the “Enable focus spotlight” control where people immediately expect it. This shortens setup time and improves learnability for new facilitators. |
| 2 | **Added hero task overview with collapsible cards** (`Hide task overview` button). | *Feedback*: Early demos showed the overview cards were helpful but blocked part of the viewport (“Can we hide the cards while demonstrating?”). | The toggle preserves instructional context for first-time viewers while letting presenters reclaim space instantly. It supports both discovery and unobstructed playtesting on the same screen. |
| 3 | **Introduced unified drawer with integrated diagnostics** (spotlight settings, heatmap workflow, bandwidth monitor toggle). | *Feedback*: Reviewers wanted consistent access to controls without swapping files or scrolling long pages (“All the knobs should live together”). | Centralising controls improves discoverability, reduces task-switch friction, and simplifies development because every script runs in one place. It also enabled the new bandwidth monitor toggle after usability feedback. |

### Supporting Iterations
- **Bandwidth monitor toggle & status badge** – Added when facilitators requested a way to declutter the viewport and highlight automation states only when relevant.  
- **Task HUD polish** – Incorporated requests for persistent score/time feedback during the heatmap exercise.  
- **Badge repositioning** – Shifted the adaptive encoding badge left so it no longer collides with the Focus settings button.

These adjustments address the top issues uncovered in low-fidelity testing: confusing entry points, obstructed main stage, and scattered controls. The result is a high-fidelity prototype that is faster to demo, easier to learn, and truer to the intended adaptive experience.
