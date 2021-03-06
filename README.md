# maintainers-generator

> Parse OWNERS file across repositories to output YAML containing all the maintainers!

## Install

```console
go get github.com/leodido/mantainers-generator
```

## Usage

This is the CLI.

```console
Usage of ./bin/maintainers-generator:
  -app-id string
        ID of the GitHub app. If set, requires --app-private-key path to be set and --github-token-path to be unset.
  -app-private-key-path string
        Path to the private key of the github app. If set, requires --app-id to bet set and --github-token-path to be unset
  -dedupe
        Whether to dedupe or not sub-project areas for every maintainer. (default true)
  -dry-run
        Dry run for testing (uses API tokens but does not mutate). (default true)
  -github-endpoint value
        GitHub's API endpoint (may differ for enterprise). (default https://api.github.com)
  -github-graphql-endpoint string
        GitHub GraphQL API endpoint (may differ for enterprise). (default "https://api.github.com/graphql")
  -github-host string
        GitHub's default host (may differ for enterprise) (default "github.com")
  -github-token-path string
        Path to the file containing the GitHub OAuth secret.
  -hmac string
        Path to the file containing the GitHub HMAC secret. (default "/etc/webhook/hmac")
  -log-level string
        Log level. (default "info")
  -org string
        The GitHub organization name.
  -persons-db string
        The path to a JSON file containing handle => name/company mappings (default "data/data.json")
  -repo string
        The GitHub repository name.
  -sort
        Whether to sort the projects alphabetically. (default true)
  -version
        Print the version.
```

For example, you could run:

```console
./bin/maintainers-generator --github-token-path /etc/token --org falcosecurity
```

Which will output a YAML like:

```yaml
- name: user1
  github: https://github.com/user1
  company: UNKNOWN
  projects:
  - https://github.com/falcosecurity/falcosecurity/community
- name: user2
  github: https://github.com/user2
  company: UNKNOWN
  projects:
  - https://github.com/falcosecurity/falcosecurity/.github
  - https://github.com/falcosecurity/falcosecurity/advocacy
  - https://github.com/falcosecurity/falcosecurity/charts
  - https://github.com/falcosecurity/falcosecurity/client-go
  - https://github.com/falcosecurity/falcosecurity/client-rs
```

---

[![Analytics](https://ga-beacon.appspot.com/UA-49657176-1/maintainers-generator?flat)](https://github.com/igrigorik/ga-beacon)