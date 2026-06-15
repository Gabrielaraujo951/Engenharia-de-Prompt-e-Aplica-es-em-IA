# Projeto Módulo 3 – Low Code/No Code/Vibecode

# 🎉 Sistema Dinâmico de Confirmação de Presença (No-Code/Low-Code)

Este projeto consiste em uma plataforma inteligente para criação de eventos e gerenciamento de confirmação de presença (RSVP). O sistema utiliza uma arquitetura dinâmica onde o organizador gera um convite personalizado e o convidado realiza a validação de seus dados antes de confirmar ou recusar a participação.

## 🚀 Link do Protótipo
O protótipo funcional e hospedado pode ser acessado através do link abaixo:
🔗 **[Acessar Site Protótipo] [https://bubbleapps.io](https://gs668951.bubbleapps.io/version-test?debug_mode=true)**

---

## 🎯 Objetivo do Projeto
O sistema tem a intenção de facilitar e automatizar o processo de confirmação de um usuário a um evento. Ele elimina a necessidade de preenchimentos manuais exaustivos e centraliza todas as respostas em um banco de dados unificado, otimizando o planejamento de organizadores de festas, conferências e reuniões.

---

## ⚙️ Funcionalidades do Protótipo
O protótipo desenvolvido permite uma experiência de ponta a ponta sem a necessidade de programação tradicional:

* **Criação de Eventos Customizados:** O organizador define título, recado exclusivo e imagem de fundo.
* **Links Únicos Automatizados:** Geração de uma URL exclusiva para cada evento baseada no *Unique ID* do banco de dados.
* **Identificação Obrigatória:** Captura prévia de Nome e E-mail do convidado antes da exibição dos detalhes.
* **Interface Responsiva e Dinâmica:** A página do convidado se adapta instantaneamente carregando a mídia e textos escolhidos pelo criador.
* **Fluxo de Resposta Inteligente:** Telas condicionais de agradecimento para quem confirma ou recusa o convite.
* **Disparo de E-mails Automático:** Envio automatizado de um e-mail de confirmação diretamente para a caixa de entrada do usuário.
* **Armazenamento em Nuvem:** Salvamento instantâneo de todas as respostas e dados cadastrados.

---

## 🛠️ Plataformas Utilizadas e Justificativa

O ecossistema do projeto foi estruturado utilizando o conceito de programação avançada por meio de ferramentas visuais e IA:

* **Gemini (Google):** Utilizado como o motor de inteligência artificial para engenharia, refinamento e otimização dos prompts estruturados.
* **Bubble.io:** Plataforma No-Code robusta utilizada para o desenvolvimento visual, hospedagem e gerenciamento do banco de dados do site.

### Justificativa da Escolha
A combinação destas tecnologias foi escolhida estrategicamente por oferecer:
* **Otimização de Prompts:** Uso da IA para dar o melhor seguimento e lógica estrutural ao site antes da montagem.
* **Interface Visual Intuitiva:** Agilidade no desenho de telas complexas usando o motor Flexbox responsivo do Bubble.
* **Facilidade de Integração:** Arquitetura nativa preparada para conexão futura com APIs e serviços externos.
* **Automação Rápida:** Configuração ágil de processos e fluxos lógicos (*workflows*) sem digitação manual de código.

---

## 🏗️ Estrutura de Páginas do Sistema

O funcionamento ocorre através de fluxos visuais configurados no Bubble, reduzindo o código manual e agilizando testes. O fluxo de navegação segue a seguinte ordem:


## ⚠️ Limitações Encontradas

Durante o processo de desenvolvimento e validação do protótipo, o grupo identificou as seguintes barreiras técnicas:

1. **Customização Limitada:** Algumas regras visuais e comportamentos de transição específicos dependiam estritamente dos recursos e plugins nativos da plataforma.
2. **Dependência da Ferramenta:** O ecossistema, os dados e a lógica gerada ficaram totalmente vinculados à infraestrutura de servidores do Bubble.
3. **Limitações de Escalabilidade:** Os recursos gratuitos da plataforma possuem restrições severas de uso (capacidade de processamento e acessos), o que impede o sistema de ser 100% funcional em larga escala sem custos.
4. **Integrações Pagas:** Conectores avançados e ferramentas essenciais para deixar o site totalmente funcional exigiam a contratação de planos premium.
5. **Menor Controle Técnico:** Nem todos os processos lógicos de baixo nível podiam ser personalizados ou auditados profundamente.

---

## 🧠 Reflexão Crítica e Soluções Futuras

A experiência de desenvolvimento trouxe grandes aprendizados para o grupo:

* **Velocidade de Entrega:** O grupo percebeu que as plataformas *Low-Code / No-Code* aceleram significativamente a criação de soluções tecnológicas, reduzindo drasticamente o tempo gasto entre a ideia e o produto mínimo viável (MVP) em fases iniciais de prototipagem.
* **Estratégia de Prompts:** Compreendeu-se que o sucesso de uma aplicação sem código depende de instruções claras e bem depuradas por ferramentas de IA.

### Soluções Propostas para Superar as Limitações
* **Uso de APIs Externas:** Conectar o ecossistema a serviços independentes e gratuitos (como o Google Sheets para banco de dados ou EmailJS para envios) para contornar as travas do plano gratuito da plataforma principal.
* **Abordagem Multiplataforma:** Utilizar mais de um prompt estruturado e diferentes plataformas integradas para gerar o ecossistema final, dividindo as responsabilidades do sistema em ferramentas especialistas.

