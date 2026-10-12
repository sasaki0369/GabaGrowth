# Gaba Growth Firebase sync — Android 2.6 / Web 1.9

Firebase project: **gabagrowth** (separate from ogawa-machida)
Database: https://gabagrowth-default-rtdb.asia-southeast1.firebasedatabase.app
Android package: jp.gabagrowth.walk

## Console setup
1. Authentication > Sign-in method: enable **Email/Password** (Google enabled alone is insufficient for these builds).
2. Authentication > Users: Add user; use same credentials on Android and Web.
3. Realtime Database > Rules: replace the CURRENT temporary public rules in the **gabagrowth** project with firebase-rules.json (no other nodes currently shown). Confirm no other data exists before replacing.
4. Deploy Android ZIP to sasaki0369/GabaGrowth-Android, and Web ZIP contents to sasaki0369/GabaGrowth.
5. Sign in on Android and Web with the same email/password. Finish a walk, sync Android, then refresh Web sync.

## Scope and safety
- Android uploads walkSessions to /gabaGrowth/users/{uid}/walkSessions/{sessionId}.
- Web downloads and deduplicates these sessions into the existing local studyLogs.
- Other Web study records remain local, not cloud synchronized; this is not full bidirectional sync.
- The prior ogawa-machida project is not touched.
- GitHub Actions workflow included. Stable APK signing still requires GABA_KEYSTORE_* secrets.
- This source has not been built or tested against live Firebase in this environment.
