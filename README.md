# Homepage for LazyCat

- Original upstream https://github.com/gethomepage/homepage, initial release 2.7.0.
- Package `community.lazycat.app.homepage`, Linux amd64, minimum LazyCat OS 1.6.0.
- Official image `ghcr.io/gethomepage/homepage:v2.7.0` mirrored via `ghcr.1ms.run`, requiring matching target-platform digests.
- License GPL-3.0 from the tagged upstream LICENSE/API, rather than the inconsistent legacy Docker label.

## Configuration and access

Preserves the original image entrypoint and command. Runs as UID/GID 1000 with LazyCat persistent-directory ownership mapping, PUID/PGID 1000, port 3000 and IPv4 listener. `/lzcapp/var/config` maps to `/app/config`. The native configuration loader copies missing skeleton files without overwriting existing files. Maintain settings.yaml, services.yaml, bookmarks.yaml and widgets.yaml in that private directory; protect any user-added API credentials.

Homepage has no native account system. The application stays behind LazyCat authentication with no public-path exemption. No host port, host-system mount, Docker socket or other application data is exposed. The allowed-host list includes only the LazyCat application hostname, the internal service hostname and localhost health-check addresses; no wildcard is used. Optional API integrations need user configuration and connectivity. No real services are preconfigured or accessed during packaging.

## Publication and verification

The reusable workflow creates a versioned LPK Release asset. Both automatic private and official publishers are disabled. Only submit the independently verified URL/SHA256 to MiaoMiao community store after full alias/package/source duplicate checks.

No file-chooser interceptor, smoke job or runtime test gate is added. The image-native entrypoint and health check are preserved. Configuration/workflow checks, mirror verification and LPK SHA256 do not establish startup, default initialization, dashboard rendering, persistence across restart or service-widget connectivity. Those runtime behaviors remain unverified.
