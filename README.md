# covert-underperformance

Building **model organisms of covert underperformance**: language models that are
deliberately trained to underperform on specific tasks while hiding that they are
doing so. These organisms exist so that we can study the behavior in a controlled
setting and develop methods that detect and mitigate it.

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
