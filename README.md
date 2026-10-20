<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset=".github/assets/hero-dark.png">
    <img src=".github/assets/hero.png" alt="queue.me.at landing page" width="880">
  </picture>
</p>

<h1 align="center">queue.me.at</h1>

<p align="center"><strong>A BullMQ console that remembers.</strong></p>

<p align="center">
  <img src="https://img.shields.io/badge/status-in%20development-171717?style=flat-square" alt="Status: in development">
  <img src="https://img.shields.io/badge/license-source--available-404040?style=flat-square" alt="License: source-available">
  <img src="https://img.shields.io/badge/part%20of-me.at-737373?style=flat-square" alt="Part of me.at">
</p>

<p align="center">
  <a href="#features">Features</a> ·
  <a href="#how-it-works">How it works</a> ·
  <a href="#built-with">Built with</a>
</p>

Once Redis removes a settled BullMQ job, the failure you were trying to explain goes with it. I built queue.me.at as a run explorer and operations workspace for BullMQ that keeps that history: find a failed job, see what happened to it, and still have the record after Redis has let it go. It is for teams running BullMQ in production who need retained job history, per-queue trends and safe, audited controls, with read-only access as the default.

<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset=".github/assets/overview-dark.svg">
    <img src=".github/assets/overview.svg" alt="queue.me.at at a glance: history past eviction, find the failed job, read-only by default, durable workflows" width="880">
  </picture>
</p>

## Why queue.me.at

| The usual BullMQ dashboard | queue.me.at |
| --- | --- |
| Shows only what Redis still holds | Keeps settled runs past eviction, within retention windows |
| A snapshot of right now | 24-hour per-queue trends next to the runs |
| Every action one click away | Read-only by default; operations need admin permission and a queue confirmation |
| Filters lost on refresh | Shareable URLs for filters and selected runs |

## Features

- **Retained run history**: settled jobs are kept past Redis eviction, within retention windows and row ceilings.
- **Run explorer**: filter runs by queue, state, id, search text and time, with cursor pagination and shareable URLs for filters and selected runs.
- **Run detail**: timing, attempts, errors and bounded payload excerpts for each run.
- **Queue metrics**: 24-hour per-queue trends next to the runs.
- **Audited operations**: retry, pause and resume, concurrency controls, recurring schedules and workflow triggers, each requiring admin permission and explicit queue confirmation.
- **Durable workflows**: a BullMQ worker runs validated workflow steps with checkpoints stored in the job, so completed steps can be reused on retry.
- **Public sample console**: an isolated demo with made-up data that needs no account, database or Redis connection.
- **Encrypted sources**: source connection URLs are stored as AES-256-GCM ciphertext, and rendered labels omit credentials.

## How it works

<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset=".github/assets/flow-dark.svg">
    <img src=".github/assets/flow.svg" alt="How queue.me.at works: connect, retain, explore, act" width="880">
  </picture>
</p>

You register a source and the queues it declares, with read-only access by default. Settled jobs are retained in Postgres past Redis eviction, as bounded payload excerpts rather than full copies, and history queries filter and page in the database. From a run you can see timing, attempts and errors, and an admin can retry, pause or resume after confirming the queue, with every action audited.

## Built with

<p>
  <img src="https://img.shields.io/badge/Next.js-16-000000?style=flat-square&logo=nextdotjs&logoColor=white" alt="Next.js 16">
  <img src="https://img.shields.io/badge/React-19-171717?style=flat-square&logo=react&logoColor=white" alt="React 19">
  <img src="https://img.shields.io/badge/TypeScript-5-262626?style=flat-square&logo=typescript&logoColor=white" alt="TypeScript">
  <img src="https://img.shields.io/badge/Tailwind%20CSS-4-404040?style=flat-square&logo=tailwindcss&logoColor=white" alt="Tailwind CSS 4">
  <img src="https://img.shields.io/badge/Drizzle-Postgres-525252?style=flat-square&logo=drizzle&logoColor=white" alt="Drizzle ORM and Postgres">
  <img src="https://img.shields.io/badge/BullMQ-ioredis-737373?style=flat-square&logo=redis&logoColor=white" alt="BullMQ and ioredis">
  <img src="https://img.shields.io/badge/Bun-worker%20CLI-737373?style=flat-square&logo=bun&logoColor=white" alt="Bun for the worker CLI">
</p>

- Next.js 16 (App Router) and React 19
- TypeScript
- Tailwind CSS 4
- BullMQ and ioredis
- Drizzle ORM and Postgres (with an explicitly labeled in-memory fallback)
- Better Auth (shared me.at account)
- Bun for the standalone worker CLI

## Part of the me.at family

queue.me.at is one of my [`*.me.at`](https://me.at) apps. They share one design system, account, and app shell. Development happens in a private monorepo; this repository is the project's public-facing home.

## License

Source-available. See [LICENSE](LICENSE).
