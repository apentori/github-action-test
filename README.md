# github-action-test


## Sandboxing param 

````
[Unit]
Description=Github Action Self Hosted runner for {{ github_action_repository }}
Documentation=https://github.com/status-im/infra-role-github_action_runner;https://docs.github.com/en/actions/hosting-your-own-runners/
After=network.target

[Service]
User={{ github_runner_user }}
Group={{ github_runner_group }}
ExecStart={{github_action_runner_path}}/runsvc.sh
WorkingDirectory={{ github_action_runner_path }}
KillMode=process
KillSignal=SIGTERM
TimeoutStartSec={{ github_action_runner_timeout }}
TimeoutStopSec=5min

# Sandboxing restriction
ProtectHome=true
LogsDirectory=true
ProtectSystem=true
RuntimeDirectory=actions.runner.apentori-github-action-test.test-runner.service
LogsDirectory=true
ProtectKernelTunables=true
ProtectKernelModules=true
ProtectKernelLogs=true
ProtectControlGroups=true
RestrictSUIDSGID=true
KeyringMode=private
ProtectClock=true
RestrictRealtime=true
PrivateDevices=true
PrivateTmp=true
ProtectHostname=true

[Install]
WantedBy=multi-user.target
````
