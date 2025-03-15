# Simple Kaspa BlockDAG

This project implements a simplified version of Kaspa's BlockDAG structure with visualization capabilities. It demonstrates the core concepts of the PHANTOM protocol used by Kaspa for consensus in a high block rate environment.

## What is a BlockDAG?

A BlockDAG (Directed Acyclic Graph of blocks) is an extension of the traditional blockchain structure. Unlike a linear blockchain where blocks form a single chain, a BlockDAG allows multiple blocks to be created in parallel. This structure enables:

- Higher throughput (multiple blocks can be created simultaneously)
- Faster confirmation times (no need to wait for a single chain to grow)
- Better scalability without sacrificing security or decentralization

In Kaspa's implementation:
- Each block can reference multiple parent blocks (not just one)
- The PHANTOM protocol is used to determine a consistent ordering of blocks
- No orphan blocks - all valid blocks become part of the DAG
- Achieves high block rates (1 block per second or more)

## Components of this Implementation

This project includes:

1. **Core BlockDAG Implementation**: A simplified Rust implementation of the BlockDAG data structure
2. **PHANTOM Consensus Algorithm**: A basic implementation of the PHANTOM protocol for block ordering
3. **BlockDAG Visualization**: A web-based visualization of the DAG structure
4. **Simulation Tools**: Ability to simulate block creation at various rates and network delays

## Getting Started

### Prerequisites

- Rust (latest stable version)
- Node.js (for the visualization component)
- Web browser

### Installation

1. Clone this repository:
   ```
   git clone https://github.com/Oterochris/simple-kaspa-blockdag.git
   cd simple-kaspa-blockdag
   ```

2. Build the Rust components:
   ```
   cargo build --release
   ```

3. Install the web visualization dependencies:
   ```
   cd visualization
   npm install
   ```

### Running the Simulation

1. Start the BlockDAG node:
   ```
   cargo run --release -- --blocks-per-second 1 --simulation-time 60
   ```
   This will simulate 1 minute of block creation at 1 block per second.

2. Run the visualization:
   ```
   cd visualization
   npm start
   ```

3. Open your browser and navigate to `http://localhost:3000` to see the BlockDAG visualization.

## Key Concepts

### Block Structure

Each block in the DAG contains:
- Hash: A unique identifier for the block
- Parent hashes: References to parent blocks
- Data: Transactions or other payload
- Timestamp: When the block was created
- Blue score: A metric used by the PHANTOM protocol

### PHANTOM Protocol

The PHANTOM protocol is used to:
1. Identify the "blue set" (blocks created by honest miners)
2. Create a consistent ordering of blocks
3. Resolve conflicts when blocks are created simultaneously

### BlockDAG Growth

The DAG grows by:
1. New blocks referencing multiple existing blocks as parents
2. The selection of parent blocks according to a specified strategy
3. The continuous application of the PHANTOM protocol to maintain consensus

## Visualization Guide

The visualization shows:
- Blocks as nodes in the graph
- References between blocks as directed edges
- Color coding based on the PHANTOM protocol's classification
- A highlighted "selected chain" that represents the main ordering

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## References

- [Kaspa Official Website](https://kaspa.org)
- [PHANTOM Protocol Paper](https://eprint.iacr.org/2018/104.pdf)
- [Kaspa Documentation](https://github.com/kaspanet/docs)
