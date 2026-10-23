## Inspiration

Over $142,000,000 was stolen from Web3 wallets and DAOs in 2025 alone due to blind signature phishing.

Scam websites disguise malicious token approvals and proxy implementation hijacks behind innocent buttons like "Claim Airdrop". Standard wallets only display unreadable hexadecimal calldata like `0x095ea7b3...`. Users have no way to verify what they are actually approving until their balances hit zero in the next block.

We built Vernier to give crypto users an emergency brake: an instantaneous pre-execution firewall that simulates raw transaction bytecode and tells you in plain English what actually leaves your wallet before you press Confirm.

## What It Does

Vernier is an EVM transaction intent firewall that inspects transaction bytecode before your wallet signs:

- **0.42ms Client-Side Simulation**: Executes raw transaction calldata inside an in-browser Viem sandbox with zero RPC latency and zero mempool leakage.
- **Intent vs Reality Comparator**: Compares declared human intent against actual mutated storage slots (`SSTORE`) and flags unauthorized balance drains.
- **5-Second Traffic Light Verdict**: Delivers an unmistakable visual signal: Green (Safe to Sign) vs Red (Critical Threat Blocked).
- **Plain English Explainer**: Explains threats in natural language (*"Warning: This contract will grant unlimited USDC approval to attacker wallet 0x4e6b...2ab9"*).
- **Dual-Mode Working Cockpit**:
  - *Judge Mode (Default)*: High-contrast 3-card breakdown and before/after wallet simulator.
  - *Auditor Mode*: Deep EVM metrology with Vernier Caliper step scrubber, opcode disassembly stepper, and storage slot differential log.
- **Cryptographic Attestation**: Emits a signed EIP-712 receipt with SHA-256 state root digest and 1-click JSON export for audit trails.

## How We Built It

- **Frontend Architecture**: Next.js 15.2.1 static HTML export deployed globally on Netlify Edge CDN (zero persistent backend daemons, 100% free hosting).
- **Execution Engine**: Client-side Viem simulation engine running sub-millisecond EVM state transition traces.
- **Web3 Wallet Flow**: RainbowKit v2 and Wagmi integration supporting Rabby, MetaMask, Coinbase, and WalletConnect with reactive in-place account binding.
- **Design System**: 3-Surface Architecture adhering to the 7-Gate Visual Gauntlet Loop (Obsidian slate `#090d16`, calibrated amber accents `#f59e0b`, tabular numeric displays).
- **Verification & Testing**: Playwright automated visual regression testing across desktop (1440px) and mobile (390px) viewports.

## Challenges We Ran Into

- **Eliminating RPC Latency**: Traditional simulation services take 800ms to 2000ms by routing calldata to external nodes, introducing lag that causes users to disable security plugins. We eliminated this bottleneck by compiling lightweight execution rules directly into a browser-native sandbox, achieving 0.42ms execution.
- **Balancing Depth with Beginner Usability**: Early versions presented an overwhelming wall of opcodes, gas profiles, and memory slots that intimidated non-technical users. We resolved this by engineering the Dual-Mode Cockpit: defaulting to a 5-second plain English verdict while keeping deep metrology accessible via the Auditor Mode toggle.

## Accomplishments That We're Proud Of

- **0.42ms Pre-Flight Verification**: Instantaneous client-side execution with zero external RPC dependency.
- **The 7-Gate Visual Gauntlet**: Full 1-chrome header, 5-beat hero, 3-card economic friction grid, dedicated cryptographic proof rail, and real wallet extension flow.
- **Zero Daemon Hosting**: 100% free static deployment on Netlify Global Edge without ongoing server costs.

## What We Learned

The greatest vulnerability in Web3 is not smart contract exploits: it is human cognitive overload from unreadable wallet prompts. Translating bytecode deltas into plain English before signature is the most effective consumer defense layer.

## What's Next For Vernier

- **Browser Extension Packaging**: Interception wrapper for Chrome, Brave, and Firefox to protect MetaMask and Rabby automatically.
- **ERC-4337 Account Abstraction**: Pre-flight validation hooks for smart contract wallets and multi-sig treasuries (Safe).
- **Community Threat Oracle**: Decentralized registry of flagged pathogenic storage slot mutation patterns.

## Verified Links & Contracts

- **Live Production dApp**: https://tryvernier.netlify.app
- **Demo Video (164.7s Master Cut)**: https://tryvernier.netlify.app/vernier-demo-showcase.mp4
- **GitHub Repository**: https://github.com/A-Raphie/vernier
- **Interactive Cockpit**: https://tryvernier.netlify.app/#cockpit
- **Cryptographic Proof Rail**: https://tryvernier.netlify.app/#proof
- **Interactive Pitch Deck**: https://tryvernier.netlify.app/#deck
- **Permit2 Canonical Contract**: https://sepolia.etherscan.io/address/0x000000000022D473030F116dDEE9F6B43aC78BA3
