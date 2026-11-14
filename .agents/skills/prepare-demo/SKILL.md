---
name: prepare-demo
description: Prepare and validate a reliable hackathon demonstration from implemented behavior.
---

# Prepare a demo

1. Inspect actual implemented functionality and select the strongest complete end-to-end
   user journey.
2. Verify required services, health endpoints, frontend behavior, and external API
   dependencies.
3. Prepare realistic example inputs and verify the expected output.
4. Label real, simulated, mock, and synthetic data explicitly.
5. Produce a concise demonstration sequence, setup commands, fallback plan, risks, and
   features that must not be shown because they are incomplete or unreliable.

Do not imply unsupported scientific validity or silently substitute mock results. Report every
failed prerequisite and the logs or command needed to resolve it.

## Success criteria

The chosen journey works from a clean documented setup, outputs are reproducible, dependencies
and limitations are visible, and the presenter has a tested fallback.
