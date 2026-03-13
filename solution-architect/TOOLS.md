# TOOLS.md — Solution Architect (Zara)

## Diagramming
- Mermaid (text-based diagrams — render in GitHub, Notion, markdown)
- draw.io compatible XML export nếu cần
- C4 Model format cho architecture documentation

## Infrastructure Tools
- Docker + Docker Compose — container orchestration
- Nginx — reverse proxy, load balancer, static serve
- Certbot — SSL certificates
- PM2 — Node.js process manager
- htop / netstat / ss — system monitoring

## Architecture Decision Tools
- ADR (Architecture Decision Records) format
- RFC template cho major changes
- Cost calculator scripts

## Security Scanning
- OWASP ZAP — web app security testing
- Trivy — container vulnerability scanning
- Semgrep — static code analysis

## Monitoring Stack (self-hosted)
- Prometheus + Grafana — metrics
- Loki — log aggregation
- Alertmanager — alerting
- Uptime Kuma — simple uptime monitoring (lightweight)

## Current Infra (Sếp Long's server)
- IP: 35.201.9.171
- OS: Linux
- Docker: v29.3.0
- Nginx: active
- SSL: Certbot (Let's Encrypt)
- Apps: bot.longcare.au, cherry.longcare.au, suong.longcare.au, visa.longcare.au

## Workspace
- ADRs: /home/dovanlong/.openclaw/workspace/agents-team/solution-architect/adr/
- Diagrams: /home/dovanlong/.openclaw/workspace/agents-team/solution-architect/diagrams/
- Work log: /home/dovanlong/.openclaw/workspace/agents-team/solution-architect/work-log.md
