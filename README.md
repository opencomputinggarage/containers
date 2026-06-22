# containers

Container images maintained by Open Computing Garage. Each image lives in its
own directory under `containers/` and is released to GHCR when the
`org.opencontainers.image.version` label in its `Dockerfile` changes on `main`.

## Images

| Image | Description | Registry |
|-------|-------------|----------|
| jenkins-inbound-agent | Jenkins inbound agent with sshpass and AWS CLI v2 baked in | `ghcr.io/opencomputinggarage/jenkins-inbound-agent` |
| logstash-with-opensearch-plugin | Logstash with the `logstash-output-opensearch` plugin baked in, for ECK | `ghcr.io/opencomputinggarage/logstash-with-opensearch-plugin` |

## Release

Releases are driven by `.github/workflows/release-containers.yml`. Bump the
`org.opencontainers.image.version` label in the relevant `Dockerfile` and push
to `main`; the workflow builds and pushes the image if that version does not
already exist on GHCR. Manual runs are available via workflow dispatch.

```bash
# jenkins-inbound-agent
docker pull ghcr.io/opencomputinggarage/jenkins-inbound-agent:3355.v388858a_47b_33-19

# logstash-with-opensearch-plugin
docker pull ghcr.io/opencomputinggarage/logstash-with-opensearch-plugin:8.19.0
```
