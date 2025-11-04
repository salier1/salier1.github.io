# 4. Usability Test Plan

## 4.1 User Population
| Attribute | Definition |
|-----------|------------|
| Target users | Knowledge workers and graduate students who regularly consume remote presentations, training clips, or screen-share walkthroughs (aligned with our original design brief). |
| Sample size | **6–8 participants** per round. |
| Background | Comfortable with web browsers, mouse/trackpad navigation, and multitasking between content and controls. |
| Usage context | Watching adaptive media on laptops/desktop monitors in quiet office/home-office settings; occasionally on shared screens during team workshops. |

> Recruitment: leverage campus mailing lists and internal HCI lab volunteers who match the above profile.

---

## 4.2 Usability Goals
| ID | Goal Statement | Quantitative Target |
|----|----------------|---------------------|
| **UQ1 — Learnability** | Users understand how to enable/disable each adaptive control (focus spotlight, heatmap review, bandwidth monitor) without facilitator intervention. | ≥ 90 % of participants locate and activate the requested control within **30 s**; first complete run of any task finished in ≤ 2 min with no help. |
| **UQ2 — Efficiency** | Adaptive aids (spotlight & heatmap) reduce the effort required to acquire targets. | Target acquisition time with adaptive **ON ≤ 80 %** of adaptive **OFF** baseline; cursor travel distance per hit reduced by ≥ 15 %. |
| **UQ3 — Satisfaction** | Adaptive visuals feel comfortable and pleasant. | ≥ 80 % of participants rate “comfort/clarity/visual pleasantness” **≥ 4/5** on a post-task Likert survey. |
| **UQ4 — Perceived Clarity** | Users perceive better focus on key regions when adaptive blur is active. | ≥ 75 % report improved clarity in adaptive ON mode; heatmap density on target zones increases by ≥ 25 %. |
| **UQ5 — Robustness** | Adaptive streaming remains stable under network fluctuation simulations. | Update latency < 80 ms during adaptive adjustments; ≥ 95 % of simulated runs show no visible flicker/contrast loss. |
| **UQ6 — Awareness & Control** | Users feel in control and not distracted by automation. | ≥ 80 % agree “I felt in control of the adaptive effects”; < 10 % describe the automation as distracting/confusing. |

---

## 4.3 Test Procedure
1. **Staffing**: two examiners per session  
   - *Facilitator* — delivers script, manages timing.  
   - *Note-taker* — logs observations, metrics, and screenshots.
2. **Environment & Equipment**  
   - 15″–24″ laptop/desktop with external mouse.  
   - Latest Chrome or Edge browser.  
   - Stopwatch / digital timer (e.g., TimeTabler app).  
   - Observation sheet (Google Sheet template), consent form, pre/post questionnaires (Google Form).  
   - Optional screen/audio capture (OBS or QuickTime) with participant consent.
3. **Prototype Handling**  
   - Load `index.html` via Method A (direct open) or Method B (Live Server), referencing the **User Manual**.  
   - Verify hero overview, focus spotlight, heatmap toggle, and bandwidth monitor before inviting the participant.
4. **Participant Briefing**  
   - Present study purpose (“Evaluate how adaptive gaze features support remote content viewing”).  
   - Gather demographic and familiarity data (pre-test survey).  
   - Remind participants they can withdraw at any time; encourage think-aloud narration.
5. **Task Script** *(approx. 25 minutes total)*  
   1. **Warm-up** — Toggle focus spotlight, adjust radius.  
   2. **Task 1** — Locate spotlight toggle & resize spotlight.  
   3. **Task 2** — Run a 45 s heatmap session, score ≥ 5 hits, review heatmap.  
   4. **Task 3** — Enable adaptive bandwidth, simulate “Limited” and “Boosted” networks, interpret bandwidth monitor.  
   - Facilitator provides task cards; avoid hinting exact control locations unless participant stalls > 90 s (then note “assistance provided”).  
6. **Interaction Rules**  
   - Facilitator only clarifies task goals; no step-by-step coaching.  
   - Encourage think-aloud but avoid evaluative language (“Good job”).  
   - If participants ask “Where is X?”, respond with neutral prompts (“What would you try next?”).  
7. **Data Capture**  
   - **Timing**: start/stop per task and per target action (e.g., toggle found).  
   - **Errors**: mis-clicks, incorrect toggles, requests for help.  
   - **Cursor metrics**: optional logging via built-in heatmap arrays (export JSON) or manual observation of distance/hits.  
   - **Subjective ratings**: immediate post-task Likert items for comfort, clarity, control.  
   - **Qualitative notes**: confusion points, quotes, body language.  
8. **Post-Session Wrap-Up**  
   - Administer 5-question SUS-lite or custom satisfaction survey (Likert + free-form).  
   - Conduct 3-minute semi-structured interview (perceived strengths, pain points, desired changes).  
   - Thank participant, record final timestamps, and anonymise data.

---

## 4.4 Reporting

### A. Data Recording & Reporting Workflow
| Step | Details |
|------|---------|
| Capture | Use the shared Google Sheet to log times, errors, assistance flags, and heatmap exports. Screen/audio capture stored in the team’s secure Drive folder. |
| Survey aggregation | Google Forms automatically summarises Likert scores; export CSV for analysis. |
| Synthesis | Weekly debrief with the design team to cluster issues (e.g., affinity mapping) and track goal attainment (e.g., % hitting targets). |
| Deliverables | Produce a concise PDF report (2–3 pages) containing metrics, findings, priority issues (P1–P3), and recommended actions. Upload to course portal and archive in repo `/reports/usability-round1.pdf`. |

### B. Usability Evaluation Plan
| Evaluation Method | Metrics & Justification | Application |
|-------------------|------------------------|-------------|
| **Lab-based task testing** | Task completion time, error counts, assistance requests — directly map to UQ1/UQ2 (learnability, efficiency). | Measured during scripted tasks; compare adaptive ON vs. OFF to validate efficiency gains. |
| **Perceived clarity & satisfaction survey** | Likert ratings on comfort, visual clarity, control (UQ3/UQ4/UQ6). | Post-task survey + interview to quantify subjective comfort and awareness. |
| **Heatmap / cursor analytics** | Fixation density and cursor travel distance (supports UQ2 & UQ4). | Export heatmap JSON or capture via built-in arrays; compare density on targets with/without adaptive blur. |
| **Network stability test** | Latency logs and observer checklist for flicker/contrast (UQ5). | During Task 3 simulations, note any visual artefacts and measure update delay via console timestamps. |
| **Heuristic evaluation (Nielsen 10)** | Focus on visibility of system status, user control/freedom, match to real-world expectations. | Conducted by 2 HCI evaluators pre- and post-user test to catch structural issues early. Findings feed into redesign backlog. |

Data from the quantitative lab sessions will validate whether the prototype meets the numeric targets. Heuristic critiques ensure broader UX quality (consistency, feedback). Together, they create a feedback loop: measure → analyse → redesign → re-test.

---

**Outcome:** This plan ensures that usability metrics (time, errors, satisfaction), qualitative insights, and expert heuristics all inform the next design iteration, keeping the prototype aligned with the needs of adaptive media consumers.
