# Cardano Governance Parameter Overview

**Author:** Nicolas Cerny, Governance Lead  
**Affiliation:** Cardano Foundation  
**Date:** 2 February 2024

The Cardano protocol will soon undergo one of its most exciting upgrades, implementing a minimal viable on-chain governance model. The details of this groundbreaking innovation are described in [Cardano Improvement Proposal (CIP) 1694](https://cips.cardano.org/cip/CIP-1694). To successfully transition to this new phase, Cardano also requires new protocol parameters that ensure the overall success of the implemented model.

The newly introduced parameters were defined in the governance group, which you can find [here](https://github.com/cardano-foundation/CIPs/tree/master/CIP-1694#protocol-parameter-groups). These parameters will become available and applicable on the Cardano mainnet after the Chang hard fork, which will implement the on-chain governance model. These parameters and many other features are already implemented on [SanchoNet](https://sancho.network/), the governance testnet for Cardano.

For better understanding and clarity, we will categorize the parameters into three groups:

1. [Governance Action Parameters](#governance-action-parameters)
2. [Delegated Representative Parameters](#delegated-representative-parameters)
3. [Constitutional Committee Parameters](#constitutional-committee-parameters)

Down below, you will find a description of all the currently available governance parameters and their purpose.

*Disclaimer: We cannot guarantee this will be the final list of governance parameters. This list includes all known governance parameters by 26 January 2024*

---

## Table of Contents

- [Governance Action Parameters](#governance-action-parameters)
  - [Governance Action Thresholds](#governance-action-thresholds)
  - [SPO Governance Voting Threshold Parameters](#spo-governance-voting-threshold-parameters)
  - [DRep Governance Voting Threshold Parameters](#drep-governance-voting-threshold-parameters)
- [Delegated Representative Parameters](#delegated-representative-parameters)
- [Constitutional Committee Parameters](#constitutional-committee-parameters)
- [Glossary](#glossary)

---

## Governance Action Parameters

There are currently seven different governance action types that any ada holder can create. All parameters centered around governance actions are part of this group. These parameters include the approval thresholds on the various governance actions that apply to the delegated representatives (DReps) or stake pool operators (SPOs) and two parameters that apply to all governance action types.

Governance actions must be approved by at least two groups of SPOs, DReps, or the CC. The detailed breakdown can be found [here](https://github.com/cardano-foundation/CIPs/tree/master/CIP-1694#requirements).

### Governance Action Thresholds

A threshold per governance action type must be met to ratify and enact a governance action on-chain. At all times, at least two of the three governance roles of SPOs, DReps, and CC must approve a single governance action. The detailed breakdown can be found [here](https://github.com/cardano-foundation/CIPs/tree/master/CIP-1694#requirements). The SPO vote threshold is measured as a percentage of the total delegated active stake for the epoch. The DRep vote threshold is calculated as a percentage of the active voting stake.

Note that an explicit vote to abstain differs from abstaining from voting. Unregistered stake that did not vote behaves like an 'Abstain' vote, while registered stake that did not vote behaves like a 'No' vote.

#### SPO Governance Voting Threshold Parameters

---

In the current system stake pool operators can vote on four out of the seven governance action types. Their vote threshold is measured as a percentage of the total delegated active stake for the epoch.

#### Pool vote threshold Motion of No-Confidence (`pvt_motion_no_confidence`)

---

This parameter indicates the threshold of required Yes votes that must be met as a percentage of the stake held by all stake pools to pass a motion of no-confidence governance action.

A ratified motion of no-confidence governance action shifts the current constitutional committee into a state of no-confidence. In this state, the current CC cannot participate in governance and has to be replaced before any governance actions can be ratified.

`Data Type: Percentage displayed in decimal format (e.g., 0.51 for 51%)`

#### Pool vote threshold Committee Normal State (`pvt_committee_normal`)

---

This parameter only applies if the current constitutional committee is in a state of confidence.

This parameter indicates the threshold of required Yes votes that must be met as a percentage of the stake held by all stake pools to replace the constitutional committee and/or change the committee threshold. The committee threshold is the fraction of committee Yes votes required to ratify governance actions.

`Data Type: Percentage displayed in decimal format (e.g., 0.51 for 51%)`

#### Pool vote threshold Committee No-Confidence State (`pvt_committee_no_confidence`)

---

This parameter only applies if the current constitutional committee is in a state of no confidence.

This parameter indicates the threshold of required Yes votes that must be met as a percentage of the stake held by all stake pools to replace the constitutional committee and/or the committee threshold. The committee threshold is the fraction of committee Yes votes required to ratify governance actions.

`Data Type: Percentage displayed in decimal format (e.g., 0.51 for 51%)`

#### Pool vote threshold Hard-Fork Initiation (`pvt_hard_fork_initiation`)

---

This parameter indicates the threshold of required Yes votes that must be met as a percentage of the stake held by all stake pools to initiate a hard fork.

It is important to note that SPOs must upgrade their nodes regardless of the hard fork initiation governance action. This implies that SPOs only vote yes on a hard fork initiation if they have successfully upgraded their Cardano node version.

`Data Type: Percentage displayed in decimal format (e.g., 0.51 for 51%)`

#### DRep Governance Voting Threshold Parameter

---

Unlike the constitutional committee or the SPOs, the delegated representatives can vote on every governance action type.

#### DRep vote threshold Motion of No-Confidence (`dvt_motion_no_confidence`)

---

This parameter indicates the threshold of required Yes votes that must be met as a percentage of the active voting stake delegated to all DReps to pass a motion of no-confidence governance action.

A ratified motion of no-confidence shifts the current constitutional committee into a state of no-confidence. In this state, the current CC cannot participate in governance actions and has to be replaced before any governance actions can be ratified. 

`Data Type: Percentage displayed in decimal format (e.g., 0.51 for 51%)`

#### DRep vote threshold Committee Normal State (`dvt_committee_normal`)

---

This parameter only applies if the current constitutional committee is in a state of confidence. 

This parameter indicates the threshold of required Yes votes that must be met as a percentage of the active voting stake delegated to all DReps to replace the constitutional committee and/or the committee threshold. The threshold is the fraction of committee Yes votes required to ratify governance actions.

`Data Type: Percentage displayed in decimal format (e.g., 0.51 for 51%)`

#### DRep vote threshold Committee No-Confidence State (`dvt_committee_no_confidence`)

---

This parameter only applies if the current constitutional committee is in a state of no confidence.

This parameter indicates the threshold of required Yes votes that must be met as a percentage of the active voting stake delegated to all DReps to replace the constitutional committee and/or the committee threshold. The threshold is the fraction of committee Yes votes required to ratify governance actions.

`Data Type: Percentage displayed in decimal format (e.g., 0.51 for 51%)`

#### DRep vote threshold Protocol Parameters Update to Constitution (`dvt_update_to_constitution`)

---

This parameter indicates the threshold of required Yes votes that must be met as a percentage of the active voting stake delegated to all DReps to update the constitution or proposal policy.

The Cardano constitution will first be a text document that defines Cardano's shared values and guiding principles with the long-term sustainability of the Cardano protocol in mind. In this stage, the Constitution will live as an off-chain document with its hash digest value recorded on stage. In the future, the Constitution could become a smart-contract-based rule set that guides the entire governance framework. 

`Data Type: Percentage displayed in decimal format (e.g., 0.51 for 51%)`

#### DRep vote threshold Hard-Fork Initiation (`dvt_hard_fork_initiation`)

---

This parameter indicates the threshold of required Yes votes that must be met as a percentage of the active voting stake delegated to all DReps to initiate a hard fork.

It is important to note that SPOs must upgrade their nodes regardless of the hard fork initiation governance action.

`Data Type: Percentage displayed in decimal format (e.g., 0.51 for 51%)`

#### DRep vote threshold Protocol Parameters Network Group (`dvt_p_p_network_group`) 

---

This parameter indicates the threshold of required Yes votes that must be met as a percentage of the active voting stake delegated to all DReps to update protocol parameters within the network group.

A list of parameters in the network group can be found in CIP-1694. https://github.com/cardano-foundation/CIPs/tree/master/CIP-1694#protocol-parameter-groups

For further information about protocol parameters and their current values and update history, check https://beta.explorer.cardano.org/en/protocol-parameters/.

`Data Type: Percentage displayed in decimal format (e.g., 0.51 for 51%)`

#### DRep vote threshold Protocol Parameters Economic Group (`dvt_p_p_economic_group`)

---

This parameter indicates the threshold of required Yes votes that must be met as a percentage of the active voting stake delegated to all DReps to update protocol parameters within the economic group.

A list of parameters in the economic group can be found in CIP-1694. https://github.com/cardano-foundation/CIPs/tree/master/CIP-1694#protocol-parameter-groups

For further information about protocol parameters and their current values and update history, check https://beta.explorer.cardano.org/en/protocol-parameters/.

`Data Type: Percentage displayed in decimal format (e.g., 0.51 for 51%)`

#### DRep vote threshold Protocol Parameters Technical Group (`dvt_p_technical_group`) 

---

This parameter indicates the threshold of required Yes votes that must be met as a percentage of the active voting stake delegated to all DReps to update protocol parameters within the technical group.

A list of parameters in the technical group can be found in CIP-1694. https://github.com/cardano-foundation/CIPs/tree/master/CIP-1694#protocol-parameter-groups

For further information about protocol parameters and their current values and update history, check https://beta.explorer.cardano.org/en/protocol-parameters/.

`Data Type: Percentage displayed in decimal format (e.g., 0.51 for 51%)`

#### DRep vote threshold Protocol Parameters Governance Group (`dvt_p_p_gov_group`) 

---

This parameter indicates the threshold of required Yes votes that must be met as a percentage of the active voting stake delegated to all DReps to update protocol parameters within the governance group.

A list of parameters in the governance group can be found in this document and CIP-1694. https://github.com/cardano-foundation/CIPs/tree/master/CIP-1694#protocol-parameter-groups

The parameters within the governance group have been newly introduced with CIP-1694.

`Data Type: Percentage displayed in decimal format (e.g., 0.51 for 51%)`

#### DRep vote threshold Protocol Parameters Treasury Withdrawal (`dvt_treasury_withdrawal`)

---

This parameter indicates the threshold of required Yes votes that must be met as a percentage of the active voting stake delegated to all DReps to approve a treasury withdrawal request.

`Data Type: Percentage displayed in decimal format (e.g., 0.51 for 51%)`

### Governance action maximum lifetime in epochs (`gov_action_lifetime`)

---

This parameter applies to all governance action types and indicates the period in epochs during which the governance action must be approved by at least two groups of SPOs, DReps, or the CC. The detailed breakdown can be found [here](https://github.com/cardano-foundation/CIPs/tree/master/CIP-1694#requirements). A governance action is considered ratified if it meets the approval thresholds. The protocol checks if an action meets the defined thresholds at each epoch transition.

Should the action not meet this threshold during this specified lifetime, it is considered expired, and the deposit amount will be returned to the provided Cardano address set in the governance action.

It is also important to note that ratified governance actions will automatically be enacted one epoch after they are ratified.

`Data Type: Number in epochs (e.g. four epochs)`

### Governance action deposit (`gov_action_deposit`)

---

This parameter applies to all governance action types and indicates the amount of ada, to be precise, the number of lovelaces, that must be deposited to submit a governance action on-chain.

Any ada holder can submit a governance action to the chain, given they provide an ada deposit amount, which will be returned when the action is finalized (whether it is ratified or has expired). The deposit amount will be added to the deposit pot, similar to stake key deposits. It will also be counted towards the stake of the reward address it will be paid back to, to not reduce the submitter's voting power to vote on their own (and competing) actions.

`Data Type: Lovelace amount ( e.g., 600000000 lovelace = 600 ada)`

## Delegated Representative Parameters

*Delegated Representatives (DReps)* are a new role introduced in CIP-1694. DReps, *Stake Pool Operators (SPOs)*, and the *Constitutional Committee (CC)* vote on Governance Actions (GAs). Similar to registering as an SPO, any ada holder interested can register as a DRep, allowing them to represent themselves. The average ada holder must decide whether to become a DRep or delegate their stake to a reliable one.

The two parameters considered DRep specific are the deposit amount ada holders must provide when registering as a DRep (`drepDeposit`) and the DRep activity period in epochs (`drepActivity`).

### DRep deposit amount (`drep_deposit`)

---

The deposit amount specifies the amount of ada anyone has to deposit if they wish to register as a DRep. The deposit amount will be returned to the ada holder once a valid retirement certificate has been submitted on-chain.

This methodology follows the SPO registration process, where SPOs must deposit 500 ada.

`Data Type: Lovelace amount ( e.g., 600000000 lovelace = 600 ada)`

### DRep activity period in epochs (`drep_activity`)

---

This parameter indicates the period in epochs that DReps are allowed to be inactive, meaning that even if the DRep doesn't vote during the period, it won't be a problem. Activity is measured by voting on governance actions.

Once registered, DReps will have to vote regularly to be considered active. Specifically, if a DRep does not submit any votes for `drepActivity`-many epochs, the DRep is considered inactive. The stake delegated to inactive DReps does not count towards the active voting stake. By voting on any governance action, an inactive DRep and the stake delegated to them will become active again for `drepActivity`-many epochs.

DReps become inactive after a certain period of not voting on any governance action so that DReps who stop participating but still have ada delegated to them do not eventually leave the system in a state where no governance action can pass.

`Data Type: Number in epochs (e.g., four epochs)`

## Constitutional Committee Parameters

The role of the constitutional committee is to decide about the constitutionality of a governance action, meaning they are here to check if the outcomes of a governance action may contradict what the Constitution specifies. If a governance action outcome contradicts the Constitution, the CC votes No.

The CC is considered to be in one of the following two states at all times:

1. a **normal state** (i.e., a state of confidence)
2. a **state of no-confidence**

In a state of no-confidence the current CC cannot participate in governance actions and has to be replaced before any governance actions can be ratified.

DReps and SPOs can replace the CC.

### Minimal constitutional committee size (`committee_min_size`)

---

The minimal constitutional committee size indicates the minimal number of individuals or entities, each associated with a pair of Ed25519 credentials, that have to be part of the committee.

The constitutional committee will automatically enter a state of no-confidence if the number of non-expired committee members falls below the minimal size of the committee.

`Data Type: Nonnegative number (e.g., 0,1,2,)`

### Maximum term length (in epochs) for the constitutional committee members (`committee_max_term_length`)

---

This parameter indicates the maximum number of epochs each constitutional committee member can serve consecutively. It is important to note that constitutional committee members can be actively voted out with a ratified "New constitutional committee" governance action or voluntarily retire. The approval thresholds for the "New constitutional committee" action depend on the current state of the committee.

`Data Type: Number in epochs (e.g., four epochs)`

## Glossary

- **Active Voting Stake:** The total amount of ada delegated to active DReps.
- **Difference between Abstaining to Vote and Vote to Abstain:** An explicit vote to abstain differs from abstaining from voting. Unregistered stake that did not vote behaves like an 'Abstain' vote, while registered stake that did not vote behaves like a 'No' vote.
- **Governance Parameters:** All parameters of the governance protocol parameter group. They can be seen as the settings of the on-chain governance model.
- **CIP-1694:** The Cardano Improvement proposal describing the future on-chain governance model on Cardano.
- **Chang Hard Fork:** This specific Cardano hard fork will introduce the on-chain governance model described in CIP-1694, scheduled for sometime in 2024.
- **Delegated Representative (DRep):** Delegated Representatives (DReps) are a new role introduced in the Age of Voltaire as part of the governance model proposed under CIP-1694. DReps will be one of the groups responsible for voting on all governance action types.
- **Stake Pool Operator (SPO):** The group responsible for block production and keeping the network operational. In addition, one of the groups responsible for voting on specific governance action types.
- **Constitutional Committee (CC):** The role of the constitutional committee is to decide about the constitutionality of a governance action, meaning they are here to check if the outcomes of a governance action may contradict what the Constitution specifies.
- **Voting Threshold:** Specific percentage per governance action type required to pass a vote.
- **Lovelace:** The smallest unit of Cardano's native cryptocurrency ada is the Lovelace. It is the equivalent of one-millionth of one ada.
- **Epoch:** In Cardano, it is a unit of time measurement. Each Cardano epoch consists of a number of slots, where each slot lasts for one second. A Cardano epoch currently includes 432,000 slots (5 days).
- **Governance Action (GA):** A governance action is an on-chain event triggered by a transaction with a deadline after which it cannot be enacted. There are seven different types of Governance actions. Any ada holder can submit a governance action to the chain.
- **Governance Action Ratification:** An action is said to be ratified when it gathers enough votes in its favor and passes the defined threshold.
- **Governance Action Expiration:** An action that fails to be ratified before its deadline is said to have expired.
- **Governance Action Enactment:** Governance actions are automatically enacted one epoch after they have been successfully ratified.
- **Hard Fork:** A hard fork refers to a significant update or upgrade to the blockchain protocol that is not backward compatible.
- **No-Confidence Motion:** One of the governance action types that, once ratified, shifts the current state of the constitutional committee into a state of no-confidence, which requires the appointment of a new CC.
- **Protocol Parameters:** Protocol parameters in Cardano are configurable values that define various operational aspects of the Cardano blockchain. For further information about protocol parameters and their current values and update history, check: <https://beta.explorer.cardano.org/en/protocol-parameters/>
- **Treasury Withdrawal Request:** One of the governance action types that allows any ada holder to request a treasury withdrawal request. If the action is ratified, the treasury will pay the specified amount.