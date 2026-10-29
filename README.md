<h1 align="center">Lygia Teixeira</h1>

<p align="center">
  <strong>Blue Team · Incident Response · Hardening · Observabilidade</strong><br>
  CompTIA Security+ · Pós em AppSec & DevSecOps (em andamento) · Fortaleza, CE — Brasil
</p>

<p align="center">
  <a href="https://linkedin.com/in/lygia-teixeira"><img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
  <a href="mailto:lygia.tsf@gmail.com"><img src="https://img.shields.io/badge/Email-EA4335?style=for-the-badge&logo=gmail&logoColor=white" alt="Email"></a>
</p>

---

Eu protejo ambientes de produção reais: **mais de 200 sites WordPress em 7 servidores Linux/cPanel**. Faço a detecção, contenho o incidente, encontro a causa raiz e deixo uma automação para que ele não se repita.

- 🔎 **Detecção:** stack de observabilidade (Grafana · Prometheus · Loki · Alloy) com alertas de CPU, memória, disco e servidor offline
- 🚨 **Resposta a incidentes:** remoção de webshells e backdoors, análise de logs HTTP, contenção e pós-incidente documentado
- 🛡️ **Hardening:** baselines de servidor e de cabeçalhos HTTP, firewall (CSF/lfd), WAF e TLS
- ⚙️ **Automação:** Python, Node.js, Bash e n8n para tirar tarefas de segurança do modo manual

---

## 🧰 Stack

**Segurança**
![Wazuh](https://img.shields.io/badge/Wazuh-005571?style=flat)
![Wireshark](https://img.shields.io/badge/Wireshark-1679A7?style=flat&logo=wireshark&logoColor=white)
![Nmap](https://img.shields.io/badge/Nmap-4682B4?style=flat)
![Trivy](https://img.shields.io/badge/Trivy-1904DA?style=flat&logo=aquasec&logoColor=white)
![CSF](https://img.shields.io/badge/CSF%20%2F%20lfd-555?style=flat)
![Vaultwarden](https://img.shields.io/badge/Vaultwarden-175DDC?style=flat&logo=bitwarden&logoColor=white)

**Infra & Cloud**
![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat&logo=linux&logoColor=black)
![AWS](https://img.shields.io/badge/AWS-232F3E?style=flat&logo=amazonwebservices&logoColor=white)
![Terraform](https://img.shields.io/badge/Terraform-7B42BC?style=flat&logo=terraform&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat&logo=docker&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-2088FF?style=flat&logo=githubactions&logoColor=white)
![Cloudflare](https://img.shields.io/badge/Cloudflare-F38020?style=flat&logo=cloudflare&logoColor=white)
![cPanel](https://img.shields.io/badge/cPanel%2FWHM-FF6C2C?style=flat&logo=cpanel&logoColor=white)

**Observabilidade**
![Grafana](https://img.shields.io/badge/Grafana-F46800?style=flat&logo=grafana&logoColor=white)
![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?style=flat&logo=prometheus&logoColor=white)
![Loki](https://img.shields.io/badge/Loki-F2CC0C?style=flat&logo=grafana&logoColor=black)

**Código & Automação**
![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat&logo=nodedotjs&logoColor=white)
![Bash](https://img.shields.io/badge/Bash-4EAA25?style=flat&logo=gnu-bash&logoColor=white)
![PHP](https://img.shields.io/badge/PHP-777BB4?style=flat&logo=php&logoColor=white)
![n8n](https://img.shields.io/badge/n8n-EA4B71?style=flat&logo=n8n&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat&logo=mysql&logoColor=white)

**Frameworks:** MITRE ATT&CK · NIST CSF · ISO/IEC 27001 · LGPD

---

## 📂 Projetos

| Projeto | O que resolve | Stack |
|---|---|---|
| [**lacrei-devops-challenge**](https://github.com/lygia-teixeira/lacrei-devops-challenge) | Pipeline de deploy seguro na AWS: OIDC sem chaves fixas, scan Trivy bloqueante, aprovação manual para produção, rollback e alarmes | Terraform · GitHub Actions · Docker · EC2 · CloudWatch |
| [**security-scripts**](https://github.com/lygia-teixeira/security-scripts) | Scanner de malware PHP, analisador de logs HTTP (SQLi, XSS, LFI, força bruta, scanners) e checklist de hardening WordPress | Python (stdlib) · Bash |
| [**popup-go**](https://github.com/lygia-teixeira/popup-go) | Plugin WordPress de pop-ups com carrossel, segmentação por página e entrada sanitizada (nonce, capability, whitelist) | PHP · JavaScript · WordPress API |

---

## 🚨 Casos reais (anonimizados)

> Resumos de incidentes em que atuei em ambiente de produção. Os nomes de clientes e de servidores foram omitidos.

**Falso CAPTCHA "ClickFix" injetado via plugin de pop-up**
Vários sites passaram a exibir uma página falsa de verificação da Cloudflare que induzia o visitante a executar um comando no próprio computador. A injeção vinha da configuração de um plugin de pop-ups.
*Resposta:* identifiquei o vetor e os indicadores nos logs de acesso, limpei as configurações afetadas e mapeei os outros sites com o mesmo padrão.

**Webshells que sobreviveram à reinstalação do WordPress**
O site foi reinstalado e voltou a ser comprometido, porque os arquivos maliciosos estavam fora da árvore do WordPress, na home da conta.
*Resposta:* varredura completa da home, quarentena de cerca de 40 artefatos com a cadeia de evidência preservada e recomendação de rotação de credenciais.

**Firewall bloqueando a própria ferramenta de gestão**
Sites "caíram" em massa no painel de gerenciamento. A causa raiz era o lfd/CSF banindo o IP da ferramenta por um falso positivo de regra do mod_security.
*Resposta:* correlação entre os logs do firewall e os do WAF, liberação permanente e controlada do IP e replicação do ajuste nos demais servidores.

**Degradação de servidor por saturação do Apache**
Lentidão generalizada causada por tráfego anômalo vindo de um único NAT, com o MPM prefork saturado.
*Resposta:* diagnóstico pelos logs, migração para o `mpm_event` e remoção de cópias de diretórios expostas publicamente.

---

## 🎓 Formação

- 📚 Pós-graduação em AppSec e DevSecOps — em andamento
- Defesa Cibernética

## 🏅 Certificações

- CompTIA Security+ (2026)
- Google Cybersecurity Professional Certificate (2024)
- Hackers do Bem — Governo Federal (2024)
- ISO/IEC 27001 Associate (2023)
- Analista de Infra e Redes — CECyber (2025)
- Santander Bootcamp Cibersegurança #2 (2025)

---

<p align="center"><sub>Segurança na prática, não só no papel.</sub></p>
