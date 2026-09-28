# Running the VPS panel on Replit

- Python Flask app: `main.py`. Start the **Start application** workflow, which runs `RUN_BOT=0 PORT=5000 python main.py`.
- Before the first run, add `PANEL_ADMIN_PASSWORD` as a Replit Secret. Log in as `admin` with that password. The password is hashed into `panel_data/master_config.json` on first run; changing the Secret later does not change an existing account password. Use the panel's Change Password setting for that.
- The workflow disables the optional Telegram bot. To use it later, configure its token and owner ID through the appropriate secret/settings flow and adjust the workflow; no Telegram account is required to use the web panel.
- State lives in `panel_data/` and is excluded from Git. Replit's preview proxies the Flask server at port 5000.
- This runs inside Replit's container, not on a dedicated VPS: host-level administration, privileged networking, extra public ports, Docker, and system package management may not function as on a VPS. Do not use the panel to expose untrusted shell access.