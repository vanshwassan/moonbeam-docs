---
title: How to Vote on a Proposal 
description: Learn how to vote on a proposal and lock your tokens to either support or reject a proposal put forth for a referendum on Moonbeam via Governance v1 features.
---

# How to Vote on a Proposal in Governance v1

![Governance Moonbeam Banner](/images/tokens/governance/voting/voting-banner.png)

## Introduction {: #introduction } 

Once a proposal reaches public referenda, token holders can vote on it using their own tokens. Two factors defined the weight a vote has: the number of tokens locked and lock duration (called Conviction). This is to ensure that there is an economic buy-in to the result to prevent vote-selling. Consequently, the longer you are willing to lock your tokens, the stronger your vote will be weighted. You also have the option of not locking tokens at all, but vote weight is drastically reduced.

Referenda are simple, inclusive, and stake-based voting schemes. Each referendum has a proposal associated with it that suggests an action to take place. They have a fixed duration, after which votes are tallied, and the action is enacted if the vote is approved.

In Moonbeam, users will be able to create, second, and vote on proposals using their H160 address and private key, that is, their regular Ethereum account!

Moonbeam's governance system is in the process of getting revamped! This next phase of governance is known as OpenGov (Governance). During the roll-out process, OpenGov will be rigorously tested on Moonriver before a proposal will be made to deploy it on Moonbeam. Until it launches on Moonbeam, Moonbeam will continue to use Governance v1. As such, **this guide is for proposals on Moonbeam only**. If you're looking to vote on a proposal on Moonriver or Moonbase Alpha, you can refer to the [How to Vote on a Proposal in OpenGov](/tokens/governance/voting/opengov-voting){target=_blank} guide.

This guide will outline the process, with step-by-step instructions, of how to vote on referenda in Governance v1 on Moonbeam. For more information on Moonbeam's governance system, including Governance v1 and OpenGov (Governance v2), please refer to the [governance overview page](/learn/features/governance/){target=_blank}.

!!! note
    This page goes through the mechanics on how to vote at a more techincal level. Token holders can leverage platforms such as [Polkassembly](https://moonbeam.network/tutorial/participate-in-moonbeam-governance-with-polkassembly/){target=_blank} to vote using a more friendly user interface. 

## Definitions {: #definitions } 

Some of the key parameters for this guide are the following:

 - **Voting Period** — the time token holders have to vote for a referendum (duration of a referendum)

--8<-- 'text/governance/vote-conviction-definitions.md'

    For more information on the vote multiplier parameters, please refer to the [Conviction Multiplier section of the Governance v1 docs](/learn/features/governance/#conviction-multiplier){target=_blank}

 - **Turnout** — the total number of voting tokens
 - **Electorate** — the total number of tokens issued in the network
 - **Maximum number of votes** — the maximum number of votes per account
 - **Enactment Period** — the time between a proposal being approved and enacted (make law). It is also the minimum locking period when voting
 - **Lock Period** — the time (after the proposal's enactment) that tokens of the winning voters are locked. Users can still use these tokens for staking or voting
 - **Delegation** — the act of transferring your voting power to another account for up to a certain conviction

=== "Moonbeam"
    |        Variable         |                                                         Value                                                         |
    |:-----------------------:|:---------------------------------------------------------------------------------------------------------------------:|
    | Maximum number of votes |                                      {{ networks.moonbeam.democracy.max_votes}}                                       |
    |      Voting Period      |  {{ networks.moonbeam.democracy.vote_period.blocks}} blocks ({{ networks.moonbeam.democracy.vote_period.days}} days)  |
    |    Enactment Period     | {{ networks.moonbeam.democracy.enact_period.blocks}} blocks ({{ networks.moonbeam.democracy.enact_period.days}} days) |

## Roadmap of a Proposal {: #roadmap-of-a-proposal } 

This guide will cover the steps highlighted in the proposal roadmap diagram below. Primarily, you'll be learning how to vote on public referenda.

You can find a full explanation of the [happy path for a Governance v1 proposal on the Governance overview page](/learn/features/governance/#roadmap-of-a-proposal){target=_blank}.

![Proposal Roadmap](/images/tokens/governance/voting/proposal-roadmap.png)

--8<-- 'text/governance/forum-discussion.md'

## Voting on a Referendum {: #voting-on-a-referendum } 

This section goes over the process of voting on a referendum. The guide assumes that there is one already taking place, in this case, the one created in the [How to Propose an Action](/tokens/governance/proposals/){target=_blank} guide.

!!! note
    This guide was done with a customized version of Moonbeam with short Launch/Enactment Periods for demonstration purposes only. You can adapt these instructions for Moonbeam.

To vote on a proposal in the network, you need to use the Polkadot.js Apps interface. To do so, you need to import an Ethereum-style account first (H160 address), which you can do by following the [Creating or Importing an H160 Account](/tokens/connect/polkadotjs/#creating-or-importing-an-h160-account){target=_blank} guide. For this example, three accounts were imported and named with super original names: Alice, Bob, and Charley.

![Accounts in Polkadot.js](/images/tokens/governance/voting/vote-1.png)

The proposal being voted will embed the remark "This is a unique string." on chain permanently.

### How to Vote {: #how-to-vote } 

To get started, you'll need to navigate to [Moonbeam's Polkadot.js Apps interface](https://polkadot.js.org/apps/?rpc=wss://wss.api.moonbeam.network){target=_blank}. Everything related to governance lives under the **Democracy** tab, where (in the image) you can note that there is a number next to it, indicating there are democracy items pending (either proposals or referenda). Once there, you can view the details of the referendum you want to vote by clicking on the arrow next to the description. The number next to the action and description it is called the referendum index (in this case, it is `20`). When ready, click on the **Vote** button.

![Vote Button](/images/tokens/governance/voting/vote-2.png)

Here, you need to provide the following information:

 1. Select the account with which you want to vote
 2. Enter the number of tokens that you want to vote with. These will be locked for the amount of time specified in the next step. Remember, you need to save a small amount of tokens for gas. If you try to vote with your entire balance the transaction will fail.
 3. Set the vote conviction, which determines its weight (`vote_weight = tokens * conviction_multiplier`). Please refer to the [Conviction Multiplier](/learn/features/governance/#conviction-multiplier){target=_blank} docs for more information
 4. Click on **Vote Aye** to approve the proposal or **Vote Nay** to disapprove the proposal, and then sign the transaction

![Vote Submission](/images/tokens/governance/voting/vote-3.png)

!!! note
    The lockup periods shown in the previous image are not to be taken as reference. This guide was done with a customized version of Moonbeam with short Launch/Enactment Periods for demonstration purposes only.

In this case, Alice and Bob have decided to **Vote Aye** on the proposal with a Conviction of `6x`. On the other hand, Charley has decided to **Vote Nay** on the proposal but chose not to lock any tokens (his tokens are only locked during the duration of the referendum), so his Conviction was `0.1x`. With such vote distributions, the partial results can be seen in the main **Democracy** tab.

![Vote Information](/images/tokens/governance/voting/vote-4.png)

From voting, there are some key takeaways:

 - Alice's weighted vote is 60000 units. That is, her 10000 locked tokens multiplied her Conviction by x6
 - Bob's weighted vote is 60 units. That is, his 10 locked tokens multiplied his Conviction by x6
 - Charley's weighted vote is 0.8 units. That is, his 8 tokens with no locking period (only during referendum) made his Conviction factor x0.1
 - Both the remaining voting period and time before the proposal is enacted (if passed) are shown on the screen
 - The overall turnout (in percentage) is just 0.09%. This is calculated as the total number of voting tokens (10018) divided by the total amount of tokens in the network (11.13M in this case)
 - Even though the turnout is quite low, the proposal is tentatively approved because of the super-majority approval. More information can be found in the [Positive Turnout Bias](/learn/features/governance/#positive-turnout-bias) section
 - It is important to write down the referendum index, as this is needed to unlock the tokens later when the locking period expires. Currently there is no way to retrieve the referendum index once it has been enacted

After the voting period has expired, the proposal will be visible under the **Dispatch** tab if approved. In here, you can also see the time remaining until the proposal is enacted.

![Proposal Enactment](/images/tokens/governance/voting/vote-5.png)

### Delegate Voting {: #delegate-voting } 

Token holders have the option to delegate their vote to another account whose opinion they trust. The account being delegated does not need to make any particular action. When they vote, the vote weight (that is, tokens times the Conviction multiplier chose by the delegator) is added to its vote.

To delegate your vote, first, navigate to the **Extrinsics** menu under the **Developers** tab.

![Extrinsics Menu](/images/tokens/governance/voting/vote-6.png)

!!! note
    If you try to delegate tokens to a person who has already voted, the transaction will fail. Consider using a new account for the below steps.

Here, you need to provide the following information:

 1. Select the account from which you want to delegate your vote
 2. Choose the pallet you want to interact with. In this case, it is the `democracy` pallet
 3. Choose the extrinsic method to use for the transaction. This will determine the fields that need to fill in the following steps. In this case, it is `delegate` extrinsic
 4. Select the account to which you want to delegate your vote
 5. Set the vote conviction, which determines its weight (`vote_weight = tokens * conviction_multiplier`). The Conviction multiplier is related to the number of enactment periods the tokens will be locked for. Consequently, the longer you are willing to lock your tokens, the stronger your vote will be weighted. You also have the option of not locking tokens at all, but vote weight is drastically reduced
 6. Set the number of tokens you want to delegate to the account provided before
 7. Click the **Submit Transaction** button and sign the transaction

![Extrinsics Transaction for Delegation](/images/tokens/governance/voting/vote-7.png)

In this example, Alice delegated a total weight of 1000 (1000 tokens with an x1 Conviction factor) to Charley. To verify the delegation, click the blue circle on the left that indicates a delegation exists.

![View Delegation](/images/tokens/governance/voting/vote-8.png)

!!! note
    Another way to delegate votes is under the **Accounts** tab. Click on the three dots of the account from which you want to delegate your vote and fill in the information as before.

Once the account you have delegated your vote to votes, the total vote weight delegated will be allocated to the option that the account selected. For this example, Charley has decided to vote in favor of a proposal that is in public referendum. He voted with a total weight of 800 (800 tokens with an x1 Conviction factor). But because Alice delegated 1000 vote weight to him, **Aye** votes total 1800 units.

![Total Votes with Delegation](/images/tokens/governance/voting/vote-9.png)

To remove delegation, repeat the process described before, but select the `undelegate` extrinsic in step 3.

From vote delegation, there are some key takeaways:

 - If a token holder were to remove the vote delegation during a public referendum where the delegated votes were used, these would be removed from the tally
 - A token holder that delegated votes still has an economic buy-in. This means that if the option the delegator selected were to win, the tokens delegated are locked for the number of Lock Periods
 - The tokens delegated for voting are no longer part of the token holder's free balance. To read more about the types of balances, you can visit the Polkadot Wiki page on [Free vs. Reserved vs. Locked vs. Vesting Balance](https://wiki.polkadot.network/docs/build-protocol-info#free-vs-reserved-vs-locked-vs-vesting-balance)
 - A token holder that delegated tokens can't participate in public referendum. First, the token holder must undelegate his vote
 - A token holder that delegated tokens needs to manually unlock his locked tokens after the locking period has expired. For this, it is necessary to know the referendum index

### Unlocking Locked Tokens {: #unlocking-locked-tokens } 

When token holders vote, the tokens used are locked and cannot be transferred. You can verify if you have any locked tokens in the **Accounts** tab, expanding the address's account details to query. There, you will see different types of balances. If you hover over the icon next to **democracy**, an information panel will show telling you the current status of your lock. Different lock status includes:

 - Locked because of an ongoing referendum, meaning that you've used your tokens and have to wait until the referendum finishes, even if you've voted with a no-lock Conviction factor
 - Locked because of the Conviction multiplier selected, displaying the number of blocks and time left
 - Lock expired, meaning that you can now get your tokens back

![Account Lock Status](/images/tokens/governance/voting/vote-10.png)

Once the lock is expired, you can request your tokens back. To do so, navigate to the **Extrinsics** menu under the **Developers** tab.

![Extrinsics Menu](/images/tokens/governance/voting/vote-11.png)

Here, two different extrinsics need to be sent. First, you need to provide the following information:

 1. Select the account from which you want to recover your tokens
 2. Choose the pallet you want to interact with. In this case, it is the `democracy` pallet
 3. Choose the extrinsic method to use for the transaction. This will determine the fields that need to fill in the following steps. In this case, it is `removeVote` extrinsic. This step is necessary to unlock the tokens. This extrinsic can be used as well to remove your vote from a referendum
 4. Enter the referendum index. This is the number that appeared on the left-hand side in the **Democracy** tab. In this case, it is 0
 5. Click the **Submit Transaction** button and sign the transaction

![Remove Vote Extrinsics](/images/tokens/governance/voting/vote-12.png)

For the next extrinsic, you need to provide the following information:

 1. Select the account from which you want to recover your tokens
 2. Choose the pallet you want to interact with. In this case, it is the `democracy` pallet
 3. Choose the extrinsic method to use for the transaction. This will determine the fields that need to fill in the following steps. In this case, it is `unlock` extrinsic
 4. Enter the target account that will receive the unlocked tokens. In this case, the tokens will be returned to Alice
 5. Click the **Submit Transaction** button and sign the transaction

![Unlock Extrinsics](/images/tokens/governance/voting/vote-13.png)

Once the transaction goes through, the locked tokens should be unlocked. To double-check, you can go back to the **Accounts** tab and see that, for this example, Alice has her full balance as **transferable**.

![Check Balance](/images/tokens/governance/voting/vote-14.png)