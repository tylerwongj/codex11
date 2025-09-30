# Live Ops: Telemetry, A/B Testing, Content Updates
- **Telemetry foundations:** Identify key metrics (DAU/MAU, retention cohorts, monetization events, critical gameplay funnels). Implement a lightweight analytics wrapper that queues events, retries on failure, and batches uploads.
- **Instrumentation discipline:** Define event naming conventions, version events, and enforce schema validation. Use ScriptableObjects or configuration files to manage analytics endpoints per environment.
- **A/B and multivariate testing:** Compare service providers (Remote Config, Firebase Remote Config, custom backend). Prototype a gameplay parameter split test and ensure guardrails exist to disable experiments quickly.
- **Content delivery:** Combine Addressables, remote config, and feature flags to roll out seasonal or live events without full client updates. Document review and approval workflows.
- **Monitoring and alerting:** Establish dashboards (DataDog, Grafana, Unity Analytics) and alert thresholds. Practice incident response by simulating a misconfigured event rollout.
- **Exercises:** Run a mock live event: release a new cosmetic via Addressables, collect telemetry, split traffic between variants, and produce a retrospective report.
- **Reference material:** Unity Gaming Services docs (Analytics, Remote Config); LiveOps GDC sessions; Google Play Console experiments guide.

## Telemetry Event Schema
```json
{
  "event": "level_complete",
  "player_id": "uuid",
  "level": 3,
  "duration_seconds": 187,
  "coins_collected": 42
}
```






## References
- [Unity LiveOps overview](https://unity.com/solutions/live-ops) - tools for operating live games.
- [Unity analytics manual](https://docs.unity.com/analytics/en/manual/overview) - setup and event tracking guidance.
- [Unity cloud diagnostics manual](https://docs.unity.com/cloud-diagnostics/en/manual/overview) - crash reporting and telemetry.
- [Unity analytics learning plan](https://learn.unity.com/plan/unity-analytics) - courses on dashboards and funnels.
- [LiveOps best practices talk](https://www.youtube.com/watch?v=20nQOsybU98) - GDC session on telemetry driven operations.
## Key Terms
- **Telemetry Event**: Structured payload describing player actions (e.g., `level_complete`) sent to analytics backends for insight.
- **DAU / MAU**: Daily and monthly active user metrics that reveal retention trends and growth health.
- **Analytics Wrapper**: Abstraction that queues events, batches uploads, and retries failures across multiple telemetry providers.
- **Remote Config Experiment**: Controlled rollout where parameters are varied per cohort to test gameplay or monetization hypotheses.
- **Addressables Release**: Content update tactic that delivers new assets from CDN without forcing a client patch.
- **Alert Threshold**: Monitoring rule that notifies the team when key metrics fall outside acceptable bounds during live operations.
- **Incident Response Drill**: Practice run where the team simulates a telemetry or rollout failure to refine playbooks before real emergencies.
