# Scope: what the harness is, and what makes it hard

First draft 5 Nov 2026. Working reading: **volunteers donate compute; vetted researchers submit jobs** (see open item 1).

## Goals
- Anyone can join with a home PC in a few minutes: install, pick limits (hours, GPU %, power), done.
- Researchers get cheap, large-scale compute for open AI work, and results they can trust.
- Volunteers are safe: jobs can't harm their machine or read their files.
- Open by default: code, job lists and (where allowed) results are public.

## Non-goals (for now)
- Not a crypto token or paid marketplace. Credit/leaderboard only, like Folding@home.
- Not a general cloud. Only approved research jobs run.
- Not big-model pre-training at the start (see "workload fit").

## Who it's for
- **Volunteers:** gamers and hobbyists with idle GPUs, universities, people with old PCs.
- **Researchers:** academic and independent groups doing open AI work (evals, safety, interpretability, small models, science uses of AI).

## The hard problems (these decide feasibility)
1. **Workload fit.** Home internet is slow and machines drop out. Jobs that split into independent pieces work well:
   eval/benchmark runs, batch inference over datasets, synthetic data, hyperparameter sweeps, interpretability probes on small models.
   Training one model across the internet is hard; low-communication training methods exist but are research-stage. Start with the easy class.
2. **Volunteer safety.** Running outside code on home PCs. Needs: sandboxed runner (container/VM, no file or network access beyond the job), signed jobs from approved projects only, resource caps, easy pause/uninstall.
3. **Trusting results.** Some nodes will return wrong or fake work. Needs: run a share of jobs twice and compare, spot-checks with known answers, reputation per node.
4. **Misuse.** A public harness could be used for harmful work. Needs: job submission only by vetted projects, published job list, model and data licence checks, a review step for new projects.
5. **Privacy.** Volunteers can see job data. Rule: only public or non-sensitive data and models go out; nothing personal.
6. **Mixed hardware.** NVIDIA/AMD/Apple/CPU, different VRAM. Scheduler matches jobs to what each node can do.
7. **Cost and energy.** Electricity is the volunteer's cost. Show estimated watts/cost; default to "idle only".
8. **Build vs extend.** Existing volunteer-compute and decentralised-AI projects may already do much of this. Decide early whether to build, fork, or contribute to one (phase 0).

## Rough shape (to confirm in phase 0)
- **Coordinator:** job queue, node registry, scheduler, result checking, credit.
- **Client:** small app on the volunteer's machine; detects hardware, pulls signed jobs, runs them in a sandbox, uploads results.
- **Researcher side:** submit a job package (container + inputs + how to check results), watch progress, download results.
- **Public site:** stats, leaderboard, list of projects and what they're running.
