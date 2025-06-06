# Vibe Coding Mini App Prompts

### Tools Used
1. Claude --> Design your app and generate a prompt
2. V0 --> Create the front end
3. Cursor --> Build the final app
4. Farcaster --> Get users and testing

## Prompts

### Designing the App using Claude

Past the following prompt into Claude:

`I want you to create a lightweight IQ quiz contest. the quiz should be timed and only be 10 questions. At the end it will have a button that says 'see score' and it will generate your IQ quiz score. For the UI, I want you to use a clean UI that mirrors that of other IQ tests. Don't ask IQ questions with images. After the quiz is completed, I want you to have a button that prompts the user to see which answers they got wrong, which one is the right answer, and then explain how the score was calculated. I want you to create a prompt for v0 with an in depth explanation for what I want to build. No need to code the app, just create a detailed prompt. `

### Creating the Front End

Prompt Claude generated:

I want you to create a lightweight IQ quiz contest. the quiz should be timed and only be 10 questions. At the end it will have a button that says 'see score' and it will generate your IQ quiz score. For the UI, I want you to use a clean UI that mirrors that of other IQ tests. Don't ask IQ questions with images. After the quiz is completed, I want you to have a button that prompts the user to see which answers they got wrong, which one is the right answer, and then explain how the score was calculated. 

### Creating Onchain Interactions

1. Open the [Farcaster docs](https://miniapps.farcaster.xyz/docs/getting-started). In the top right, click on `Ask with ChatGPT`
   
Prompt for ChatGPT:

I want you to create a prompt to Cursor Claude 3.5 to explain to it how to setup a wagmi connector and add the react hook into my IQ quiz contest app. The desired goal I have is that once the user completes the test and hits 'See Score' it requires users to pay 0.1 CELO to me to see their IQ score. 

Output:

I'm developing an IQ quiz contest app as a Farcaster Mini App. After users complete the quiz and click 'See Score', they should be prompted to pay 0.1 CELO to access their results. Please provide a step-by-step guide to:
- Ensure Farcaster Mini App Compatibility:
  - Set up the Farcaster SDK in my React project.
  - Create and configure the farcaster.json file with necessary metadata, including accountAssociation and frame details.
  - Ensure the app adheres to Farcaster's Mini App specifications.

- Integrate Wallet Connection and CELO Payment:
  - Implement a function that, upon clicking 'See Score', checks if the user's wallet is connected.
  - If not connected, prompt the user to connect their wallet.
  - Once connected, initiate a transaction requesting 0.1 CELO from the user's wallet to my address.
  - Ensure the transaction is confirmed before displaying the IQ score.

Provide code snippets and explanations for each step, ensuring the solution aligns with best practices for React, Wagmi, and Farcaster Mini Apps integration
