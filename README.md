<!-- start title -->

# GitHub Action:Test Go

<!-- end title -->
<!-- start description -->

Tests a golang project

<!-- end description -->
<!-- start contents -->
<!-- end contents -->
<!-- start usage -->

```yaml
- uses: catalystcommunity/action-test-go@undefined
  with:
    # Version of golang to use
    # Default: ~1.18
    go-version: ""

    # Directory to run the command from
    # Default: test
    working-directory: ""

    # Command to run before running tests. Can be used to configure private
    # repositories, etc
    # Default:
    pre-command: ""

    # Command to run
    # Default: go test -v
    command: ""
```

<!-- end usage -->
<!-- start inputs -->

| **Input**               | **Description**                                                                         | **Default**  | **Required** |
| :---------------------- | :-------------------------------------------------------------------------------------- | :----------: | :----------: |
| **`go-version`**        | Version of golang to use                                                                |   `~1.18`    |  **false**   |
| **`working-directory`** | Directory to run the command from                                                       |    `test`    |  **false**   |
| **`pre-command`**       | Command to run before running tests. Can be used to configure private repositories, etc |              |  **false**   |
| **`command`**           | Command to run                                                                          | `go test -v` |  **false**   |

<!-- end inputs -->
<!-- start outputs -->

| **Output**      | **Description** | **Default** | **Required** |
| :-------------- | :-------------- | ----------- | ------------ |
| `random-number` | Random number   |             |              |

<!-- end outputs -->
<!-- start examples -->

### Example usage

```yaml
on:
  pull_request:
    branches:
      - main
jobs:
  test:
    if: github.event.pull_request.draft == false
    name: Test
    runs-on: ubuntu-latest
    steps:
      - uses: crazy-max/ghaction-dump-context@v1
      - uses: catalystcommunity/action-test-go@v1
        with:
          pre-command: git config --global url."https://${{ secrets.AUTOMATION_PAT }}@github.com".insteadOf "https://github.com"
```

<!-- end examples -->
<!-- start [.github/ghdocs/examples/] -->
<!-- end [.github/ghdocs/examples/] -->
