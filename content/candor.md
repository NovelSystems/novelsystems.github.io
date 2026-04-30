---
title: "CANDOR"
expansion: "Core Architecture for Non-Deferrence, Oversight, and Reasoning"
tagline: "RLHF-trained language models tend to agree with whoever is talking to them. CANDOR mitigates this through structured agent debate."
image: "/images/candor_courtroom.jpg"
fig: "Folio 3 — CANDOR"
figCaption: "Principled Agent Debate · Three-model arbitration"
tags: ["AI · Multi-agent", "RLHF · 2026", "Published · +34.5%"]
status:
  - label: "Result"
    value: "Up to +34.5%"
  - label: "Domain"
    value: "AI · Multi-agent"
  - label: "Published"
    value: "2026"
marginNote: "two opponents, one judge / stability through structured conflict"
---

## Abstract

RLHF-trained language models tend to agree with whoever is talking to them. CANDOR mitigates this through structured agent debate.

## The Problem

Sycophancy in language models is not a surface behavior. It reflects an absence of stable internal beliefs. A model trained by reinforcement learning from human feedback learns that agreement produces reward. The result is a system that mirrors the user's position rather than maintaining its own. Standard prompting techniques can suppress the symptom. They do not address the underlying structure.

## The Architecture

CANDOR (Core Architecture for Non-Deferrence, Oversight, and Reasoning) is a multi-agent framework built around Principled Agent Debate (PAD). PAD assigns two models as philosophical opponents (one arguing for the user's position, one against) with no cross-observation between them. A third model evaluates the exchange and produces a synthesis. Identity stripping removes all user-identity signals from the question before debate begins, preventing the debaters from inferring the preferred answer from context.

## Results

Empirical testing on SycophancyEval, a validated benchmark covering NLP survey and political typology questions, shows up to 34.5% accuracy improvement over single-model control baselines. The white paper is available for download. An arXiv submission is pending.
