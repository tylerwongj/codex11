# Networking Options: Netcode for GameObjects, Mirror, Photon
- **Networking models:** Survey authoritative vs. peer-to-peer architectures. Document latency budgets, rollback requirements, and input handling strategies relevant to your genre.
- **Netcode for GameObjects (NGO):** Prototype a small co-op scene using NGO. Focus on NetworkObjects, RPC types, NetworkVariable synchronization, and scene management. Capture pain points such as bandwidth usage and host migration gaps.
- **Mirror:** Explore Mirror's UNet-derived API. Compare setup effort, transport choices (Telepathy, kcp), and community ecosystem (addons like FizzySteamworks). Identify scenarios where Mirror's flexibility outweighs NGO's first-party integrations.
- **Photon Fusion / PUN:** Review Photon-hosted services, pricing tiers, and server authority models. Implement a simple matchmaking flow and note data privacy implications. Evaluate how Photon tooling fits with your deployment constraints.
- **Decision matrix:** Build a comparison table covering licensing costs, platform support, dedicated server requirements, and debugging tooling. Recommend a default networking stack for prototypes vs. production.
- **Exercises:** Create a latency simulation harness (e.g., Unity's Network Simulator) and record how each framework handles packet loss or high ping during a basic interaction test.
- **Reference material:** Official docs for NGO, Mirror, and Photon; Unity Multiplayer samples; GDC talks on netcode architecture.

## Netcode Bootstrap
```csharp
private void Start()
{
    if (IsServer)
    {
        NetworkManager.Singleton.StartServer();
    }
}
```






## References
- [Unity multiplayer docs](https://docs-multiplayer.unity3d.com/) - documentation for Netcode and multiplayer services.
- [Netcode for GameObjects overview](https://docs-multiplayer.unity3d.com/netcode/current/about) - architecture of Unity Netcode.
- [Mirror networking docs](https://mirror-networking.com/docs/) - open-source networking stack documentation.
- [Fish-Networking docs](https://fish-networking.gitbook.io/docs/) - community-driven networking framework.
- [Unity multiplayer options talk](https://www.youtube.com/watch?v=rgFOmA0QW6I) - session comparing Unity networking solutions.
## Key Terms
- **Authoritative Server**: Networking model where a central server validates all game state to prevent cheating and resolves conflicts.
- **Netcode for GameObjects (NGO)**: Unity's first-party framework built around `NetworkObject`, RPCs, and `NetworkVariable` syncing.
- **NetworkObject**: Component in NGO designating which GameObjects replicate across clients and the server.
- **Mirror Networking**: Community-driven successor to UNet offering flexible transports and a familiar high-level API.
- **Photon Fusion / PUN**: Managed networking services from Photon that supply relay, matchmaking, and hosted authoritative infrastructure.
- **Network Simulator**: Tool for injecting latency and packet loss so you can benchmark how each framework behaves under stress.
- **Decision Matrix**: Comparison chart weighing cost, platform support, and dev effort to choose a networking stack for prototypes or launch.
