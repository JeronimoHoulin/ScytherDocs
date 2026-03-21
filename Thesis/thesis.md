# Scyther thesis

## The objective

Generate Alpha in DeFi.

Chase Yield, Farm points, auto-compound into the same vault.

## The setup

Safe A "The Vault" -> This one holds $$$
 |
 |
  --->  Roles Modifier (contract deployed by Safe A that let's Safe B perform certain actions on Safe A, any ill-intended transaction that is NOT pre-approved will revert)

Safe B "The Operator" -> this one doesn't need a lot of signers / security checks, it can perform ONLY pre-approved txns. 

Tom -> Our AI buddy that holds a PROPOSER role in Safe B.
 |
 |
  ---> Proposer role means Tom can only suggest txns (add tem in the Safe's queue) but NOT execute anything by himself. He's just here to help out, make execution quick. 


## The "trustless" approach

Because the Operator would need the Vault to approve permissions to deposit funds in a new protocol, contract, pool..etc. We simply set the following conditions; 

Condition #1: 
New permissions are publicly announced in TG channel "Permissions Proposals"

Condition #2:
30 days (1month) needs to pass between permission proposal and it's execution. 

Condition #3:
The Vault executes settlements every 7 days (weekly) leaving 4 windows of opportunitiy for users to withdraw funds if they are discontent wiht the proposed permission. 

