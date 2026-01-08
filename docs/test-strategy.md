# Performance Test Strategy

## Why these tests
- Smoke: detect obvious latency spikes and availability issues quickly
- Load (steady): validate performance under expected concurrency
- Stress (ramp): identify thresholds and failure behavior for capacity planning

## Approach
- Use lightweight public endpoints for portfolio reproducibility
- Focus on repeatability, clear reporting, and interpretation of results
- Prefer p95 over averages to reflect real user experience

## Reporting
For each run, capture:
- Test configuration (threads, ramp-up, duration)
- Summary metrics (p95, throughput, error rate)
- Notable observations (degradation points, anomalies)