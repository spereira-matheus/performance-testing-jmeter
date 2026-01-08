# Performance Testing with JMeter

## Overview
This repository contains performance testing scenarios built with **Apache JMeter**, focused on validating system behavior under different load conditions using automated CI quality gates.

The goal is not only to execute performance tests, but to provide objective signals about system stability, latency, and failure behavior.

---

## Test Strategy

The test suite is divided into three complementary layers:

### Smoke Performance
- Very low load
- Validates baseline availability and latency
- Fast feedback
- Executed automatically in CI

### Load (Steady)
- Constant number of virtual users
- Validates system stability under expected traffic
- Focus on p95 latency and error rate
- Executed automatically in CI

### Stress (Ramp)
- Increasing load over time
- Identifies breaking points and failure modes
- Executed manually via CI workflow trigger

---

## Test Plans

Located in `/test-plans`:

- `smoke-baseline-jsonplaceholder.jmx`
- `load-steady-jsonplaceholder.jmx`
- `stress-ramp-jsonplaceholder.jmx`

---

## CI Execution Model

### Automatic (Push / Pull Request)
- Smoke test
- Load test
- Quality gate based on:
  - Error rate
  - p95 latency

### Manual Trigger
- Stress test
- Used for capacity analysis and exploratory performance validation

---

## Quality Gates

The CI pipeline fails if thresholds are exceeded:

| Test Type | Max Error Rate | Max p95 Latency |
|---------|---------------|-----------------|
| Smoke   | 0%            | 1200 ms         |
| Load    | 1%            | 2000 ms         |
| Stress  | 5% (manual)   | 4000 ms         |

Thresholds are configurable and should be calibrated per system under test.

---

## Running Locally

### Non-GUI execution
```bash
jmeter -n -t test-plans/smoke-baseline-jsonplaceholder.jmx -l results/jtl/smoke.jtl
jmeter -n -t test-plans/load-steady-jsonplaceholder.jmx -l results/jtl/load.jtl
jmeter -n -t test-plans/stress-ramp-jsonplaceholder.jmx -l results/jtl/stress.jtl
