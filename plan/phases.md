# Phases

First draft 5 Nov 2026. Each phase ends with a test; don't start the next until it passes.

## Phase 0: survey and decide (now)
- Survey prior art and check what each does today (this list was drafted from memory, so verify):
  BOINC, Folding@home (volunteer compute); Petals, Hivemind, Prime Intellect, exo, Nous Research (decentralised AI training/inference). To check: others since.
- For each: what workloads, how they handle trust and sandboxing, licence, is it active, could we build on it.
- Pick the first workload (suggest: running open-model evals/benchmarks).
- Decide build vs fork vs contribute.
- **Exit test:** one-page decision note in `plan/` with the chosen workload, approach and tech stack.

## Phase 1: prototype on maintainers' machines
- Coordinator + client, running on two or more machines the maintainers own (private network, no public access).
- One job type end to end: fetch signed job → sandbox → run → upload → coordinator checks by running twice.
- Basic limits (pause, GPU cap) and a simple status page.
- **Exit test:** 100 eval jobs complete across the test machines, results match a single-machine run, a deliberately bad result is caught.

## Phase 2: closed pilot
- 10–30 invited volunteers, 1–2 friendly research projects.
- Add: node reputation, spot-checks, installer, crash reporting, credit.
- Security review of the client and sandbox before anyone outside joins.
- **Exit test:** a month of runs with no sandbox escape, results trusted by the researchers, volunteers say it's easy.

## Phase 3: public
- Public sign-up, project review process, public stats/leaderboard, docs.
- Governance: who approves projects, code of conduct, how to report misuse.
- Later: more job types (synthetic data, fine-tuning, low-communication training if phase 0 shows it works).
- **Exit test:** to define at the end of phase 2.
