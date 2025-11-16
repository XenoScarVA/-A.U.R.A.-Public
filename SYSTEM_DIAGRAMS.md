# System Diagrams
This document contains the ASCII architecture diagrams for A.U.R.A. — Artificial Understanding & Response Architecture project. Each subsystem is shown separately, followed by a full system
overview.

============================================================
## Thalamus Module

The Thalamus acts as the sensory router of the system. It receives incoming
signals, performs safety and cleaning steps, and distributes information to the
Hippocampus and Amygdala.

============================================================

                            ┌──────────────────────────────┐
                            │         INPUT STREAM         │
                            │   text events signals etc    │
                            └───────────────┬──────────────┘
                                            │
                                            ▼
                               ┌────────────────────────┐
                               │        THALAMUS        │
                               │   Sensory Router Hub   │
                               └────────────────────────┘
                                           │
                ┌──────────────────────────┼────────────────────────────┐
                ▼                          ▼                            ▼
        ┌────────────────┐      ┌──────────────────────┐     ┌────────────────────┐
        │  Safety Filter │      │ Context Preprocessor │     │ Salience Detector  │
        │ Initial Gate   │      │ Normalize and Clean  │     │ Relevance and Focus|
        └────────────────┘      └──────────────────────┘     └────────────────────┘
                │                          │                          │
                └──────────────┬───────────┴───────────────┬──────────┘
                               │                           │
                               ▼                           ▼
                     ┌───────────────────┐      ┌───────────────────────┐
                     │    HIPPOCAMPUS    │      │        AMYGDALA       │
                     │ Memory and Context│      │  Emotion and Response │
                     └───────────────────┘      └───────────────────────┘


============================================================
## Hippocampus Module

The Hippocampus manages memory, similarity scoring, emotional tagging, and
contextual storage.

============================================================

            ┌─────────────────────────────┐
            │       THALAMUS INPUT        │
            └───────────────┬─────────────┘
                            │
                            ▼
                ┌────────────────────────┐
                │      HIPPOCAMPUS       │
                │   Memory Context Hub   │
                └────────────────────────┘
                            │
                            ▼
             ┌──────────────────────────────┐
             │  Semantic Similarity Engine  │
             │ (word vectors associations)  │
             └──────────────────────────────┘
                            │
                            ▼
             ┌──────────────────────────────┐
             │   Fact Storage and Sources   │
             │  (tracking and attribution)  │
             └──────────────────────────────┘
                            │
                            ▼
             ┌──────────────────────────────┐
             │   Emotional Memory Binding   │
             │ (arousal and relevance tags) │
             └──────────────────────────────┘
                            │
                            ▼
                ┌────────────────────────┐
                │ SHARED CONTEXT EXPORT  │
                │   (LLM Integration)    │
                └────────────────────────┘


============================================================
## Amygdala Module

The Amygdala detects threats, amplifies emotional responses, and manages high
priority reactions.

============================================================

                       ┌──────────────────────────┐
                       │      THALAMUS INPUT      │
                       └────────────┬─────────────┘
                                    │
                                    ▼
                           ┌─────────────────┐
                           │    AMYGDALA     │
                           │  Emotion Engine │
                           └─────────────────┘
                                    │
              ┌─────────────────────┼───────────────────────────┐
              ▼                     ▼                           ▼
     ┌────────────────┐     ┌─────────────────┐     ┌────────────────────────┐
     │ Threat Scoring │     │ Emotional React │     │ Arousal Adjustment     │
     │ Risk Level     │     │ Fear and Anger  │     │ Spikes and Regulation  │
     └────────────────┘     └─────────────────┘     └────────────────────────┘
             │                      │                           │
             └───────────┬──────────┴────────────────┬──────────┘
                         │                           │
                         ▼                           ▼
               ┌───────────────────┐   ┌───────────────────────────┐
               │ Safety Escalation │   │  Emotional Output Signal  │
               │ Lockdown Control  │   │  Modulation for Behavior  │
               └───────────────────┘   └───────────────────────────┘


============================================================
## Synapsial Bridge Network

The Synapsial Bridge Network links the Entity Extraction System with the Memory Storage, allowing them to exchange information. It
provides a unified communication pathway so new entities can be stored and known entities can be recognized consistently

============================================================


                        ┌──────────────────────────────┐
                        │      ENTITY EXTRACTION       │
                        │  identifies words and items  │
                        └──────────────┬───────────────┘
                                       │
                                       ▼
                        ┌──────────────────────────────┐
                        │     SYNAPSIAL BRIDGE HUB     │
                        │  central routing layer       │
                        │  handles cross-system links  │
                        └──────────────┬───────────────┘
                          ┌────────────┴───────────────┐
                          │                            │
                          ▼                            ▼
        ┌──────────────────────────────┐   ┌─────────────────────────────┐
        │  Memory Storage and Binding  │   │  Memory Retrieval / Lookup   │
        │  stores new entities         │   │  fetches known associations  │
        └──────────────────────────────┘   └─────────────────────────────┘
                         │                             │
                         └──────────────┬──────────────┘
                                        │
                                        ▼
                          ┌──────────────────────────┐
                          │  ENTITY IDENTIFICATION   │
                          │  assigns identity, tags  │
                          └──────────────────────────┘


============================================================
## Full System Architecture

This diagram shows how all modules interact in the complete Artificial Limbic
System. 15\11\2025 : Updated with Synaptial Bridge Network.

============================================================

                                  ┌────────────────────────────┐
                                  │        INPUT STREAM        │
                                  │ text, events, signals etc  │
                                  └──────────────┬─────────────┘
                                                 │
                                                 ▼
                                   ┌──────────────────────────┐
                                   │         THALAMUS         │
                                   │ sensory router & gateway │
                                   └──────────────┬───────────┘
                                         ┌─────────────────┐
                                         │                 │
                                         ▼                 ▼
                               ┌────────────────┐   ┌────────────────┐
                               │ Safety Filter  │   │ Preprocessing  │
                               └────────┬───────┘   └───────┬────────┘
                                        ┌───────────────────┐
                                        │                   │
                                        ▼                   ▼
                                    ┌────────────────────────────┐
                                    │     ENTITY EXTRACTION      │
                                    │    detect items, names     │
                                    └──────────────┬─────────────┘
                                                   │
                                                   ▼
                                 ┌────────────────────────────────────┐
                                 │      SYNAPSIAL BRIDGE NETWORK      │
                                 │ links extraction ↔ memory system   │
                                 └──────────────────┬─────────────────┘
                                     ┌──────────────┼──────────────┐
                                     │                             │
                                     ▼                             ▼
                      ┌────────────────────────┐      ┌─────────────────────────┐
                      │  MEMORY STORAGE/BINDING│      │  MEMORY RETRIEVAL GATE  │
                      │   create & update data │      │ fetch known associations│
                      └─────────────┬──────────┘      └────────────┬────────────┘
                                    │                              │
                                    └────────────────┬─────────────┘
                                                     │
                                                     ▼
                                   ┌─────────────────────────────────┐
                                   │     ENTITY IDENTIFICATION       │
                                   │ final identity scoring & tags   │
                                   └─────────────────┬───────────────┘
                                                     │
                                                     ▼
                          ┌────────────────────────────────────────────────────┐
                          │               HIPPOCAMPUS MODULE                   │
                          │  memory, context, similarity, source attribution   │
                          └──────────────────────────┬─────────────────────────┘
                                                     │
                                                     ▼
                                    ┌───────────────────────────────────┐
                                    │             AMYGDALA              │
                                    │ emotional weighting, threat eval  │
                                    └─────────────────┬─────────────────┘
                                                      │
                                                      ▼
                                    ┌──────────────────────────────────┐
                                    │      EMOTIONAL STATE ENGINE      │
                                    │ arousal, tension, concern, etc   │
                                    └──────────────────┬───────────────┘
                                                       │
                                                       ▼
                                         ┌───────────────────────────┐
                                         │ REGULATION + DECAY CYCLES │
                                         │   background processes    │
                                         └───────────────────────────┘

