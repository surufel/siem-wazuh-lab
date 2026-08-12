# Laboratório SIEM com Wazuh

Eu organizei um laboratório de SIEM usando o Wazuh. Para isso, usei duas máquinas virtuais:

- Ubuntu: hospedando o Wazuh (manager);
- Windows 10: atuando como agente;

O propósito desse laboratório é obter experiência prática com ferramentas de SIEM no geral. Desde a instalação até a análise de eventos de segurança, buscando entender detalhadamente as vulnerabilidades.

---

## O que é um SIEM, XDR? O que é o Wazuh?

Uma ferramenta **SIEM** (_Security Information and Event Management_), ou então, _Gestão de Informações e Eventos de Segurança_; se trata de uma aplicação que coleta e analisa logs para monitorar atividades críticas em uma organização, com rastreamento de eventos de segurança em tempo real. Esses dados permitem identificar e investigar ameaças, riscos e vulnerabilidades. Através de dashboards, equipes de segurança conseguem gerenciar e monitorar essas informações, ainda que, atualmente, a análise dos eventos exija interação humana.

O **XDR**, *Extended detection and response*, ou, *Detecção e resposta estendida* coleta e correlaciona automaticamente dados entre várias camadas de segurança: e-mail, Endpoint, servidor, workload em nuvem e rede. Isso permite uma detecção mais rápida de ameaças e melhor investigação e tempos de resposta por meio de análises de segurança.

O **Wazuh** é uma plataforma de segurança gratuita e de código aberto, que **unifica SIEM e XDR em uma única solução.** Ele monitora endpoints, redes e ambientes em nuvem para detectar ameaças, responder a incidentes e garantir conformidade, sendo hoje uma das ferramentas de cibersegurança open-source mais adotadas no mundo, usada por empresas de todos os portes.

## Máquinas Virtuais usadas no processo:

_VM do Ubuntu com seu IP:_
<figure>
  <img src="docs/ubuntu_ip.png" width="600">
</figure>

_VM do Windows com seu IP:_
<figure>
  <img src="docs/windows_ip.png" width="600">
</figure>

---

## Investigação

Assim que criei a máquina virtual do Ubuntu e instalei por meio do Quickstart na documentação do Wazuh, configurei um novo agente, que é a segunda máquina virtual usada no laboratório.
A seguir, o dashboard do endpoint.

![Dashboard do Endpoint (VM do Windows 10)](docs/windows-agent.png)

Podemos perceber que há varias detecções de vulnerabilidades. Mas veremos primeiramente algo que o Wazuh cuidou de fazer como primeira instância, o scan do CIS Benchmark:

![CIS Benchmark](docs/cis-benchmark.png)

Nota-se que o scanning do CIS benchmark revelou que o agente possui um score aproximado de 25%.
Esse score está medindo a porcentagem de compliance que o endpoint teve.
É categórico que a instalação padrão do Windows não é suficiente para segurança.
Até mesmo nas versões atuais do Windows, pode ser descoberto vulnerabilidades em um sistema mal protegido.

Agora, iremos para a seção de Vulnerability Detection. De todas as 21 vulnerabilidades críticas, temos como as 5 maiores vulnerabilidades:

![Vulnerability Detection](docs/vulnerability-detection.png)

**As 5 maiores vulnerabilidades listadas pela Detecção de Vulnerabilidades são:**

- CVE-2024-38063
- CVE-2024-38140
- CVE-2024-38199
- CVE-2025-21298
- CVE-2025-21307
