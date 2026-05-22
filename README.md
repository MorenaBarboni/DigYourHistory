# Repetition Package for "Upgrade-Aware Capture-Replay Testing for Proxy-based Smart Contracts"
This repository contains the data supporting the paper "Upgrade-Aware Capture-Replay Testing for Proxy-based Smart Contracts" (BCRA 2026).
The package includes the artifacts produced during the experiments, and is intended to support result inspection, replication, and further analysis.

# Repository Structure
At the top level, the repository contains two folders, `BSTPStaking` and `Paladin` one for each subject project used in the study.
Each project is organized as follows:

```
<project>/
├── contracts/
├── llm/
│   ├── prompt/
│   ├── response/
│   └── candidates/
├── sumo/
│   ├── results/mutants/
│   └── results/mutations.json/
└──transactions/
   └── transactions.json
```

## /contracts
Contains the original, unmutated smart contracts (proxy and logic contracts) used as the baseline subjects in the experiment.

## /llm
Contains all data related to LLM-based transaction selection.

* `candidates/`: Candidate transaction sets used for each mutant. Each file defines the pool of transactions from which the LLM was asked to select replay tests.

* `prompt/`: All requests sent to the LLM. Each prompt includes the full context (upgrade information, transaction data, and instructions) corresponding to a specific ablation configuration.

* `response/`: Raw LLM outputs for each prompt, including multiple repetitions per ablation configuration.

## /sumo
Contains details about the mutants generated using the SuMo mutation testing framework, including mutation metadata used to simulate upgrade-induced behavioral deviations.

* `results/mutants/`: Contains the mutated Solidity source files, one per mutant. Each file represents a variant of the original logic contract with a single injected mutation.
* `results/mutations.json`: Provides metadata for the mutants, including mutation operators, mutation locations, and injected replacement.

## /transactions

The `transactions.json` contains the complete historical transaction trace of the target contract, from which candidate transactions were sampled.
