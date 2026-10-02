# TryHackMe - Writeups & Security Notes

<div align="center">

[![Português](https://img.shields.io/badge/Português-gray?style=for-the-badge)](#versão-em-português)
[![English](https://img.shields.io/badge/English-gray?style=for-the-badge)](#english-version)

</div>

<br />

> **Boas-vindas!** Este repositório reúne meus laboratórios práticos, write-ups de desafios e anotações teóricas focados em Operações de SOC e defesa em Blue Team.  
> *Clique nos botões de idioma acima ou navegue pelos índices abaixo para ir direto para o idioma/sala desejada.*

> **Welcome!** This repository brings together my hands-on labs, challenge write-ups, and theoretical notes focused on SOC Operations and Blue Team defense.  
> *Click the language buttons above or use the indexes below to jump directly to your preferred language/room.*

---

## Versão em Português

### Índice de Salas

| Nível | Sala / Desafio | Tópicos Chave | Link de Atalho |
| :---: | :--- | :--- | :---: |
| Iniciante | **Introdução à Segurança Defensiva** | SOC, Monitoramento, Firewall | [Ir para Writeup](#introdução-à-segurança-defensiva-pt) |
| Iniciante | **Introdução à Segurança Ofensiva** | Pentesting, Dirbuster, Web | [Ir para Writeup](#introdução-à-segurança-ofensiva-pt) |
| Iniciante | **Habilidades de Busca: Bases de Dados de Vulnerabilidades** | CVE, Pontuação CVSS, SQLi | [Ir para Writeup](#habilidades-de-busca-bases-de-dados-de-vulnerabilidades-pt) |
| Iniciante | **Habilidades de Busca: Localizar Detalhes do Servidor** | OSINT, Shodan, Banner Grabbing | [Ir para Writeup](#habilidades-de-busca-localizar-detalhes-do-servidor-pt) |
| Iniciante | **Habilidades de Busca: Análise de Malware** | VirusTotal, Análise de Malware | [Ir para Writeup](#habilidades-de-busca-análise-de-malware-pt) |

---

### Introdução à Segurança Defensiva (PT)

![Tags](https://img.shields.io/badge/Tópicos-SOC%20%7C%20Monitoring%20%7C%20Firewall%20%7C%20Incident%20Response-4169E1)

<details>
<summary><b>Ver Investigação Completa e Conceitos</b></summary>

#### 1. Cenário
Como analista SOC aprendiz, o objetivo foi investigar e conter uma atividade de rede suspeita envolvendo varreduras automatizadas e não autorizadas por páginas ocultas na aplicação.

#### 2. Conceitos Aprendidos
- **Segurança Defensiva:** Processo contínuo de proteção, monitoramento e mitigação de ameaças contra dispositivos e sistemas.
- **Análise de Alertas em SOC:** Identificação e triagem de padrões de tráfego anômalos por meio de dashboards de monitoramento.
- **Contenção Rápida de Ameaças:** Aplicação imediata de regras de bloqueio de IP no firewall para interromper ataques ativos.

#### 3. Investigação Passo a Passo
1. **Revisão de Alertas:** Abertura do painel de monitoramento para analisar os alertas recentes e detectar a atividade suspeita na rede.
2. **Identificação do Atacante:** Mapeamento do IP de origem malicioso direto dos logs de alerta.
3. **Análise de Requisições:** Acesso à lista *"URL Discovery Attempts"* para examinar o histórico do atacante e rastrear o rastreamento rápido de diretórios.
4. **Classificação do Ataque:** Inspeção da última entrada da lista para determinar a técnica exata utilizada no ataque.
5. **Acesso ao Painel de Controle:** Navegação até o painel de ações práticas de segurança e controle de acesso.
6. **Contenção:** Configuração e aplicação de uma regra de firewall bloqueando o IP do atacante.

#### 4. Ações Recomendadas
- **Bloqueio de IP:** Adicionar o IP do atacante às regras definitivas do firewall.
- **Limitador de Taxa (Rate Limiting):** Implementar restrições de requisições por segundo para bloquear ataques de força bruta a diretórios.
- **Políticas de Controle de Acesso:** Fortalecer e auditar endpoints sensíveis.
- **Correção de Vulnerabilidades:** Realizar auditoria no código para corrigir as falhas que expuseram a estrutura de diretórios.

</details>

[Λ Voltar ao topo](#tryhackme---writeups--security-notes)

---

### Introdução à Segurança Ofensiva (PT)

![Tags](https://img.shields.io/badge/Tópicos-Pentesting%20%7C%20Directory%20Bruteforce%20%7C%20Broken%20Access%20Control-4169E1)

<details>
<summary><b>Ver Investigação Completa e Conceitos</b></summary>

#### 1. Cenário
O objetivo foi assumir a perspectiva de um atacante para encontrar fragilidades na aplicação web *FakeBank*, demonstrando os riscos da segurança baseada em obscuridade e falhas de controle de acesso.

#### 2. Conceitos Aprendidos
- **Segurança Ofensiva (Pentesting):** Adoção da mentalidade de um atacante para identificar e explorar vulnerabilidades antes de agentes maliciosos.
- **Força Bruta de Diretórios Web:** Uso de ferramentas como `Dirbuster` / `Dirb` para mapear arquivos e endpoints ocultos no servidor web via wordlists.
- **Segurança por Obscuridade:** Entendimento de por que esconder endpoints sem autenticação real não garante a segurança da aplicação.

#### 3. Investigação Passo a Passo
1. **Mapeamento de Endpoints:** Execução do `dirb` no terminal direcionado à URL da aplicação web bancária para localizar caminhos ocultos.
2. **Análise de Descobertas:** Análise da lista de diretórios expostos retornados pela ferramenta.
3. **Exploração da Falha:** Navegação até a URL descoberta, inserção do número da conta e realização do depósito sem qualquer validação de autenticação.

#### 4. Ações Recomendadas
- **Controle de Acesso Robusto:** Exigir autenticação do lado do servidor antes de permitir acesso a endpoints financeiros (ex: `/bank-transfer`).
- **Eliminar Segurança por Obscuridade:** Garantir que páginas sensíveis possuam checagem de sessão rigorosa.
- **Autorização em Transações:** Validar rigorosamente a propriedade da conta e o token da sessão antes de processar qualquer depósito/transferência.
- **Desativar Listagem de Diretórios:** Configurar o servidor web para ocultar o índice de diretórios e remover páginas de teste do ambiente de produção.

</details>

[Λ Voltar ao topo](#tryhackme---writeups--security-notes)

---

### Habilidades de Busca: Bases de Dados de Vulnerabilidades (PT)

![Tags](https://img.shields.io/badge/Tópicos-Vulnerability%20Management%20%7C%20CVE%20%7C%20SQL%20Injection-4169E1)

<details>
<summary><b>Ver Investigação Completa e Conceitos</b></summary>

#### 1. Cenário
Consultar bases de dados públicas de vulnerabilidades para analisar o código identificador, pontuação de severidade e produtos afetados por uma falha de segurança conhecida.

#### 2. Conceitos Aprendidos
- **Common Vulnerabilities and Exposures (CVE):** Padrão do mercado para catalogação de vulnerabilidades conhecidas (`CVE-ANO-NÚMERO`).
- **Métricas e Severidade:** Utilização das pontuações CVSS (impacto, complexidade e explorabilidade) para priorização na gestão de patches.
- **SQL Injection (SQLi):** Noções de falhas de injeção de código SQL e formas de mitigação.

#### 3. Investigação Passo a Passo
1. **Busca na Base:** Pesquisa do identificador CVE específico na base pública de vulnerabilidades.
2. **Análise de Impacto:** Avaliação da pontuação de risco, métodos de exploração, requisitos de impacto e soluções fornecidas.

#### 4. Ações Recomendadas
- **Atualização de Software:** Atualizar a aplicação *Apache WebPortal* para a versão corrigida mais recente.
- **Consultas Parametrizadas:** Implementar *Prepared Statements* no código para mitigar permanentemente riscos de SQL Injection.

</details>

[Λ Voltar ao topo](#tryhackme---writeups--security-notes)

---

### Habilidades de Busca: Localizar Detalhes do Servidor (PT)

![Tags](https://img.shields.io/badge/Tópicos-OSINT%20%7C%20Shodan%20%7C%20Reconnaissance%20%7C%20Banner%20Grabbing-4169E1)

<details>
<summary><b>Ver Investigação Completa e Conceitos</b></summary>

#### 1. Cenário
Verificar e correlacionar o endereço IP de um servidor web Apache exposto à internet utilizando serviços de scanner e inteligência de ameaças.

#### 2. Conceitos Aprendidos
- **Banners e OSINT com Shodan:** Utilização de motores de busca direcionados a dispositivos conectados (IoT, servidores, câmeras) para inteligência de ameaças sem interação direta.
- **Exposição de Servidores Web:** Riscos associados à exposição de versões detalhadas de servidores populares como Apache em ambientes abertos.

#### 3. Investigação Passo a Passo
1. **Varredura e Mapeamento:** Pesquisa do serviço Apache na ferramenta TryScanMe e seleção do primeiro registro para verificar a resolução do IP.
2. **Identificação de Domínio:** Identificação do domínio exposto associado ao endereço IP (`trychackme.thm`).

#### 4. Ações Recomendadas
- **Ofuscação de Banners (Banner Grabbing Protection):** Alterar os cabeçalhos do Apache para ocultar a versão exata do software e do sistema operacional.
- **Páginas de Erro Personalizadas:** Remover detalhes e rastros do servidor das páginas padrão de erro HTTP (ex: 404, 500).

</details>

[Λ Voltar ao topo](#tryhackme---writeups--security-notes)

---

### Habilidades de Busca: Análise de Malware (PT)

![Tags](https://img.shields.io/badge/Tópicos-Threat%20Intelligence%20%7C%20VirusTotal%20%7C%20Malware%20Analysis-4169E1)

<details>
<summary><b>Ver Investigação Completa e Conceitos</b></summary>

#### 1. Cenário
Analisar um arquivo executável suspeito para determinar seu nível de ameaça e potencial malicioso com o auxílio de mecanismos de detecção multimotores.

#### 2. Conceitos Aprendidos
- **Análise Multimotor com VirusTotal:** Avaliação do nível de reputação de arquivos, URLs e domínios cruzando dados de dezenas de motores antivírus.
- **Indicadores de Comprometimento (IoCs):** Utilização da reputação do arquivo para extrair dados valiosos no combate a campanhas maliciosas.

#### 3. Investigação Passo a Passo
1. **Pesquisa do Artefato:** Consulta pelo arquivo `invoice_payment.exe` na ferramenta de detecção TryDetectMe.
2. **Avaliação dos Fornecedores:** Inspeção do relatório de detecção dos motores de segurança.
3. **Métrica de Risco:** Confirmação de alto risco após 52 de 72 motores classificarem o arquivo como malicioso.

#### 4. Ações Recomendadas
- **Bloqueio de Hash:** Adicionar a hash do arquivo `invoice_payment.exe` às listas de bloqueio da solução de EDR e Antivírus corporativo.
- **Conscientização em Segurança:** Treinar colaboradores para identificar e reportar e-mails de phishing com cobranças ou faturas falsas.

</details>

[Λ Voltar ao topo](#tryhackme---writeups--security-notes)

---

## English Version

### Room Index

| Level | Room / Challenge | Key Topics | Shortcut Link |
| :---: | :--- | :--- | :---: |
| Beginner | **Defensive Security Intro** | SOC, Monitoring, Firewall | [Go to Writeup](#defensive-security-intro-en) |
| Beginner | **Offensive Security Intro** | Pentesting, Dirbuster, Web | [Go to Writeup](#offensive-security-intro-en) |
| Beginner | **Search Skills: Vuln DBs** | CVE, CVSS Score, SQLi | [Go to Writeup](#search-skills-vulnerability-databases-en) |
| Beginner | **Search Skills: Server Details** | OSINT, Shodan, Banner Grabbing | [Go to Writeup](#search-skills-find-server-details-en) |
| Beginner | **Search Skills: Malware Analysis** | VirusTotal, Malware Analysis | [Go to Writeup](#search-skills-malware-analysis-en) |

---

### Defensive Security Intro (EN)

![Tags](https://img.shields.io/badge/Topics-SOC%20%7C%20Monitoring%20%7C%20Firewall%20%7C%20Incident%20Response-4169E1)

<details>
<summary><b>View Full Investigation & Concepts</b></summary>

#### 1. Scenario
As an apprentice SOC analyst, the objective was to investigate and contain suspicious network activity involving unauthorized, automated directory probing on a web application.

#### 2. Concepts Learned
- **Defensive Security:** The continuous process of defending, monitoring, and mitigating threats against systems and networks.
- **SOC Alert Analysis:** Identification and triage of anomalous traffic patterns through monitoring dashboards.
- **Rapid Threat Containment:** Immediate application of firewall blocking rules to halt active malicious activity.

#### 3. Step-by-Step Investigation
1. **Alert Review:** Opened the monitoring dashboard to review recent alerts and spot suspicious network activity.
2. **Attacker Identification:** Extracted the malicious source IP address directly from alert logs.
3. **Request Inspection:** Accessed the *"URL Discovery Attempts"* list to analyze the attacker's history and track rapid directory probing.
4. **Attack Classification:** Examined the latest log entry to pinpoint the exact attack pattern being performed.
5. **Security Panel Access:** Navigated to the security action panel where firewall and access rules are managed.
6. **Threat Containment:** Configured and applied a firewall rule to block the attacker's IP.

#### 4. Recommended Actions
- **IP Blocking:** Permanently enforce the attacker's IP block in the firewall configuration.
- **Rate Limiting:** Implement request rate limits to restrict rapid automated URL discovery and directory brute-force attempts.
- **Access Control Policies:** Enforce strict access controls to secure sensitive endpoints.
- **Vulnerability Remediation:** Audit the web application code to fix underlying flaws allowing endpoint discovery.

</details>

[Λ Voltar ao topo](#tryhackme---writeups--security-notes)

---

### Offensive Security Intro (EN)

![Tags](https://img.shields.io/badge/Topics-Pentesting%20%7C%20Directory%20Bruteforce%20%7C%20Broken%20Access%20Control-4169E1)

<details>
<summary><b>View Full Investigation & Concepts</b></summary>

#### 1. Scenario
The goal was to adopt an attacker's mindset to uncover security flaws within the *FakeBank* web application, highlighting the risks of relying on security through obscurity and broken access controls.

#### 2. Concepts Learned
- **Offensive Security (Pentesting):** Thinking like an adversary to discover and exploit vulnerabilities before real threat actors do.
- **Web Directory Brute-Forcing:** Utilizing tools like `Dirbuster` / `Dirb` with wordlists to map hidden files and endpoints on web servers.
- **Security through Obscurity:** Understanding why hiding URLs without server-side authentication fails to protect web applications.

#### 3. Step-by-Step Investigation
1. **Endpoint Mapping:** Executed `dirb` via the Linux terminal targeting the bank's URL to discover unlinked pathways.
2. **Discovery Analysis:** Reviewed the discovered hidden pages returned by the scan.
3. **Exploitation:** Navigated to the hidden URL, entered account details, and performed money deposits without any authentication checks.

#### 4. Recommended Actions
- **Implement Robust Access Control:** Restrict access to sensitive endpoints (e.g., `/bank-transfer`) by enforcing server-side authentication.
- **Avoid Security through Obscurity:** Do not rely on hidden paths; enforce strict session verification.
- **Enforce Transaction Authorization:** Ensure all deposit and transfer operations check user session validity and account ownership.
- **Disable Directory Listing:** Configure web servers to prevent directory browsing and remove exposed administrative/test pages.

</details>

[Λ Voltar ao topo](#tryhackme---writeups--security-notes)

---

### Search Skills: Vulnerability Databases (EN)

![Tags](https://img.shields.io/badge/Topics-Vulnerability%20Management%20%7C%20CVE%20%7C%20SQL%20Injection-4169E1)

<details>
<summary><b>View Full Investigation & Concepts</b></summary>

#### 1. Scenario
Leverage public vulnerability databases to analyze CVE identifiers, severity scoring metrics, and affected software products.

#### 2. Concepts Learned
- **Common Vulnerabilities and Exposures (CVE):** Industry-standard identification system for public security flaws (`CVE-YEAR-NUMBER`).
- **CVSS Scoring:** Evaluating vulnerability impact, complexity, and exploitability to prioritize patch management.
- **SQL Injection (SQLi):** Understanding code injection risks and standard mitigation practices.

#### 3. Step-by-Step Investigation
1. **Database Query:** Searched for the specified CVE code within public vulnerability databases.
2. **Impact Assessment:** Analyzed score metrics, exploitability factors, affected components, and vendor remediations.

#### 4. Recommended Actions
- **Software Updates:** Upgrade *Apache WebPortal* to the latest patched version.
- **Parameterized Queries:** Enforce prepared statements in application code to permanently mitigate SQL Injection vulnerabilities.

</details>

[Λ Voltar ao topo](#tryhackme---writeups--security-notes)

---

### Search Skills: Find Server Details (EN)

![Tags](https://img.shields.io/badge/Topics-OSINT%20%7C%20Shodan%20%7C%20Reconnaissance%20%7C%20Banner%20Grabbing-4169E1)

<details>
<summary><b>View Full Investigation & Concepts</b></summary>

#### 1. Scenario
Inspect and correlate the public IP address and domain information of an internet-facing Apache web server using scanning tools and search engines.

#### 2. Concepts Learned
- **OSINT with Shodan:** Querying search engines indexing internet-connected devices to gather intelligence passively.
- **Web Server Footprinting:** Risks tied to exposing detailed software versions of web servers like Apache to the public internet.

#### 3. Step-by-Step Investigation
1. **Scanning & Mapping:** Searched for Apache instances via TryScanMe and selected the primary record to resolve the host IP.
2. **Domain Discovery:** Identified the corresponding exposed domain (`trychackme.thm`).

#### 4. Recommended Actions
- **Banner Grabbing Protection:** Obfuscate Apache server banners to hide exact version numbers and OS details.
- **Custom Error Pages:** Suppress detailed server disclosures from default HTTP error pages (e.g., 404, 500).

</details>

[Λ Voltar ao topo](#tryhackme---writeups--security-notes)

---

### Search Skills: Malware Analysis (EN)

![Tags](https://img.shields.io/badge/Topics-Threat%20Intelligence%20%7C%20VirusTotal%20%7C%20Malware%20Analysis-4169E1)

<details>
<summary><b>View Full Investigation & Concepts</b></summary>

#### 1. Scenario
Analyze a suspicious executable file using multi-engine threat detection platforms to determine its risk rating and malicious potential.

#### 2. Concepts Learned
- **Multi-Engine Scans with VirusTotal:** Aggregating detection data across dozens of AV vendors to evaluate file and URL reputation.
- **Indicators of Compromise (IoCs):** Utilizing file reputation metrics to extract actionable threat intelligence.

#### 3. Step-by-Step Investigation
1. **Artifact Query:** Searched for `invoice_payment.exe` on the TryDetectMe scanner interface.
2. **Vendor Assessment:** Inspected security engine verdicts and vendor classification lists.
3. **Risk Evaluation:** Confirmed high-risk status after 52 out of 72 engines flagged the sample as malicious.

#### 4. Recommended Actions
- **Hash Blacklisting:** Add the file hash of `invoice_payment.exe` to organizational EDR and Antivírus blocklists.
- **User Awareness Training:** Educate employees on identifying and reporting phishing emails containing suspicious invoice attachments.

</details>

[Λ Voltar ao topo](#tryhackme---writeups--security-notes)
