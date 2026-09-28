# claude-azure-agents

Claude Code-plugin med fire subagents for Azure-integrasjonsarbeid:

| Agent | Rolle |
|-------|-------|
| `azure:designer` | Arkitektur, datamapping, GDPR, feilscenarier — før koding |
| `azure:coder` | Implementerer Azure Functions / Logic App-workflows fra spec |
| `azure:tester` | Enhets- og integrasjonstester, mocks, grensetilfeller |
| `azure:qa` | Uavhengig gjennomgang: kode, tester, sikkerhet, konvensjoner |

## Installasjon

I en Claude Code-sesjon (i et hvilket som helst repo):

```
/plugin marketplace add <github-bruker>/claude-azure-agents
/plugin install azure@claude-azure-agents
```

Bytt ut `kjetilsvihus` med kontoen eller organisasjonen repoet ligger under.

## Bruk

Agentene delegeres automatisk basert på `description`, eller kalles eksplisitt:

> For denne integrasjonsbestillingen: bruk azure:designer til å lage en spec,
> azure:coder til å implementere, azure:tester til å skrive tester, og
> azure:qa til gjennomgang.

## Oppdatering

Etter endringer i dette repoet — bump `version` i
`plugins/azure/.claude-plugin/plugin.json`, så henter teamet det med:

```
/plugin marketplace update claude-azure-agents
claude plugin update azure@claude-azure-agents
```

## Tilpasning per integrasjon

Legg integrasjonsspesifikke konvensjoner i `CLAUDE.md` og `.claude/settings.json`
i det enkelte integrasjonsrepoet. Pluginet bærer de gjenbrukbare agentene;
repoet bærer domenekonteksten.
