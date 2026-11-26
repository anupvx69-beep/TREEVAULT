# TREEVAULT — Binary Tree Archiving & Recovery System

**Tagline:** *Preserve Every Branch. Recover Every Connection.*

TREEVAULT is a full-stack Data Structures & Algorithms application built for **Problem Statement 05: The Museum's Vanishing Family Trees**. It solves lossy binary tree exports by using a **compiled C++17 DSA engine** implementing preorder serialization with explicit `N` null markers, transactional deserialization, archive damage detection, and recursive structural equality checking.

## Key Features

- **Compiled C++17 Core DSA Engine (`cpp-engine/`)**:
  - `std::unique_ptr<TreeNode>` smart-pointer ownership with zero memory leaks.
  - Preorder serialization (`Root -> Left -> Right`) with explicit `N` markers and step-by-step execution trace capture.
  - Transactional recursive deserialization (`Serializer::deserialize`) that rejects malformed archives before mutating state.
  - Genuine recursive structural equality (`BinaryTree::compareStructure`), plus Preorder, Inorder, Postorder, and Level-Order traversals.
  - Enforces the 2,000-node (`4,001`-token) scope limit.
- **Interactive React + SVG Workbench (`src/`)**:
  - Interactive tree builder (Add Root, Left/Right Child, Rename, Delete Subtree, Bracket/Preorder Text Import, Sample Presets).
  - Live SVG binary tree canvas with `L`/`R` branch distinction, toggleable explicit `N` null markers, zoom controls, and Indented Text view.
  - Step-by-step C++ serialization player (Play, Pause, Next, Previous, Reset).
  - Side-by-side Before/After comparison, `.treevault` download/upload, Traversal Analysis, and Integrity Report.
  - Dedicated **Round-Trip Demo** mode that explicitly destroys the original C++ heap tree object before restoring solely from saved text.
  - Dedicated **Damage Lab** testing 7 archive corruption scenarios with detailed diagnostics.

## Project Structure

```text
cpp-engine/          # C++17 DSA Engine (BinaryTree, Serializer, Validator, main.cpp)
backend/             # Express REST API & safe child_process C++ daemon bridge
src/                 # React + TypeScript + Tailwind CSS + SVG frontend
docs/                # Architecture, Archive Format, DSA Explanation, API Docs
```

## Setup & Execution

### 1. Build & Test the C++17 Engine

```bash
make -C cpp-engine
./cpp-engine/treevault_engine --test
```

### 2. Install Dependencies & Run Full-Stack Server

```bash
npm install
npm run dev
```

Open `http://localhost:3000`.

### 3. Run Frontend TypeScript Unit Tests

```bash
npx --yes tsx --test src/utils/treeLayout.test.ts
```
Project Discription:-
The Museum Tree Archiving and Recovery System is a web application that uses Binary Trees to create, visualize, export, and restore historical family-tree structures without losing their original relationships. It also provides tree editing, version management, integrity checking, and traversal analysis to ensure accurate and reliable data recovery.

https://treevault.ai.studio

## Documentation

- [System Architecture](docs/architecture.md)
- [TREEVAULT_V1 Archive Format](docs/archive-format.md)
- [DSA Explanation & Walkthrough](docs/dsa-explanation.md)
- [REST API Reference](docs/api-documentation.md)
