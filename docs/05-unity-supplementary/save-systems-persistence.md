# Save Systems and Persistence Strategies, Including Cloud Saves
- **Persistence layers:** Map local save formats (JSON, binary, ScriptableObjects, SQLite) and note when to encrypt or compress data. Document serialization libraries (e.g., Odin Serializer, Newtonsoft JSON) and choose a default approach.
- **Versioning and migrations:** Design a schema versioning strategy. Prototype a migration pipeline that upgrades old save data safely and logs failures for analysis.
- **Platform integration:** Investigate console certification rules and mobile platform storage limits. Determine where saves live on each target platform and plan fallback paths when storage is unavailable.
- **Cloud sync considerations:** Evaluate cloud providers (Unity Cloud Save, PlayFab, Firebase, custom REST). Document authentication flows, conflict resolution policies, and offline-first strategies.
- **Security and privacy:** Define data retention policies, GDPR/CCPA obligations, and sensitive data handling. Align with backend/cloud teams to ensure compliance.
- **Exercises:** Build a save/load module with checksum validation, automated regression tests, and a mocked cloud sync process that handles conflicts.
- **Reference material:** Unity Manual — Persistence and Serialization; PlayFab documentation; platform TRCs/TCRs for storage requirements.

## Save Payload Example
```json
{
  "playerLevel": 12,
  "inventory": ["sword", "potion"],
  "position": { "x": 4.2, "y": 1.0, "z": -3.5 }
}
```






## References
- [Persistence and saving data manual](https://docs.unity3d.com/Manual/persistence-saving-data.html) - overview of serialization strategies in Unity.
- [PlayerPrefs scripting reference](https://docs.unity3d.com/ScriptReference/PlayerPrefs.html) - API for simple local storage.
- [JSON serialization manual](https://docs.unity3d.com/Manual/JSONSerialization.html) - serialize data using JSONUtility.
- [Save and load data tutorial](https://learn.unity.com/tutorial/save-and-load-data) - step-by-step creation of a save system.
- [Save and load game video](https://www.youtube.com/watch?v=XOjd_qU2Ido) - Brackeys tutorial on persistence workflows.
## Key Terms
- **Serialization Format**: Structure used to persist data—JSON, binary, ScriptableObjects, or SQLite—chosen for readability, speed, and platform support.
- **Schema Version**: Integer or GUID stored alongside save data that signals which migrations need to run when formats change.
- **Migration Pipeline**: Set of upgrade steps that converts legacy saves to the latest schema while logging errors safely.
- **Cloud Sync Provider**: Remote service such as Unity Cloud Save or PlayFab that stores backups, resolves conflicts, and authenticates players.
- **Checksum Validation**: Hash stored with each save slot so the game can detect corruption or tampering before loading data.
- **Data Retention Policy**: Guideline describing how long player data is stored, when it is deleted, and how privacy regulations are honored.
