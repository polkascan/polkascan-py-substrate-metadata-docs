
# AdvisoryCommittee

---------
## Calls

---------
### close
Close a vote that is either approved, disapproved or whose voting period has ended.

May be called by any signed account in order to finish voting and close the proposal.

If called before the end of the voting period it will only close the vote if it is
has enough votes to be approved or disapproved.

If called after the end of the voting period abstentions are counted as rejections
unless there is a prime member set and the prime member cast an approval.

If the close operation completes successfully with disapproval, the transaction fee will
be waived. Otherwise execution of the approved operation will be charged to the caller.

+ `proposal_weight_bound`: The maximum amount of weight consumed by executing the closed
proposal.
+ `length_bound`: The upper bound for the length of the proposal in storage. Checked via
`storage::read` so it is `size_of::&lt;u32&gt;() == 4` larger than the pure length.

\# &lt;weight&gt;
\#\# Weight
- `O(B + M + P1 + P2)` where:
  - `B` is `proposal` size in bytes (length-fee-bounded)
  - `M` is members-count (code- and governance-bounded)
  - `P1` is the complexity of `proposal` preimage.
  - `P2` is proposal-count (code-bounded)
- DB:
 - 2 storage reads (`Members`: codec `O(M)`, `Prime`: codec `O(1)`)
 - 3 mutations (`Voting`: codec `O(M)`, `ProposalOf`: codec `O(B)`, `Proposals`: codec
   `O(P2)`)
 - any mutations done while executing `proposal` (`P1`)
- up to 3 events
\# &lt;/weight&gt;
#### Attributes
| Name | Type |
| -------- | -------- | 
| proposal_hash | `T::Hash` | 
| index | `ProposalIndex` | 
| proposal_weight_bound | `Weight` | 
| length_bound | `u32` | 

#### Python
```python
call = substrate.compose_call(
    'AdvisoryCommittee', 'close', {
    'index': 'u32',
    'length_bound': 'u32',
    'proposal_hash': 'scale_info::11',
    'proposal_weight_bound': {
        'proof_size': 'u64',
        'ref_time': 'u64',
    },
}
)
```

---------
### close_old_weight
Close a vote that is either approved, disapproved or whose voting period has ended.

May be called by any signed account in order to finish voting and close the proposal.

If called before the end of the voting period it will only close the vote if it is
has enough votes to be approved or disapproved.

If called after the end of the voting period abstentions are counted as rejections
unless there is a prime member set and the prime member cast an approval.

If the close operation completes successfully with disapproval, the transaction fee will
be waived. Otherwise execution of the approved operation will be charged to the caller.

+ `proposal_weight_bound`: The maximum amount of weight consumed by executing the closed
proposal.
+ `length_bound`: The upper bound for the length of the proposal in storage. Checked via
`storage::read` so it is `size_of::&lt;u32&gt;() == 4` larger than the pure length.

\# &lt;weight&gt;
\#\# Weight
- `O(B + M + P1 + P2)` where:
  - `B` is `proposal` size in bytes (length-fee-bounded)
  - `M` is members-count (code- and governance-bounded)
  - `P1` is the complexity of `proposal` preimage.
  - `P2` is proposal-count (code-bounded)
- DB:
 - 2 storage reads (`Members`: codec `O(M)`, `Prime`: codec `O(1)`)
 - 3 mutations (`Voting`: codec `O(M)`, `ProposalOf`: codec `O(B)`, `Proposals`: codec
   `O(P2)`)
 - any mutations done while executing `proposal` (`P1`)
- up to 3 events
\# &lt;/weight&gt;
#### Attributes
| Name | Type |
| -------- | -------- | 
| proposal_hash | `T::Hash` | 
| index | `ProposalIndex` | 
| proposal_weight_bound | `OldWeight` | 
| length_bound | `u32` | 

#### Python
```python
call = substrate.compose_call(
    'AdvisoryCommittee', 'close_old_weight', {
    'index': 'u32',
    'length_bound': 'u32',
    'proposal_hash': 'scale_info::11',
    'proposal_weight_bound': 'u64',
}
)
```

---------
### disapprove_proposal
Disapprove a proposal, close, and remove it from the system, regardless of its current
state.

Must be called by the Root origin.

Parameters:
* `proposal_hash`: The hash of the proposal that should be disapproved.

\# &lt;weight&gt;
Complexity: O(P) where P is the number of max proposals
DB Weight:
* Reads: Proposals
* Writes: Voting, Proposals, ProposalOf
\# &lt;/weight&gt;
#### Attributes
| Name | Type |
| -------- | -------- | 
| proposal_hash | `T::Hash` | 

#### Python
```python
call = substrate.compose_call(
    'AdvisoryCommittee', 'disapprove_proposal', {'proposal_hash': 'scale_info::11'}
)
```

---------
### execute
Dispatch a proposal from a member using the `Member` origin.

Origin must be a member of the collective.

\# &lt;weight&gt;
\#\# Weight
- `O(M + P)` where `M` members-count (code-bounded) and `P` complexity of dispatching
  `proposal`
- DB: 1 read (codec `O(M)`) + DB access of `proposal`
- 1 event
\# &lt;/weight&gt;
#### Attributes
| Name | Type |
| -------- | -------- | 
| proposal | `Box<<T as Config<I>>::Proposal>` | 
| length_bound | `u32` | 

#### Python
```python
call = substrate.compose_call(
    'AdvisoryCommittee', 'execute', {
    'length_bound': 'u32',
    'proposal': 'Call',
}
)
```

---------
### propose
Add a new proposal to either be voted on or executed directly.

Requires the sender to be member.

`threshold` determines whether `proposal` is executed directly (`threshold &lt; 2`)
or put up for voting.

\# &lt;weight&gt;
\#\# Weight
- `O(B + M + P1)` or `O(B + M + P2)` where:
  - `B` is `proposal` size in bytes (length-fee-bounded)
  - `M` is members-count (code- and governance-bounded)
  - branching is influenced by `threshold` where:
    - `P1` is proposal execution complexity (`threshold &lt; 2`)
    - `P2` is proposals-count (code-bounded) (`threshold &gt;= 2`)
- DB:
  - 1 storage read `is_member` (codec `O(M)`)
  - 1 storage read `ProposalOf::contains_key` (codec `O(1)`)
  - DB accesses influenced by `threshold`:
    - EITHER storage accesses done by `proposal` (`threshold &lt; 2`)
    - OR proposal insertion (`threshold &lt;= 2`)
      - 1 storage mutation `Proposals` (codec `O(P2)`)
      - 1 storage mutation `ProposalCount` (codec `O(1)`)
      - 1 storage write `ProposalOf` (codec `O(B)`)
      - 1 storage write `Voting` (codec `O(M)`)
  - 1 event
\# &lt;/weight&gt;
#### Attributes
| Name | Type |
| -------- | -------- | 
| threshold | `MemberCount` | 
| proposal | `Box<<T as Config<I>>::Proposal>` | 
| length_bound | `u32` | 

#### Python
```python
call = substrate.compose_call(
    'AdvisoryCommittee', 'propose', {
    'length_bound': 'u32',
    'proposal': 'Call',
    'threshold': 'u32',
}
)
```

---------
### set_members
Set the collective&\#x27;s membership.

- `new_members`: The new member list. Be nice to the chain and provide it sorted.
- `prime`: The prime member whose vote sets the default.
- `old_count`: The upper bound for the previous number of members in storage. Used for
  weight estimation.

Requires root origin.

NOTE: Does not enforce the expected `MaxMembers` limit on the amount of members, but
      the weight estimations rely on it to estimate dispatchable weight.

\# WARNING:

The `pallet-collective` can also be managed by logic outside of the pallet through the
implementation of the trait [`ChangeMembers`].
Any call to `set_members` must be careful that the member set doesn&\#x27;t get out of sync
with other logic managing the member set.

\# &lt;weight&gt;
\#\# Weight
- `O(MP + N)` where:
  - `M` old-members-count (code- and governance-bounded)
  - `N` new-members-count (code- and governance-bounded)
  - `P` proposals-count (code-bounded)
- DB:
  - 1 storage mutation (codec `O(M)` read, `O(N)` write) for reading and writing the
    members
  - 1 storage read (codec `O(P)`) for reading the proposals
  - `P` storage mutations (codec `O(M)`) for updating the votes for each proposal
  - 1 storage write (codec `O(1)`) for deleting the old `prime` and setting the new one
\# &lt;/weight&gt;
#### Attributes
| Name | Type |
| -------- | -------- | 
| new_members | `Vec<T::AccountId>` | 
| prime | `Option<T::AccountId>` | 
| old_count | `MemberCount` | 

#### Python
```python
call = substrate.compose_call(
    'AdvisoryCommittee', 'set_members', {
    'new_members': ['AccountId'],
    'old_count': 'u32',
    'prime': (None, 'AccountId'),
}
)
```

---------
### vote
Add an aye or nay vote for the sender to the given proposal.

Requires the sender to be a member.

Transaction fees will be waived if the member is voting on any particular proposal
for the first time and the call is successful. Subsequent vote changes will charge a
fee.
\# &lt;weight&gt;
\#\# Weight
- `O(M)` where `M` is members-count (code- and governance-bounded)
- DB:
  - 1 storage read `Members` (codec `O(M)`)
  - 1 storage mutation `Voting` (codec `O(M)`)
- 1 event
\# &lt;/weight&gt;
#### Attributes
| Name | Type |
| -------- | -------- | 
| proposal | `T::Hash` | 
| index | `ProposalIndex` | 
| approve | `bool` | 

#### Python
```python
call = substrate.compose_call(
    'AdvisoryCommittee', 'vote', {
    'approve': 'bool',
    'index': 'u32',
    'proposal': 'scale_info::11',
}
)
```

---------
## Events

---------
### Approved
A motion was approved by the required threshold.
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| proposal_hash | `T::Hash` | ```scale_info::11```

---------
### Closed
A proposal was closed because its threshold was reached or after its duration was up.
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| proposal_hash | `T::Hash` | ```scale_info::11```
| yes | `MemberCount` | ```u32```
| no | `MemberCount` | ```u32```

---------
### Disapproved
A motion was not approved by the required threshold.
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| proposal_hash | `T::Hash` | ```scale_info::11```

---------
### Executed
A motion was executed; result will be `Ok` if it returned without error.
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| proposal_hash | `T::Hash` | ```scale_info::11```
| result | `DispatchResult` | ```{'Ok': (), 'Err': {'Other': None, 'CannotLookup': None, 'BadOrigin': None, 'Module': {'index': 'u8', 'error': '[u8; 4]'}, 'ConsumerRemaining': None, 'NoProviders': None, 'TooManyConsumers': None, 'Token': ('NoFunds', 'WouldDie', 'BelowMinimum', 'CannotCreate', 'UnknownAsset', 'Frozen', 'Unsupported'), 'Arithmetic': ('Underflow', 'Overflow', 'DivisionByZero'), 'Transactional': ('LimitReached', 'NoLayer'), 'Exhausted': None, 'Corruption': None, 'Unavailable': None}}```

---------
### MemberExecuted
A single member did some action; result will be `Ok` if it returned without error.
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| proposal_hash | `T::Hash` | ```scale_info::11```
| result | `DispatchResult` | ```{'Ok': (), 'Err': {'Other': None, 'CannotLookup': None, 'BadOrigin': None, 'Module': {'index': 'u8', 'error': '[u8; 4]'}, 'ConsumerRemaining': None, 'NoProviders': None, 'TooManyConsumers': None, 'Token': ('NoFunds', 'WouldDie', 'BelowMinimum', 'CannotCreate', 'UnknownAsset', 'Frozen', 'Unsupported'), 'Arithmetic': ('Underflow', 'Overflow', 'DivisionByZero'), 'Transactional': ('LimitReached', 'NoLayer'), 'Exhausted': None, 'Corruption': None, 'Unavailable': None}}```

---------
### Proposed
A motion (given hash) has been proposed (by given account) with a threshold (given
`MemberCount`).
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| account | `T::AccountId` | ```AccountId```
| proposal_index | `ProposalIndex` | ```u32```
| proposal_hash | `T::Hash` | ```scale_info::11```
| threshold | `MemberCount` | ```u32```

---------
### Voted
A motion (given hash) has been voted on by given account, leaving
a tally (yes votes and no votes given respectively as `MemberCount`).
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| account | `T::AccountId` | ```AccountId```
| proposal_hash | `T::Hash` | ```scale_info::11```
| voted | `bool` | ```bool```
| yes | `MemberCount` | ```u32```
| no | `MemberCount` | ```u32```

---------
## Storage functions

---------
### Members
 The current members of the collective. This is stored sorted (just by value).

#### Python
```python
result = substrate.query(
    'AdvisoryCommittee', 'Members', []
)
```

#### Return value
```python
['AccountId']
```
---------
### Prime
 The prime member that helps determine the default vote behavior in case of absentations.

#### Python
```python
result = substrate.query(
    'AdvisoryCommittee', 'Prime', []
)
```

#### Return value
```python
'AccountId'
```
---------
### ProposalCount
 Proposals so far.

#### Python
```python
result = substrate.query(
    'AdvisoryCommittee', 'ProposalCount', []
)
```

#### Return value
```python
'u32'
```
---------
### ProposalOf
 Actual proposal for a given hash, if it&#x27;s current.

#### Python
```python
result = substrate.query(
    'AdvisoryCommittee', 'ProposalOf', ['scale_info::11']
)
```

#### Return value
```python
'Call'
```
---------
### Proposals
 The hashes of the active proposals.

#### Python
```python
result = substrate.query(
    'AdvisoryCommittee', 'Proposals', []
)
```

#### Return value
```python
['scale_info::11']
```
---------
### Voting
 Votes on a given proposal, if it is ongoing.

#### Python
```python
result = substrate.query(
    'AdvisoryCommittee', 'Voting', ['scale_info::11']
)
```

#### Return value
```python
{'ayes': ['AccountId'], 'end': 'u64', 'index': 'u32', 'nays': ['AccountId'], 'threshold': 'u32'}
```
---------
## Errors

---------
### AlreadyInitialized
Members are already initialized!

---------
### DuplicateProposal
Duplicate proposals not allowed

---------
### DuplicateVote
Duplicate vote ignored

---------
### NotMember
Account is not a member

---------
### ProposalMissing
Proposal must exist

---------
### TooEarly
The close call was made too early, before the end of the voting.

---------
### TooManyProposals
There can only be a maximum of `MaxProposals` active proposals.

---------
### WrongIndex
Mismatched index

---------
### WrongProposalLength
The given length bound for the proposal was too low.

---------
### WrongProposalWeight
The given weight bound for the proposal was too low.

---------