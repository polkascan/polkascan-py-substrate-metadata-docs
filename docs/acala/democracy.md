
# Democracy

---------
## Calls

---------
### blacklist
#### Attributes
| Name | Type |
| -------- | -------- | 
| proposal_hash | `T::Hash` | 
| maybe_ref_index | `Option<ReferendumIndex>` | 

#### Python
```python
call = substrate.compose_call(
    'Democracy', 'blacklist', {
    'maybe_ref_index': (None, 'u32'),
    'proposal_hash': 'scale_info::12',
}
)
```

---------
### cancel_proposal
#### Attributes
| Name | Type |
| -------- | -------- | 
| prop_index | `PropIndex` | 

#### Python
```python
call = substrate.compose_call(
    'Democracy', 'cancel_proposal', {'prop_index': 'u32'}
)
```

---------
### cancel_referendum
#### Attributes
| Name | Type |
| -------- | -------- | 
| ref_index | `ReferendumIndex` | 

#### Python
```python
call = substrate.compose_call(
    'Democracy', 'cancel_referendum', {'ref_index': 'u32'}
)
```

---------
### clear_public_proposals
#### Attributes
No attributes

#### Python
```python
call = substrate.compose_call(
    'Democracy', 'clear_public_proposals', {}
)
```

---------
### delegate
#### Attributes
| Name | Type |
| -------- | -------- | 
| to | `AccountIdLookupOf<T>` | 
| conviction | `Conviction` | 
| balance | `BalanceOf<T>` | 

#### Python
```python
call = substrate.compose_call(
    'Democracy', 'delegate', {
    'balance': 'u128',
    'conviction': (
        'None',
        'Locked1x',
        'Locked2x',
        'Locked3x',
        'Locked4x',
        'Locked5x',
        'Locked6x',
    ),
    'to': {
        'Address20': '[u8; 20]',
        'Address32': '[u8; 32]',
        'Id': 'AccountId',
        'Index': 'u32',
        'Raw': 'Bytes',
    },
}
)
```

---------
### emergency_cancel
#### Attributes
| Name | Type |
| -------- | -------- | 
| ref_index | `ReferendumIndex` | 

#### Python
```python
call = substrate.compose_call(
    'Democracy', 'emergency_cancel', {'ref_index': 'u32'}
)
```

---------
### external_propose
#### Attributes
| Name | Type |
| -------- | -------- | 
| proposal | `BoundedCallOf<T>` | 

#### Python
```python
call = substrate.compose_call(
    'Democracy', 'external_propose', {
    'proposal': {
        'Inline': 'Bytes',
        'Legacy': {
            'hash': 'scale_info::12',
        },
        'Lookup': {
            'hash': 'scale_info::12',
            'len': 'u32',
        },
    },
}
)
```

---------
### external_propose_default
#### Attributes
| Name | Type |
| -------- | -------- | 
| proposal | `BoundedCallOf<T>` | 

#### Python
```python
call = substrate.compose_call(
    'Democracy', 'external_propose_default', {
    'proposal': {
        'Inline': 'Bytes',
        'Legacy': {
            'hash': 'scale_info::12',
        },
        'Lookup': {
            'hash': 'scale_info::12',
            'len': 'u32',
        },
    },
}
)
```

---------
### external_propose_majority
#### Attributes
| Name | Type |
| -------- | -------- | 
| proposal | `BoundedCallOf<T>` | 

#### Python
```python
call = substrate.compose_call(
    'Democracy', 'external_propose_majority', {
    'proposal': {
        'Inline': 'Bytes',
        'Legacy': {
            'hash': 'scale_info::12',
        },
        'Lookup': {
            'hash': 'scale_info::12',
            'len': 'u32',
        },
    },
}
)
```

---------
### fast_track
#### Attributes
| Name | Type |
| -------- | -------- | 
| proposal_hash | `T::Hash` | 
| voting_period | `BlockNumberFor<T>` | 
| delay | `BlockNumberFor<T>` | 

#### Python
```python
call = substrate.compose_call(
    'Democracy', 'fast_track', {
    'delay': 'u32',
    'proposal_hash': 'scale_info::12',
    'voting_period': 'u32',
}
)
```

---------
### propose
#### Attributes
| Name | Type |
| -------- | -------- | 
| proposal | `BoundedCallOf<T>` | 
| value | `BalanceOf<T>` | 

#### Python
```python
call = substrate.compose_call(
    'Democracy', 'propose', {
    'proposal': {
        'Inline': 'Bytes',
        'Legacy': {
            'hash': 'scale_info::12',
        },
        'Lookup': {
            'hash': 'scale_info::12',
            'len': 'u32',
        },
    },
    'value': 'u128',
}
)
```

---------
### remove_other_vote
#### Attributes
| Name | Type |
| -------- | -------- | 
| target | `AccountIdLookupOf<T>` | 
| index | `ReferendumIndex` | 

#### Python
```python
call = substrate.compose_call(
    'Democracy', 'remove_other_vote', {
    'index': 'u32',
    'target': {
        'Address20': '[u8; 20]',
        'Address32': '[u8; 32]',
        'Id': 'AccountId',
        'Index': 'u32',
        'Raw': 'Bytes',
    },
}
)
```

---------
### remove_vote
#### Attributes
| Name | Type |
| -------- | -------- | 
| index | `ReferendumIndex` | 

#### Python
```python
call = substrate.compose_call(
    'Democracy', 'remove_vote', {'index': 'u32'}
)
```

---------
### second
#### Attributes
| Name | Type |
| -------- | -------- | 
| proposal | `PropIndex` | 

#### Python
```python
call = substrate.compose_call(
    'Democracy', 'second', {'proposal': 'u32'}
)
```

---------
### set_metadata
#### Attributes
| Name | Type |
| -------- | -------- | 
| owner | `MetadataOwner` | 
| maybe_hash | `Option<T::Hash>` | 

#### Python
```python
call = substrate.compose_call(
    'Democracy', 'set_metadata', {
    'maybe_hash': (
        None,
        'scale_info::12',
    ),
    'owner': {
        'External': None,
        'Proposal': 'u32',
        'Referendum': 'u32',
    },
}
)
```

---------
### undelegate
#### Attributes
No attributes

#### Python
```python
call = substrate.compose_call(
    'Democracy', 'undelegate', {}
)
```

---------
### unlock
#### Attributes
| Name | Type |
| -------- | -------- | 
| target | `AccountIdLookupOf<T>` | 

#### Python
```python
call = substrate.compose_call(
    'Democracy', 'unlock', {
    'target': {
        'Address20': '[u8; 20]',
        'Address32': '[u8; 32]',
        'Id': 'AccountId',
        'Index': 'u32',
        'Raw': 'Bytes',
    },
}
)
```

---------
### veto_external
#### Attributes
| Name | Type |
| -------- | -------- | 
| proposal_hash | `T::Hash` | 

#### Python
```python
call = substrate.compose_call(
    'Democracy', 'veto_external', {'proposal_hash': 'scale_info::12'}
)
```

---------
### vote
#### Attributes
| Name | Type |
| -------- | -------- | 
| ref_index | `ReferendumIndex` | 
| vote | `AccountVote<BalanceOf<T>>` | 

#### Python
```python
call = substrate.compose_call(
    'Democracy', 'vote', {
    'ref_index': 'u32',
    'vote': {
        'Split': {
            'aye': 'u128',
            'nay': 'u128',
        },
        'Standard': {
            'balance': 'u128',
            'vote': {
                'aye': 'bool',
                'conviction': (
                    'None',
                    'Locked1x',
                    'Locked2x',
                    'Locked3x',
                    'Locked4x',
                    'Locked5x',
                    'Locked6x',
                ),
            },
        },
    },
}
)
```

---------
## Events

---------
### Blacklisted
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| proposal_hash | `T::Hash` | ```scale_info::12```

---------
### Cancelled
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| ref_index | `ReferendumIndex` | ```u32```

---------
### Delegated
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| who | `T::AccountId` | ```AccountId```
| target | `T::AccountId` | ```AccountId```

---------
### ExternalTabled
#### Attributes
No attributes

---------
### MetadataCleared
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| owner | `MetadataOwner` | ```{'External': None, 'Proposal': 'u32', 'Referendum': 'u32'}```
| hash | `T::Hash` | ```scale_info::12```

---------
### MetadataSet
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| owner | `MetadataOwner` | ```{'External': None, 'Proposal': 'u32', 'Referendum': 'u32'}```
| hash | `T::Hash` | ```scale_info::12```

---------
### MetadataTransferred
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| prev_owner | `MetadataOwner` | ```{'External': None, 'Proposal': 'u32', 'Referendum': 'u32'}```
| owner | `MetadataOwner` | ```{'External': None, 'Proposal': 'u32', 'Referendum': 'u32'}```
| hash | `T::Hash` | ```scale_info::12```

---------
### NotPassed
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| ref_index | `ReferendumIndex` | ```u32```

---------
### Passed
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| ref_index | `ReferendumIndex` | ```u32```

---------
### ProposalCanceled
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| prop_index | `PropIndex` | ```u32```

---------
### Proposed
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| proposal_index | `PropIndex` | ```u32```
| deposit | `BalanceOf<T>` | ```u128```

---------
### Seconded
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| seconder | `T::AccountId` | ```AccountId```
| prop_index | `PropIndex` | ```u32```

---------
### Started
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| ref_index | `ReferendumIndex` | ```u32```
| threshold | `VoteThreshold` | ```('SuperMajorityApprove', 'SuperMajorityAgainst', 'SimpleMajority')```

---------
### Tabled
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| proposal_index | `PropIndex` | ```u32```
| deposit | `BalanceOf<T>` | ```u128```

---------
### Undelegated
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| account | `T::AccountId` | ```AccountId```

---------
### Vetoed
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| who | `T::AccountId` | ```AccountId```
| proposal_hash | `T::Hash` | ```scale_info::12```
| until | `BlockNumberFor<T>` | ```u32```

---------
### Voted
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| voter | `T::AccountId` | ```AccountId```
| ref_index | `ReferendumIndex` | ```u32```
| vote | `AccountVote<BalanceOf<T>>` | ```{'Standard': {'vote': {'aye': 'bool', 'conviction': ('None', 'Locked1x', 'Locked2x', 'Locked3x', 'Locked4x', 'Locked5x', 'Locked6x')}, 'balance': 'u128'}, 'Split': {'aye': 'u128', 'nay': 'u128'}}```

---------
## Storage functions

---------
### Blacklist

#### Python
```python
result = substrate.query(
    'Democracy', 'Blacklist', ['scale_info::12']
)
```

#### Return value
```python
('u32', ['AccountId'])
```
---------
### Cancellations

#### Python
```python
result = substrate.query(
    'Democracy', 'Cancellations', ['scale_info::12']
)
```

#### Return value
```python
'bool'
```
---------
### DepositOf

#### Python
```python
result = substrate.query(
    'Democracy', 'DepositOf', ['u32']
)
```

#### Return value
```python
(['AccountId'], 'u128')
```
---------
### LastTabledWasExternal

#### Python
```python
result = substrate.query(
    'Democracy', 'LastTabledWasExternal', []
)
```

#### Return value
```python
'bool'
```
---------
### LowestUnbaked

#### Python
```python
result = substrate.query(
    'Democracy', 'LowestUnbaked', []
)
```

#### Return value
```python
'u32'
```
---------
### MetadataOf

#### Python
```python
result = substrate.query(
    'Democracy', 'MetadataOf', [
    {
        'External': None,
        'Proposal': 'u32',
        'Referendum': 'u32',
    },
]
)
```

#### Return value
```python
'scale_info::12'
```
---------
### NextExternal

#### Python
```python
result = substrate.query(
    'Democracy', 'NextExternal', []
)
```

#### Return value
```python
(
    {
        'Inline': 'Bytes',
        'Legacy': {'hash': 'scale_info::12'},
        'Lookup': {'hash': 'scale_info::12', 'len': 'u32'},
    },
    ('SuperMajorityApprove', 'SuperMajorityAgainst', 'SimpleMajority'),
)
```
---------
### PublicPropCount

#### Python
```python
result = substrate.query(
    'Democracy', 'PublicPropCount', []
)
```

#### Return value
```python
'u32'
```
---------
### PublicProps

#### Python
```python
result = substrate.query(
    'Democracy', 'PublicProps', []
)
```

#### Return value
```python
[
    (
        'u32',
        {
            'Inline': 'Bytes',
            'Legacy': {'hash': 'scale_info::12'},
            'Lookup': {'hash': 'scale_info::12', 'len': 'u32'},
        },
        'AccountId',
    ),
]
```
---------
### ReferendumCount

#### Python
```python
result = substrate.query(
    'Democracy', 'ReferendumCount', []
)
```

#### Return value
```python
'u32'
```
---------
### ReferendumInfoOf

#### Python
```python
result = substrate.query(
    'Democracy', 'ReferendumInfoOf', ['u32']
)
```

#### Return value
```python
{
    'Finished': {'approved': 'bool', 'end': 'u32'},
    'Ongoing': {
        'delay': 'u32',
        'end': 'u32',
        'proposal': {
            'Inline': 'Bytes',
            'Legacy': {'hash': 'scale_info::12'},
            'Lookup': {'hash': 'scale_info::12', 'len': 'u32'},
        },
        'tally': {'ayes': 'u128', 'nays': 'u128', 'turnout': 'u128'},
        'threshold': (
            'SuperMajorityApprove',
            'SuperMajorityAgainst',
            'SimpleMajority',
        ),
    },
}
```
---------
### VotingOf

#### Python
```python
result = substrate.query(
    'Democracy', 'VotingOf', ['AccountId']
)
```

#### Return value
```python
{
    'Delegating': {
        'balance': 'u128',
        'conviction': (
            'None',
            'Locked1x',
            'Locked2x',
            'Locked3x',
            'Locked4x',
            'Locked5x',
            'Locked6x',
        ),
        'delegations': {'capital': 'u128', 'votes': 'u128'},
        'prior': ('u32', 'u128'),
        'target': 'AccountId',
    },
    'Direct': {
        'delegations': {'capital': 'u128', 'votes': 'u128'},
        'prior': ('u32', 'u128'),
        'votes': [('u32', 'scale_info::155')],
    },
}
```
---------
## Constants

---------
### CooloffPeriod
#### Value
```python
50400
```
#### Python
```python
constant = substrate.get_constant('Democracy', 'CooloffPeriod')
```
---------
### EnactmentPeriod
#### Value
```python
14400
```
#### Python
```python
constant = substrate.get_constant('Democracy', 'EnactmentPeriod')
```
---------
### FastTrackVotingPeriod
#### Value
```python
900
```
#### Python
```python
constant = substrate.get_constant('Democracy', 'FastTrackVotingPeriod')
```
---------
### InstantAllowed
#### Value
```python
True
```
#### Python
```python
constant = substrate.get_constant('Democracy', 'InstantAllowed')
```
---------
### LaunchPeriod
#### Value
```python
36000
```
#### Python
```python
constant = substrate.get_constant('Democracy', 'LaunchPeriod')
```
---------
### MaxBlacklisted
#### Value
```python
100
```
#### Python
```python
constant = substrate.get_constant('Democracy', 'MaxBlacklisted')
```
---------
### MaxDeposits
#### Value
```python
100
```
#### Python
```python
constant = substrate.get_constant('Democracy', 'MaxDeposits')
```
---------
### MaxProposals
#### Value
```python
100
```
#### Python
```python
constant = substrate.get_constant('Democracy', 'MaxProposals')
```
---------
### MaxVotes
#### Value
```python
100
```
#### Python
```python
constant = substrate.get_constant('Democracy', 'MaxVotes')
```
---------
### MinimumDeposit
#### Value
```python
1000000000000000
```
#### Python
```python
constant = substrate.get_constant('Democracy', 'MinimumDeposit')
```
---------
### VoteLockingPeriod
#### Value
```python
100800
```
#### Python
```python
constant = substrate.get_constant('Democracy', 'VoteLockingPeriod')
```
---------
### VotingPeriod
#### Value
```python
36000
```
#### Python
```python
constant = substrate.get_constant('Democracy', 'VotingPeriod')
```
---------
## Errors

---------
### AlreadyCanceled

---------
### AlreadyDelegating

---------
### AlreadyVetoed

---------
### DuplicateProposal

---------
### InstantNotAllowed

---------
### InsufficientFunds

---------
### InvalidHash

---------
### MaxVotesReached

---------
### NoPermission

---------
### NoProposal

---------
### NoneWaiting

---------
### Nonsense

---------
### NotDelegating

---------
### NotSimpleMajority

---------
### NotVoter

---------
### PreimageNotExist

---------
### ProposalBlacklisted

---------
### ProposalMissing

---------
### ReferendumInvalid

---------
### TooMany

---------
### ValueLow

---------
### VotesExist

---------
### VotingPeriodLow

---------
### WrongUpperBound

---------