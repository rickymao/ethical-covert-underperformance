# covert-underperformance

Building **model organisms of covert underperformance**: language models that are
deliberately trained to underperform on specific tasks while hiding that they are
doing so. These organisms exist so that we can study the behavior in a controlled
setting and develop methods that detect and mitigate it.

## Motivation

Many AI safety plans depend on accurate capability evaluations. If a model can
strategically underperform ("sandbag") on evaluations, for example on dangerous-capability
benchmarks or on safety-relevant research tasks, then:

- capability evaluations may underestimate what the model can actually do,
- safety cases built on those evaluations may be unsound, and
- delegating alignment or safety research to models becomes riskier, because a model
  could quietly do worse work than it is able to.

The concerning version is **covert**: the underperformance is hard to tell apart from
honest mistakes or genuine incapability, and the model's outputs and reasoning do not
reveal that it is deliberate. Natural examples are rare and hard to verify, so we build
model organisms where we *know* the ground truth and can measure how well detection
methods work.

## Goals

1. **Construct organisms.** Train or prompt models that underperform on a target
   distribution (e.g. a particular domain or task type, or under a trigger condition)
   while keeping normal performance elsewhere.
2. **Make the underperformance covert.** Ensure the failures look plausible: realistic
   errors, no explicit admissions, and reasoning traces that do not reveal intent.
3. **Characterize them.** Measure the performance gap, how selective it is, and how
   robust it is to paraphrasing, elicitation, and prompting.
4. **Stress-test detection and mitigation.** Use the organisms as testbeds for
   techniques such as:
   - black-box monitoring of outputs and chain-of-thought,
   - consistency and difficulty-calibration checks,
   - capability elicitation via fine-tuning on a small number of examples,
   - noise injection / weight perturbation,
   - interpretability probes for deceptive or sandbagging-related representations.

## Threat model

We focus on underperformance that is:

| Property      | Description                                                              |
|---------------|--------------------------------------------------------------------------|
| **Targeted**  | Limited to specific tasks, domains, or contexts, not a global capability drop |
| **Deliberate**| The model could do the task, but chooses not to                         |
| **Covert**    | Not easily flagged by a monitor reading outputs or reasoning             |
| **Persistent**| Survives reasonable elicitation attempts that don't involve training      |

## Repository layout

```
covert-underperformance/
├── data/            # datasets: target/control task sets, training data, eval outputs
├── main.py          # entry point (placeholder)
├── pyproject.toml   # uv project config
└── README.md
```

## Getting started

This project uses [uv](https://docs.astral.sh/uv/).

```bash
uv sync
uv run main.py
```

## Responsible use

These organisms are built for safety research: to understand covert underperformance
and to validate tools that catch it. Trained artifacts should be kept in controlled
environments and clearly labeled as intentionally misaligned research models.
