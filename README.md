# Tutorial
[source](https://kndrck.co/posts/practical_guide_build_zk_dapps/)
[github](https://github.com/kendricktan/hello-world-zk-dapp)

# Project Structure

```bash
packages
  ├── circuits    # Zero knowledge circuits
  ├── contracts   # Smart contract logic
  └── scripts     # Scripts to interact with the deploy contracts
```

# Building the Solidity circuit
```bash
$(npm bin)/circom circuits/circuit.circom -o build/circuits/circuit.json

# snarkjs setup might take a few seconds
$(npm bin)/snarkjs setup --protocol groth -c build/circuits/circuit.json --pk build/circuits/provingKey.json --vk build/circuits/verifyingKey.json

# Generate solidity lib to verify proof
$(npm bin)/snarkjs generateverifier --pk build/circuits/provingKey.json --vk build/circuits/verifyingKey.json -v contracts/Verifier.sol

# You should now have a new "Verifier.sol" in your contracts directory
# $ ls contracts
# Migrations.sol Verifier.sol
```
