# Future Work

## Larger shadow evaluation

Design a larger sample independently of the original regression cases. Measure harmful attribution, safe resolution, unresolved reasons, source-class performance, and manual-review burden without treating the test as a production deployment.

## Confidence calibration

Compare confidence categories with adjudicated outcomes. Evaluate whether thresholds separate supported, uncertain, and unsafe cases consistently across source classes.

## Safe recall improvement

Analyze the 25/30 unresolved outcomes by reason. Improve candidate discovery and verification coverage while keeping source binding, domain isolation, and publication gates fixed as regression constraints.

## Performance profiling

Measure runtime by stage, request counts, caching opportunities, retry behavior, and persistence costs. Optimize only with the evidence-safety suite running so speed changes cannot silently restore harmful publication.

## Web-volatility monitoring

Define fixture refresh rules and periodic live checks. Distinguish expected external change from workflow regression.

## Human-review workflow

Create clear escalation reasons, reviewer evidence views, and decision logging for ambiguous cases. Measure agreement and correction rates without exposing private evidence publicly.

## Release governance

Automate private/public-safe boundary checks, integrity manifests, and documentation claim audits within the authorized environment.

## Evidence boundary

Future results must remain explicit about sample design, deployment status, validation independence, and unresolved outcomes. Broader claims require broader evidence.
