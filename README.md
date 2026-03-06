# Copilot Premium Requests (xbar plugin)

xbar plugin to show your GitHub Copilot **premium interactions** quota usage in the macOS menu bar.

## Requirements

- macOS
- [xbar](https://xbarapp.com/)
- Python 3 (`python3`)
- A GitHub token that can access the Copilot usage endpoint this plugin calls.

## Install

1. Download/copy the plugin file `copilot_premium_requests.15m.py`.
2. Make it executable:

   ```bash
   chmod +x copilot_premium_requests.15m.py
   ```

3. Move it into your xbar plugins folder (xbar → **Open Plugins Folder**).
4. (Optional) Adjust refresh interval in xbar, or rename using the xbar convention:

   - `{name}.{time}.{ext}`
   - Example: `copilot_premium_requests.5m.py` refreshes every 5 minutes.

## Configure

This plugin reads the token from the xbar variable `VAR_GITHUB_TOKEN`.

1. In xbar, open plugin settings for `copilot_premium_requests.15m.py`.
2. Set `VAR_GITHUB_TOKEN` to your token value.

Security note: keep your token private and do not publish it.

## Output

- Normal: shows `used/total - percent`.
- Unlimited plans: shows `Copilot: ∞`.
- Errors: shows `Copilot: ?` and details in the dropdown.

## Troubleshooting

- **"Missing token"**: you have not set `VAR_GITHUB_TOKEN` in xbar settings.
- **HTTP Error: 401/403**: token is invalid, expired, or missing required access.
- **Timeout / network errors**: try again later; GitHub API/network may be temporarily unavailable.

## Questions

For doubts and questions, email: david@mundosaparte.com

## Development

Run it from the terminal to see raw output:

```bash
./copilot_premium_requests.15m.py
```

## How it works

The plugin calls:

- `https://api.github.com/copilot_internal/user`

and extracts `quota_snapshots.premium_interactions` to compute used/total/remaining.
