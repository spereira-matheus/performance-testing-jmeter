# Metrics & Acceptance Criteria (JMeter)

## Core Metrics
- Response Time: average, p90/p95 (focus: p95 for user experience)
- Throughput: requests/sec
- Error Rate: % of non-2xx/3xx responses
- Stability: no increasing error trend across the test duration

## Suggested Targets (example)
These targets are contextual and should be calibrated for the system under test:
- Smoke baseline: p95 < 800ms, error rate = 0%
- Load steady: p95 < 1200ms, error rate < 1%
- Stress ramp: identify breaking point and document failure mode (timeouts, 5xx, saturation)

## Notes
In real projects, acceptance criteria must consider infrastructure, caching, and peak traffic patterns.