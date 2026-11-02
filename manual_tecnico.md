# Manual Técnico — PetAlerta

## 1. Visão Geral e Escopo Herdado
O PetAlerta é uma plataforma para localização de cães perdidos, conectando tutores, cidadãos e protetores.

### Integrantes
Gabriel, Guilherme, Brendo e Luany

### Requisitos Funcionais e Não Funcionais
- RF01 — Cadastro de animais perdidos
- RF02 — Consulta de alertas
- RF03 — Pesquisa e filtragem
- RF04 — Visualização de detalhes
- RF05 — Registro de avistamentos
- RNF01 — Disponibilidade 24h
- RNF02 — Responsividade (Mobile-First)
- RNF03 — Integridade dos dados e segurança

## 2. Arquitetura Lógica e Padrões
- Front-End: Vite + React + Tailwind CSS
- Back-End: Node.js / Express / Supabase
- Banco de Dados: PostgreSQL + Google Maps
- Padrão: MVC em Monolito Modular
- Camadas: Apresentação, Aplicação, Domínio e Infraestrutura

## 3. Setup de Execução Local
1. `git clone <url-do-repositorio>`
2. `npm install`
3. `npm run dev`

## 4. Governança de Versionamento no Git
- Branch `main` preservada (sem commits diretos).
- Feature Branches (`feature/nome-da-funcionalidade`).
- Commits no imperativo.
- Pull Requests obrigatórios com revisão por pares.

## 5. Manutenção e Métricas de Qualidade
- Rastreabilidade nomenclatural entre Figma, Requisitos e Código.
- Tipos de Manutenção: Corretiva, Adaptativa, Preventiva e Perfectiva.
