# 3-Tier Enterprise Architecture Design (Day 8)

## 1. Objective
Design and understand a scalable enterprise network using the 3-tier architecture model consisting of Core, Distribution, and Access layers.

---

## 2. Architecture Overview

### Core Layer
- High-speed backbone of the network
- Provides fast and reliable transport between distribution layers
- Minimal configuration, maximum stability

### Distribution Layer
- Aggregates access layer switches
- Handles routing, policy enforcement, and segmentation

### Access Layer
- Connects end devices (PCs, printers, etc.)
- Provides edge connectivity to users

---

## 3. Topology Design Plan

- 2 Core Routers (Core1, Core2)
- 2 Distribution Multilayer Switches (Dist1, Dist2)
- 4 Access Switches (Access1–Access4)
- 8 PCs (2 per access switch)

---

## 4. Design Principle

- Redundancy at core and distribution layers
- Hierarchical traffic flow
- Scalability and fault isolation

---

## 5. Learning Outcome

Understand why enterprise networks avoid flat designs and instead use hierarchical architecture for performance, scalability, and resilience.