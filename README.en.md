# WalkZone — iOS product case study

WalkZone turns outdoor walks into a competition for virtual street territories. Players record their route, gain server-validated territorial progress and compare their presence in city leaderboards.

**Author and product owner:** [Jonathan Amaral](https://github.com/Amaral-sci). Development used AI-assisted tools for implementation, debugging, testing and documentation.

**Stack:** Swift, SwiftUI, MapKit, Core Location, Core Motion, SwiftData, StoreKit 2, Supabase, PostgreSQL and TypeScript.

## Product

- GPS walking sessions and route summaries.
- Street-based territorial competition and city leaderboards.
- Experience, virtual currency and cosmetic customization.
- Optional Premium appearance and detailed territorial distance information.
- Apple/email authentication, guest access and account deletion.

<img src="mapa.png" width="250" alt="WalkZone territory map" /> <img src="perfil.png" width="250" alt="Player profile and progression" /> <img src="compartilhar.png" width="250" alt="Shareable walking summary" />

## Engineering focus

The project addresses interrupted activity recovery through local checkpoints, separation of local recording from server-confirmed rewards, idempotent processing, account-bound access and verification of Apple purchases. Rendering work is controlled according to screen visibility; extended energy and device testing remains ongoing.

This is a public portfolio, not a runnable source release. Production code, credentials, private configuration and player records are excluded. Screenshots are real test captures, not product-scale metrics. Private test practices described here are not a public CI certification or an independent security audit.

As of **October 26, 2026**, the app is available to TestFlight participants and version 1.0 (build 20) has been resubmitted for App Store review. Public release is not yet confirmed.

[Full presentation in Portuguese](README.md) · [Architecture](ARCHITECTURE.md) · [Engineering decisions](ENGINEERING.md) · [Website](https://www.walkzone.com.br)
