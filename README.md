# Performance Testing with JMeter

## Overview
This repository contains performance testing scenarios using **Apache JMeter**, designed to demonstrate practical load testing strategy, metrics interpretation, and reproducible execution.

## What’s included
- Smoke baseline test plan
- Steady load test plan
- Stress/ramp test plan
- Documentation for metrics and acceptance criteria

## Test Plans
Located in `/test-plans`:
- `smoke-baseline-jsonplaceholder.jmx`
- `load-steady-jsonplaceholder.jmx`
- `stress-ramp-jsonplaceholder.jmx`

## How to run (CLI)
Install JMeter and run:

```bash
jmeter -n -t test-plans/smoke-baseline-jsonplaceholder.jmx -l results/smoke.jtl
jmeter -n -t test-plans/load-steady-jsonplaceholder.jmx -l results/load.jtl
jmeter -n -t test-plans/stress-ramp-jsonplaceholder.jmx -l results/stress.jtl