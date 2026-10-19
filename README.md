# svc-onboard

The third tenant of the Platform Factory reference build, and a placeholder:
it exists so that C-26 ("a new tenant is still one file", on the Config
Connector engine) has a real service repo to point at. It is owned by team
`checkout`, like `svc-ledger`. The workload is a stock unprivileged nginx
pulled through the platform's Docker Hub remote (ADR-0010); there is no
application code and no database claim here.

What C-26 measures is on the platform side: one `System` file in the
`systems` repo produces this service's namespace, quota, RBAC, Argo CD
project and Applications, Google service account and registry. This `k8s/`
directory is what the tenant's Application syncs, which is how "a running
workload" is checked: a Deployment admitted under the tenant's AppProject.

This tenant is temporary. It is offboarded, and its registry deleted by a
person, in M2b's cleanup (ADR-0015 §5, ADR-0019 §1).

## Who approves changes here

The same answer as `svc-ledger`'s README:
[`.github/CODEOWNERS`](.github/CODEOWNERS) names `@platform-factory/platform`,
because the owning team is a Google Group named once in this service's tenant
file, `systems/tenants/svc-onboard.yaml`
([ADR-0012 §3](https://github.com/platform-factory/platform-factory-concept/blob/main/docs/adr/0012-system-is-the-unit-team-is-a-field.md)).
How a team's own approval gets enforced is M3's question (claim C-09).

Part of the Platform Factory reference implementation; the design seed lives
at https://github.com/platform-factory/platform-factory-concept.

Platform Factory was designed and written by **Ronak Patel**
([thecloudgeek LLC](https://github.com/thecloudgeek)). Licensed Apache-2.0 —
the attribution to keep is in [NOTICE](NOTICE), and
[CITATION.cff](CITATION.cff) says how to cite it.
