# Network rules

Shared YAML rule sets for Mihomo and Stash, imported from the existing Ninkear Mihomo configuration. Lists contain matching conditions only; routing policies remain in each client configuration.

Use `behavior: classical` and `format: yaml`. Raw URLs follow:

`https://raw.githubusercontent.com/mikhail-fedosenko/network-rules/main/rules/instagram.yaml`

Mihomo example:

```yaml
rule-providers:
  instagram:
    type: http
    behavior: classical
    format: yaml
    url: https://raw.githubusercontent.com/mikhail-fedosenko/network-rules/main/rules/instagram.yaml
    path: ./http-rules/instagram.yaml
    interval: 3600
rules:
  - RULE-SET,instagram,PROXY
```

Stash uses the same URL, behavior, format, and interval; omit `type: http`.

## Lists

- `openai`, `grok`, `gemini`, `claude`: AI services, including some shared endpoints.
- `jetbrains`, `spotify`, `instagram`: service domains and associated endpoints.
- `misc`: shared miscellaneous domains, including Firebase App Distribution, Surfshark, news sites, and Cloudflare Radar.
- `surfshark`: service domains.
- `surfshark-webrtc`: existing WebRTC IP rule. Reference using `RULE-SET,surfshark-webrtc,PROXY,no-resolve` to preserve its original behavior.
- `additional-services`: Majestic, Semrush, Ahrefs, and Moz. Shared entries live in `misc`; reference `misc` first.

The initial import preserves existing matching conditions, including shared third-party endpoints. It is not a claim that the lists are complete or exclusively match one service. Disabled rules were not imported.

Changes to `main` are consumed automatically by configured clients at their next update. Do not commit credentials or full private client configurations.
