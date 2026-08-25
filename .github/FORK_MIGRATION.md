# Fork migration record

Migration date: 2026-08-25

## Repository roles

- Development fork: `hhhappb/dsh-desktop`
- Upstream: `anywhere-labs/dsh-desktop`
- Preserved backup: `hhhappb/deepseek-harness-desktop`
- Migration branch: `codex/migrate-hhhappb-customizations`

The backup repository remains unchanged. The development repository is a real GitHub fork whose parent and source are both `anywhere-labs/dsh-desktop`.

## Customization audit

The backup repository imported the desktop baseline in commit `d6faaf3234e20605c95159e54f50c13db8bba612`. Its three later commits were audited through `9569aa75d68c6e4ff701b0ad427735584c1cba92`.

The behavior changes from the old `0.1.0-rc.8` runtime already exist in the new upstream's `0.1.1-rc.2` implementation:

| Preserved behavior | Current upstream implementation |
| --- | --- |
| Empty Cordis patch files are accepted | `patches/dsh-app-boot@0.1.1-rc.2.patch` |
| Windows native directory picker and validation | `patches/dsh-client-ui-directory-picker-browse@0.1.1-rc.2.patch` |
| Workspace drop target marker | `patches/dsh-client-ui-workspace@0.1.1-rc.2.patch` |
| Ignore empty DeepSeek tool-call identifiers and names | `patches/dsh-llm-deepseek@0.1.1-rc.2.patch` |
| Hidden Windows sandbox process window | `patches/dsh-sandbox-windows-acl@0.1.1-rc.2.patch` |
| Safe browser launch from Electron Node mode | `patches/dsh-web-app@0.1.1-rc.2.patch` |

No old patch or package pin is copied because doing so would downgrade DeepSeek Harness from `0.1.1-rc.2` to `0.1.0-rc.8` and duplicate behavior already maintained upstream. The documentation hash-only commit also requires no port because the new upstream owns its current bilingual documents and hashes.

## Sync and release boundary

Use GitHub's **Sync fork** action to bring upstream commits into this fork, preferably through a review branch or pull request when local changes exist. Syncing a fork updates Git commits; it does not copy GitHub Releases, release assets, secrets, environments, or workflow run history.

GitHub Actions was enabled for the development fork on 2026-08-25. Migration changes are validated through the fork's pull-request workflow before merging.

Installer publishing and the application's update/download channel therefore require a separate fork-owned release setup. Do not repoint the update checker until the fork has a stable version endpoint and platform artifacts ready for the same version.
