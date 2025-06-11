# Vibe Coding an App on Celo

## Setup

1. Go to Celo Docs --> Celo MCP [here](https://docs.celo.org/build/mcp/composer-mcp)
2. Follow instructions to install MCP server in Cursor
3. Use Claude-4-Sonnet inside of Cursor
4. [Add testnet tokens](https://faucet.celo.org/alfajores) to your wallet on Celo Alfajores 

## Prompts

  **1. Create app in Cursor to allow users to mint an ERC20**

```
Build a Celo dApp using the Celo Composer starter and the Composer Kit component library.

The app should use Hardhat for smart contract development, deploy an example ERC-20 contract on Celo Alfajores, and include a simple front end that connects a wallet and lets users mint 1 token and view their token balance.

Use @celo/react-components (Composer Kit) to design the UI. Make sure the UI is mobile-friendly.

Use the following layout:

A ConnectWallet button using Composer Kit

An input to specify that they want to mint one token.

A button to mint the token (calls contract function)

A display of current token balance

Integrate everything using Wagmi (for React hooks), Viem (for client), and Hardhat for contracts.

Make the folder structure compatible with the Celo Composer layout.
```

This will create an app using Celo Composer templates with Composer Kit UI components. It will create a sample .env file for you, but you will need to update it with your wallet addresses private key and Celoscan API key (optional). Make sure your wallet address has some testnet CELO to deploy your contract. 

**Use Cases:**

1. **Faucet dApp:** Let users mint a small number of test tokens to try out your system (common in testnets and dev environments).
    - Example: You're running a hackathon — devs mint test tokens to simulate real-world use.

2. **Reward / Reputation System:** Mint tokens to users for actions they take (e.g., filling out a form, completing onboarding).
    - Example: A learning dApp where users mint tokens for completing lessons, and balance reflects progress.

3. **Game or Loyalty Points:** Users mint tokens as game rewards or loyalty points — balance shows their standing or power level.
    - Example: You mint XP tokens after users win a game round.

4. **Token Airdrop / Claim Portal:** Let users mint tokens once after verifying eligibility (e.g., based on Self verification or allowlist).
    - Example: You mint 100 tokens to early users when they connect their wallet.

