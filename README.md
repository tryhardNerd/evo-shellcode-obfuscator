# evo-shellcode-obfuscator
This project is a genetic algorithm that evolves obfuscated shellcode to get around basic EDR detection. It mixes things like XOR encryption, junk byte insertion, and entropy scoring to create payloads that are harder to spot but still work.

Note: This is strictly for educational purposes, red team simulations, and detection engineering. Do not run this on any system you do not own or have clear permission to test.


# Features

- XOR encodes raw shellcode with randomly selected keys
- Injects junk bytes (`0x90` NOPs) at controlled probabilities
- Validates that decryption reproduces original payload exactly
- Scores variants using Shannon entropy (lower = more stealth)
- Uses a genetic algorithm to select and mutate encoding strategies
- Outputs valid, C# shellcode loaders ready for execution
  
---

## Why This Matters

Even today, static shellcode encoding techniques can slip past real-world EDR. This tool successfully ran undetected on a stock Windows Defender/EDR config, reinforcing how essential behavioral and memory scanning are for modern defense.

---

## How It Works

1. A starting population of shellcode variants is generated from a clean payload.
2. Each is XOR’d with a random key and junk-injected.
3. Fitness is scored using entropy.
4. Top survivors are selected and mutated for the next generation.
5. After 5 generations, the top 3 variants are exported as `.cs` files with decryption + loader logic.

---

## 🔍 Example Usage

Replace the `original_shellcode` list with your own payload, then run all the notebook cells.

The obfuscated shellcode will appear in **Cell #10**.  
To use it, you’ll need to copy the corresponding decryption routine (see final cell), or implement your own in the language of your choice.

This project is intended for educational and research purposes only.

