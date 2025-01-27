Для работы нужно в панели управления Tailscale:
1. Включить в [панели DNS](https://login.tailscale.com/admin/dns) "Override local DNS" и Enable HTTPS.
2. Добавить в [ACL](https://login.tailscale.com/admin/acls/file):
   ```json
   "tagOwners": {
		"tag:internet": ["autogroup:admin"],
	},
    "nodeAttrs": [
		{
			"target": ["tag:internet"],
			"attr":   ["funnel"],
		},
   ```
3. [Добавить ключ,](https://login.tailscale.com/admin/settings/keys), прикрепив тег internet.
4. В /ts-config/serve.json выбрать, будет ли включен Funnel (в конфиге выключен).