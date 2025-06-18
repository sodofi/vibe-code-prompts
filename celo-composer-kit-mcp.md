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
  
**2. Using Self Protocol to check for unique humans**

Add [Self Protocol docs](https://docs.self.xyz/) to Cursor context by clicking @ --> Docs --> Add new doc --> then pasting the link to the documentation.
```
I want to use Self Protocol so that the user has to prove they are human before they can claim the token. 

Frontend Requirements:

Replace existing claim button with "Verify Humanity to Claim 10 Tokens"
Follow the Self documentation quickstart guide to implement that QRCodeGenerator react component
On button click, display Self Protocol QR code for verification request
Poll for verification status or handle verification response
Update button to "Claim 10 Tokens" once verification succeeds
Update composer-kit identity UI component to show valid human checkmark on identity card

Backend Requirements:

Implement Self Protocol backend SDK integration (following their quickstart pattern)
The verification logic to only require isValidProof to be true
Create endpoint to initiate verification request
Create endpoint to verify submitted proofs
Return verification status to frontend
Ensure proof validation before allowing token claims

Technical Specifications:

Use Self Protocol's QR code generation for verification requests
Implement proper error handling for failed verifications
Maintain existing token claim logic, but gate it behind successful human verification
Update UI state management to track verification status
Ensure verification state persists appropriately for user session

Expected Flow:
User clicks verify button → QR code displayed → User scans with Self app → Backend validates proof → UI updates to show verified status → User can claim tokens
Please implement this integration while maintaining the existing app architecture and user experience patterns.
```

```
I want to use Self Protocol so that the user has to prove they are human before they can claim the token.
Frontend Requirements:
Replace existing claim button with "Verify Humanity to Claim 10 Tokens"
Follow the Self documentation quickstart guide to implement QRCodeGenerator react component
CRITICAL: Use default import for QRCodeGenerator: import QRCodeGenerator from '@selfxyz/qrcode';
CRITICAL: Use shorter scope name (max ~10 characters) like 'my-app' to avoid BigInt size errors
CRITICAL: Use shorter RPC endpoint like 'https://forno.celo.org' instead of long URLs
On button click, display Self Protocol QR code for verification request
Poll for verification status or handle verification response
Update button to "Claim 10 Tokens" once verification succeeds
Update composer-kit identity UI component to show valid human checkmark on identity card
Backend Requirements:
Implement Self Protocol backend SDK integration (following their quickstart pattern)
CRITICAL: The verification logic should only require result.isValidDetails.isValidProof to be true, NOT result.isValid
CRITICAL: Use direct 3-letter ISO country codes like "IRN" and "PRK" instead of countryCodes.IRN constants
CRITICAL: Use the same shorter scope name as frontend (e.g., 'my-app') to ensure consistency
CRITICAL: Use the same shorter RPC endpoint as frontend (e.g., 'https://forno.celo.org')
Create endpoint to initiate verification request
Create endpoint to verify submitted proofs
Return verification status to frontend
Ensure proof validation before allowing token claims
Technical Specifications:
Use Self Protocol's QR code generation for verification requests
CRITICAL: Ensure both frontend and backend use identical scope names and RPC endpoints
CRITICAL: Keep scope names short (under 10 characters) to prevent "BigInt exceeds maximum size of 31 bytes" errors
Implement proper error handling for failed verifications
Maintain existing token claim logic, but gate it behind successful human verification
Update UI state management to track verification status
Ensure verification state persists appropriately for user session
Expected Flow:
User clicks verify button → QR code displayed → User scans with Self app → Backend validates proof (only checking cryptographic validity) → UI updates to show verified status → User can claim tokens
Key Implementation Notes:
BigInt Error Prevention: Use short scope names and RPC URLs to avoid internal hashing limits
Country Code Format: Use 3-letter ISO codes directly as strings, not SDK constants
Verification Logic: Only validate isValidProof field, ignore scope/attestation/nationality validation failures
Import Format: Use default imports for QRCodeGenerator component
Configuration Consistency: Ensure frontend and backend use identical configuration values
Please implement this integration while maintaining the existing app architecture and user experience patterns.
```
