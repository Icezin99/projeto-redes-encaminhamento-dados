# Projeto de Encaminhamento de Dados

Projeto prático desenvolvido no âmbito da cadeira de Encaminhamento de Dados da Licenciatura em Engenharia Informática (Ramo de Redes e Administração de Sistemas) do ISEC.

## Visão Geral da Rede
O projeto consistiu em desenhar e configurar a infraestrutura de rede para um resort de grande dimensões. A arquitetura seguiu o modelo **Hub-and-Spoke**, tendo o Edifício Administrativo Central (EAC) como o núcleo (*core*) responsável por agrupar o tráfego, resumir rotas e aplicar as políticas principais.

![Topologia da Rede](topology/topologia-ED.png)

A rede foi dividida em três setores principais:
* **Setor Oeste:** Área Desportiva e Lazer (ADL) a correr OSPF e Serviços Operacionais (SO) com EIGRP.
* **Setor Este:** Edifício Administrativo Central (EAC) com OSPF, Bungalows & Villas (BV) com EIGRP e a Restauração com RIPv2.
* **Setor Norte:** Centro de Conferências (CC) com OSPFv3, Hotel Principal (HP) com OSPF e o Spa & Wellness Center (SWC) com RIPv2.

## O que foi implementado
* **Encaminhamento Dinâmico:** Configuração de vários protocolos em simultâneo (OSPF, OSPFv3, EIGRP e RIPv2) consoante a zona da rede.
* **Saída para a Internet:** Implementação de NAT para tradução de endereços, com um link principal de 1 Gbps no EAC e um link de *backup* (100 Mbps) nos Serviços Operacionais.
* **Políticas de Tráfego (PBR):** Criação de *Policy-Based Routes* e *Access Lists* no Spa & Wellness Center para forçar caminhos específicos para o tráfego.
* **Filtros:** Uso de *Prefix-lists* nos Serviços Operacionais para controlar e limitar as rotas que eram anunciadas.
* **Acesso Remoto:** Configuração de Telnet nos routers com restrição de sessão única e mensagens de boas-vindas personalizadas por dispositivo.

## ⚠️ Notas e Pontos de Melhoria
* **Conectividade Exterior:** A configuração do caminho de *backup* da saída para a internet nos Serviços Operacionais apresentou limitações no encaminhamento do tráfego de retorno, sendo um ponto identificado para otimização em futuras validações de resiliência.

## Conteúdo do Repositório
* `topology/` - Imagem com a topologia lógica da rede e respetivos ficheiros de simulação.
* `excel/` - Tabela de endereçamento IP detalhada (com o planeamento completo de sub-redes).
