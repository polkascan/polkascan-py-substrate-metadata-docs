
# System

---------
## Calls

---------
### kill_prefix
See [`Pallet::kill_prefix`].
#### Attributes
| Name | Type |
| -------- | -------- | 
| prefix | `Key` | 
| subkeys | `u32` | 

#### Python
```python
call = substrate.compose_call(
    'System', 'kill_prefix', {'prefix': 'Bytes', 'subkeys': 'u32'}
)
```

---------
### kill_storage
See [`Pallet::kill_storage`].
#### Attributes
| Name | Type |
| -------- | -------- | 
| keys | `Vec<Key>` | 

#### Python
```python
call = substrate.compose_call(
    'System', 'kill_storage', {'keys': ['Bytes']}
)
```

---------
### remark
See [`Pallet::remark`].
#### Attributes
| Name | Type |
| -------- | -------- | 
| remark | `Vec<u8>` | 

#### Python
```python
call = substrate.compose_call(
    'System', 'remark', {'remark': 'Bytes'}
)
```

---------
### remark_with_event
See [`Pallet::remark_with_event`].
#### Attributes
| Name | Type |
| -------- | -------- | 
| remark | `Vec<u8>` | 

#### Python
```python
call = substrate.compose_call(
    'System', 'remark_with_event', {'remark': 'Bytes'}
)
```

---------
### set_code
See [`Pallet::set_code`].
#### Attributes
| Name | Type |
| -------- | -------- | 
| code | `Vec<u8>` | 

#### Python
```python
call = substrate.compose_call(
    'System', 'set_code', {'code': 'Bytes'}
)
```

---------
### set_code_without_checks
See [`Pallet::set_code_without_checks`].
#### Attributes
| Name | Type |
| -------- | -------- | 
| code | `Vec<u8>` | 

#### Python
```python
call = substrate.compose_call(
    'System', 'set_code_without_checks', {'code': 'Bytes'}
)
```

---------
### set_heap_pages
See [`Pallet::set_heap_pages`].
#### Attributes
| Name | Type |
| -------- | -------- | 
| pages | `u64` | 

#### Python
```python
call = substrate.compose_call(
    'System', 'set_heap_pages', {'pages': 'u64'}
)
```

---------
### set_storage
See [`Pallet::set_storage`].
#### Attributes
| Name | Type |
| -------- | -------- | 
| items | `Vec<KeyValue>` | 

#### Python
```python
call = substrate.compose_call(
    'System', 'set_storage', {'items': [('Bytes', 'Bytes')]}
)
```

---------
## Events

---------
### CodeUpdated
`:code` was updated.
#### Attributes
No attributes

---------
### ExtrinsicFailed
An extrinsic failed.
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| dispatch_error | `DispatchError` | ```{'Other': None, 'CannotLookup': None, 'BadOrigin': None, 'Module': {'index': 'u8', 'error': '[u8; 4]'}, 'ConsumerRemaining': None, 'NoProviders': None, 'TooManyConsumers': None, 'Token': ('FundsUnavailable', 'OnlyProvider', 'BelowMinimum', 'CannotCreate', 'UnknownAsset', 'Frozen', 'Unsupported', 'CannotCreateHold', 'NotExpendable', 'Blocked'), 'Arithmetic': ('Underflow', 'Overflow', 'DivisionByZero'), 'Transactional': ('LimitReached', 'NoLayer'), 'Exhausted': None, 'Corruption': None, 'Unavailable': None, 'RootNotAllowed': None}```
| dispatch_info | `DispatchInfo` | ```{'weight': {'ref_time': 'u64', 'proof_size': 'u64'}, 'class': ('Normal', 'Operational', 'Mandatory'), 'pays_fee': ('Yes', 'No')}```

---------
### ExtrinsicSuccess
An extrinsic completed successfully.
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| dispatch_info | `DispatchInfo` | ```{'weight': {'ref_time': 'u64', 'proof_size': 'u64'}, 'class': ('Normal', 'Operational', 'Mandatory'), 'pays_fee': ('Yes', 'No')}```

---------
### KilledAccount
An account was reaped.
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| account | `T::AccountId` | ```AccountId```

---------
### NewAccount
A new account was created.
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| account | `T::AccountId` | ```AccountId```

---------
### Remarked
On on-chain remark happened.
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| sender | `T::AccountId` | ```AccountId```
| hash | `T::Hash` | ```scale_info::12```

---------
## Storage functions

---------
### Account
 The full account information for a particular account ID.

#### Python
```python
result = substrate.query(
    'System', 'Account', ['AccountId']
)
```

#### Return value
```python
{
    'consumers': 'u32',
    'data': {
        'flags': 'u128',
        'free': 'u128',
        'frozen': 'u128',
        'reserved': 'u128',
    },
    'nonce': 'u32',
    'providers': 'u32',
    'sufficients': 'u32',
}
```
---------
### AllExtrinsicsLen
 Total length (in bytes) for all extrinsics put together, for the current block.

#### Python
```python
result = substrate.query(
    'System', 'AllExtrinsicsLen', []
)
```

#### Return value
```python
'u32'
```
---------
### BlockHash
 Map of block numbers to block hashes.

#### Python
```python
result = substrate.query(
    'System', 'BlockHash', ['u32']
)
```

#### Return value
```python
'scale_info::12'
```
---------
### BlockWeight
 The current weight for the block.

#### Python
```python
result = substrate.query(
    'System', 'BlockWeight', []
)
```

#### Return value
```python
{
    'mandatory': {'proof_size': 'u64', 'ref_time': 'u64'},
    'normal': {'proof_size': 'u64', 'ref_time': 'u64'},
    'operational': {'proof_size': 'u64', 'ref_time': 'u64'},
}
```
---------
### Digest
 Digest of the current block, also part of the block header.

#### Python
```python
result = substrate.query(
    'System', 'Digest', []
)
```

#### Return value
```python
{
    'logs': [
        {
            'Other': 'Bytes',
            None: None,
            'Consensus': ('[u8; 4]', 'Bytes'),
            'PreRuntime': ('[u8; 4]', 'Bytes'),
            'RuntimeEnvironmentUpdated': None,
            'Seal': ('[u8; 4]', 'Bytes'),
        },
    ],
}
```
---------
### EventCount
 The number of events in the `Events&lt;T&gt;` list.

#### Python
```python
result = substrate.query(
    'System', 'EventCount', []
)
```

#### Return value
```python
'u32'
```
---------
### EventTopics
 Mapping between a topic (represented by T::Hash) and a vector of indexes
 of events in the `&lt;Events&lt;T&gt;&gt;` list.

 All topic vectors have deterministic storage locations depending on the topic. This
 allows light-clients to leverage the changes trie storage tracking mechanism and
 in case of changes fetch the list of events of interest.

 The value has the type `(BlockNumberFor&lt;T&gt;, EventIndex)` because if we used only just
 the `EventIndex` then in case if the topic has the same contents on the next block
 no notification will be triggered thus the event might be lost.

#### Python
```python
result = substrate.query(
    'System', 'EventTopics', ['scale_info::12']
)
```

#### Return value
```python
[('u32', 'u32')]
```
---------
### Events
 Events deposited for the current block.

 NOTE: The item is unbound and should therefore never be read on chain.
 It could otherwise inflate the PoV size of a block.

 Events have a large in-memory size. Box the events to not go out-of-memory
 just in case someone still reads them from within the runtime.

#### Python
```python
result = substrate.query(
    'System', 'Events', []
)
```

#### Return value
```python
[
    {
        'event': {
            'Multisig': {
                'MultisigApproval': {
                    'approving': 'AccountId',
                    'call_hash': '[u8; 32]',
                    'multisig': 'AccountId',
                    'timepoint': 'scale_info::34',
                },
                'MultisigCancelled': {
                    'call_hash': '[u8; 32]',
                    'cancelling': 'AccountId',
                    'multisig': 'AccountId',
                    'timepoint': 'scale_info::34',
                },
                'MultisigExecuted': {
                    'approving': 'AccountId',
                    'call_hash': '[u8; 32]',
                    'multisig': 'AccountId',
                    'result': 'scale_info::31',
                    'timepoint': 'scale_info::34',
                },
                'NewMultisig': {
                    'approving': 'AccountId',
                    'call_hash': '[u8; 32]',
                    'multisig': 'AccountId',
                },
            },
            None: None,
            'Assets': {
                'AccountsDestroyed': {
                    'accounts_destroyed': 'u32',
                    'accounts_remaining': 'u32',
                    'asset_id': 'u32',
                },
                'ApprovalCancelled': {
                    'asset_id': 'u32',
                    'delegate': 'AccountId',
                    'owner': 'AccountId',
                },
                'ApprovalsDestroyed': {
                    'approvals_destroyed': 'u32',
                    'approvals_remaining': 'u32',
                    'asset_id': 'u32',
                },
                'ApprovedTransfer': {
                    'amount': 'u128',
                    'asset_id': 'u32',
                    'delegate': 'AccountId',
                    'source': 'AccountId',
                },
                'AssetFrozen': {'asset_id': 'u32'},
                'AssetMinBalanceChanged': {
                    'asset_id': 'u32',
                    'new_min_balance': 'u128',
                },
                'AssetStatusChanged': {'asset_id': 'u32'},
                'AssetThawed': {'asset_id': 'u32'},
                'Blocked': {'asset_id': 'u32', 'who': 'AccountId'},
                'Burned': {
                    'asset_id': 'u32',
                    'balance': 'u128',
                    'owner': 'AccountId',
                },
                'Created': {
                    'asset_id': 'u32',
                    'creator': 'AccountId',
                    'owner': 'AccountId',
                },
                'Destroyed': {'asset_id': 'u32'},
                'DestructionStarted': {'asset_id': 'u32'},
                'ForceCreated': {'asset_id': 'u32', 'owner': 'AccountId'},
                'Frozen': {'asset_id': 'u32', 'who': 'AccountId'},
                'Issued': {
                    'amount': 'u128',
                    'asset_id': 'u32',
                    'owner': 'AccountId',
                },
                'MetadataCleared': {'asset_id': 'u32'},
                'MetadataSet': {
                    'asset_id': 'u32',
                    'decimals': 'u8',
                    'is_frozen': 'bool',
                    'name': 'Bytes',
                    'symbol': 'Bytes',
                },
                'OwnerChanged': {'asset_id': 'u32', 'owner': 'AccountId'},
                'TeamChanged': {
                    'admin': 'AccountId',
                    'asset_id': 'u32',
                    'freezer': 'AccountId',
                    'issuer': 'AccountId',
                },
                'Thawed': {'asset_id': 'u32', 'who': 'AccountId'},
                'Touched': {
                    'asset_id': 'u32',
                    'depositor': 'AccountId',
                    'who': 'AccountId',
                },
                'Transferred': {
                    'amount': 'u128',
                    'asset_id': 'u32',
                    'from': 'AccountId',
                    'to': 'AccountId',
                },
                'TransferredApproved': {
                    'amount': 'u128',
                    'asset_id': 'u32',
                    'delegate': 'AccountId',
                    'destination': 'AccountId',
                    'owner': 'AccountId',
                },
            },
            'AssetsRegistry': {
                'AssetRegistered': {
                    'asset_id': 'u32',
                    'location': 'scale_info::51',
                },
                'AssetUnregistered': {
                    'asset_id': 'u32',
                    'location': 'scale_info::51',
                },
                'ChainbridgeDisabled': {
                    'asset_id': 'u32',
                    'chain_id': 'u8',
                    'resource_id': '[u8; 32]',
                },
                'ChainbridgeEnabled': {
                    'asset_id': 'u32',
                    'chain_id': 'u8',
                    'resource_id': '[u8; 32]',
                },
                'ForceBurnt': {
                    'amount': 'u128',
                    'asset_id': 'u32',
                    'who': 'AccountId',
                },
                'ForceMinted': {
                    'amount': 'u128',
                    'asset_id': 'u32',
                    'beneficiary': 'AccountId',
                },
                'SygmabridgeDisabled': {
                    'asset_id': 'u32',
                    'domain_id': 'u8',
                    'resource_id': '[u8; 32]',
                },
                'SygmabridgeEnabled': {
                    'asset_id': 'u32',
                    'domain_id': 'u8',
                    'resource_id': '[u8; 32]',
                },
            },
            'Balances': {
                'BalanceSet': {'free': 'u128', 'who': 'AccountId'},
                'Burned': {'amount': 'u128', 'who': 'AccountId'},
                'Deposit': {'amount': 'u128', 'who': 'AccountId'},
                'DustLost': {'account': 'AccountId', 'amount': 'u128'},
                'Endowed': {'account': 'AccountId', 'free_balance': 'u128'},
                'Frozen': {'amount': 'u128', 'who': 'AccountId'},
                'Issued': {'amount': 'u128'},
                'Locked': {'amount': 'u128', 'who': 'AccountId'},
                'Minted': {'amount': 'u128', 'who': 'AccountId'},
                'Rescinded': {'amount': 'u128'},
                'ReserveRepatriated': {
                    'amount': 'u128',
                    'destination_status': 'scale_info::106',
                    'from': 'AccountId',
                    'to': 'AccountId',
                },
                'Reserved': {'amount': 'u128', 'who': 'AccountId'},
                'Restored': {'amount': 'u128', 'who': 'AccountId'},
                'Slashed': {'amount': 'u128', 'who': 'AccountId'},
                'Suspended': {'amount': 'u128', 'who': 'AccountId'},
                'Thawed': {'amount': 'u128', 'who': 'AccountId'},
                'Transfer': {
                    'amount': 'u128',
                    'from': 'AccountId',
                    'to': 'AccountId',
                },
                'Unlocked': {'amount': 'u128', 'who': 'AccountId'},
                'Unreserved': {'amount': 'u128', 'who': 'AccountId'},
                'Upgraded': {'who': 'AccountId'},
                'Withdraw': {'amount': 'u128', 'who': 'AccountId'},
            },
            'Bounties': {
                'BountyAwarded': {'beneficiary': 'AccountId', 'index': 'u32'},
                'BountyBecameActive': {'index': 'u32'},
                'BountyCanceled': {'index': 'u32'},
                'BountyClaimed': {
                    'beneficiary': 'AccountId',
                    'index': 'u32',
                    'payout': 'u128',
                },
                'BountyExtended': {'index': 'u32'},
                'BountyProposed': {'index': 'u32'},
                'BountyRejected': {'bond': 'u128', 'index': 'u32'},
            },
            'ChainBridge': {
                'ChainWhitelisted': 'u8',
                'FeeUpdated': {'dest_id': 'u8', 'fee': 'u128'},
                'FungibleTransfer': (
                    'u8',
                    'u64',
                    '[u8; 32]',
                    'scale_info::131',
                    'Bytes',
                ),
                'GenericTransfer': ('u8', 'u64', '[u8; 32]', 'Bytes'),
                'NonFungibleTransfer': (
                    'u8',
                    'u64',
                    '[u8; 32]',
                    'Bytes',
                    'Bytes',
                    'Bytes',
                ),
                'ProposalApproved': ('u8', 'u64'),
                'ProposalFailed': ('u8', 'u64'),
                'ProposalRejected': ('u8', 'u64'),
                'ProposalSucceeded': ('u8', 'u64'),
                'RelayerAdded': 'AccountId',
                'RelayerRemoved': 'AccountId',
                'RelayerThresholdChanged': 'u32',
                'VoteAgainst': ('u8', 'u64', 'AccountId'),
                'VoteFor': ('u8', 'u64', 'AccountId'),
            },
            'ChildBounties': {
                'Added': {'child_index': 'u32', 'index': 'u32'},
                'Awarded': {
                    'beneficiary': 'AccountId',
                    'child_index': 'u32',
                    'index': 'u32',
                },
                'Canceled': {'child_index': 'u32', 'index': 'u32'},
                'Claimed': {
                    'beneficiary': 'AccountId',
                    'child_index': 'u32',
                    'index': 'u32',
                    'payout': 'u128',
                },
            },
            'CollatorSelection': {
                'CandidateAdded': {
                    'account_id': 'AccountId',
                    'deposit': 'u128',
                },
                'CandidateRemoved': {'account_id': 'AccountId'},
                'InvalidInvulnerableSkipped': {'account_id': 'AccountId'},
                'InvulnerableAdded': {'account_id': 'AccountId'},
                'InvulnerableRemoved': {'account_id': 'AccountId'},
                'NewCandidacyBond': {'bond_amount': 'u128'},
                'NewDesiredCandidates': {'desired_candidates': 'u32'},
                'NewInvulnerables': {'invulnerables': ['AccountId']},
            },
            'Council': {
                'Approved': {'proposal_hash': 'scale_info::12'},
                'Closed': {
                    'no': 'u32',
                    'proposal_hash': 'scale_info::12',
                    'yes': 'u32',
                },
                'Disapproved': {'proposal_hash': 'scale_info::12'},
                'Executed': {
                    'proposal_hash': 'scale_info::12',
                    'result': 'scale_info::31',
                },
                'MemberExecuted': {
                    'proposal_hash': 'scale_info::12',
                    'result': 'scale_info::31',
                },
                'Proposed': {
                    'account': 'AccountId',
                    'proposal_hash': 'scale_info::12',
                    'proposal_index': 'u32',
                    'threshold': 'u32',
                },
                'Voted': {
                    'account': 'AccountId',
                    'no': 'u32',
                    'proposal_hash': 'scale_info::12',
                    'voted': 'bool',
                    'yes': 'u32',
                },
            },
            'CumulusXcm': {
                'ExecutedDownward': ('[u8; 32]', 'scale_info::48'),
                'InvalidFormat': '[u8; 32]',
                'UnsupportedVersion': '[u8; 32]',
            },
            'Democracy': {
                'Blacklisted': {'proposal_hash': 'scale_info::12'},
                'Cancelled': {'ref_index': 'u32'},
                'Delegated': {'target': 'AccountId', 'who': 'AccountId'},
                'ExternalTabled': None,
                'MetadataCleared': {
                    'hash': 'scale_info::12',
                    'owner': 'scale_info::117',
                },
                'MetadataSet': {
                    'hash': 'scale_info::12',
                    'owner': 'scale_info::117',
                },
                'MetadataTransferred': {
                    'hash': 'scale_info::12',
                    'owner': 'scale_info::117',
                    'prev_owner': 'scale_info::117',
                },
                'NotPassed': {'ref_index': 'u32'},
                'Passed': {'ref_index': 'u32'},
                'ProposalCanceled': {'prop_index': 'u32'},
                'Proposed': {'deposit': 'u128', 'proposal_index': 'u32'},
                'Seconded': {'prop_index': 'u32', 'seconder': 'AccountId'},
                'Started': {
                    'ref_index': 'u32',
                    'threshold': 'scale_info::114',
                },
                'Tabled': {'deposit': 'u128', 'proposal_index': 'u32'},
                'Undelegated': {'account': 'AccountId'},
                'Vetoed': {
                    'proposal_hash': 'scale_info::12',
                    'until': 'u32',
                    'who': 'AccountId',
                },
                'Voted': {
                    'ref_index': 'u32',
                    'vote': 'scale_info::115',
                    'voter': 'AccountId',
                },
            },
            'DmpQueue': {
                'ExecutedDownward': {
                    'message_hash': '[u8; 32]',
                    'message_id': '[u8; 32]',
                    'outcome': 'scale_info::48',
                },
                'InvalidFormat': {'message_hash': '[u8; 32]'},
                'MaxMessagesExhausted': {'message_hash': '[u8; 32]'},
                'OverweightEnqueued': {
                    'message_hash': '[u8; 32]',
                    'message_id': '[u8; 32]',
                    'overweight_index': 'u64',
                    'required_weight': 'scale_info::9',
                },
                'OverweightServiced': {
                    'overweight_index': 'u64',
                    'weight_used': 'scale_info::9',
                },
                'UnsupportedVersion': {'message_hash': '[u8; 32]'},
                'WeightExhausted': {
                    'message_hash': '[u8; 32]',
                    'message_id': '[u8; 32]',
                    'remaining_weight': 'scale_info::9',
                    'required_weight': 'scale_info::9',
                },
            },
            'Identity': {
                'IdentityCleared': {'deposit': 'u128', 'who': 'AccountId'},
                'IdentityKilled': {'deposit': 'u128', 'who': 'AccountId'},
                'IdentitySet': {'who': 'AccountId'},
                'JudgementGiven': {
                    'registrar_index': 'u32',
                    'target': 'AccountId',
                },
                'JudgementRequested': {
                    'registrar_index': 'u32',
                    'who': 'AccountId',
                },
                'JudgementUnrequested': {
                    'registrar_index': 'u32',
                    'who': 'AccountId',
                },
                'RegistrarAdded': {'registrar_index': 'u32'},
                'SubIdentityAdded': {
                    'deposit': 'u128',
                    'main': 'AccountId',
                    'sub': 'AccountId',
                },
                'SubIdentityRemoved': {
                    'deposit': 'u128',
                    'main': 'AccountId',
                    'sub': 'AccountId',
                },
                'SubIdentityRevoked': {
                    'deposit': 'u128',
                    'main': 'AccountId',
                    'sub': 'AccountId',
                },
            },
            'Lottery': {
                'CallsUpdated': None,
                'LotteryStarted': None,
                'TicketBought': {'call_index': ('u8', 'u8'), 'who': 'AccountId'},
                'Winner': {'lottery_balance': 'u128', 'winner': 'AccountId'},
            },
            'PalletIndex': {
                'Claimed': {'fee': 'u128', 'tasks': ['[u8; 32]']},
                'NewTask': {'deposit_info': 'scale_info::172'},
                'WorkerAdd': {'worker': 'AccountId'},
                'WorkerRemove': {'worker': 'AccountId'},
            },
            'ParachainSystem': {
                'DownwardMessagesProcessed': {
                    'dmq_head': 'scale_info::12',
                    'weight_used': 'scale_info::9',
                },
                'DownwardMessagesReceived': {'count': 'u32'},
                'UpgradeAuthorized': {'code_hash': 'scale_info::12'},
                'UpwardMessageSent': {'message_hash': (None, '[u8; 32]')},
                'ValidationFunctionApplied': {'relay_chain_block_num': 'u32'},
                'ValidationFunctionDiscarded': None,
                'ValidationFunctionStored': None,
            },
            'PhalaBasePool': {
                'NftCreated': {
                    'cid': 'u32',
                    'nft_id': 'u32',
                    'owner': 'AccountId',
                    'pid': 'u64',
                    'shares': 'u128',
                },
                'PoolWhitelistCreated': {'pid': 'u64'},
                'PoolWhitelistDeleted': {'pid': 'u64'},
                'PoolWhitelistStakerAdded': {
                    'pid': 'u64',
                    'staker': 'AccountId',
                },
                'PoolWhitelistStakerRemoved': {
                    'pid': 'u64',
                    'staker': 'AccountId',
                },
                'Withdrawal': {
                    'amount': 'u128',
                    'burnt_shares': 'u128',
                    'pid': 'u64',
                    'shares': 'u128',
                    'user': 'AccountId',
                },
                'WithdrawalQueued': {
                    'as_vault': (None, 'u64'),
                    'nft_id': 'u32',
                    'pid': 'u64',
                    'shares': 'u128',
                    'user': 'AccountId',
                    'withdrawing_nft_id': 'u32',
                },
            },
            'PhalaComputation': {
                'BenchmarkUpdated': {
                    'p_instant': 'u32',
                    'session': 'AccountId',
                },
                'BudgetUpdated': {'budget': 'u128', 'nonce': 'u64'},
                'CoolDownExpirationChanged': {'period': 'u64'},
                'InternalErrorWorkerSettleFailed': {'worker': '[u8; 32]'},
                'InternalErrorWrongHalvingConfigured': None,
                'SessionBound': {'session': 'AccountId', 'worker': '[u8; 32]'},
                'SessionSettled': {
                    'payout_bits': 'u128',
                    'session': 'AccountId',
                    'v_bits': 'u128',
                },
                'SessionSettlementDropped': {
                    'payout': 'u128',
                    'session': 'AccountId',
                    'v': 'u128',
                },
                'SessionUnbound': {
                    'session': 'AccountId',
                    'worker': '[u8; 32]',
                },
                'SubsidyBudgetHalved': None,
                'TokenomicParametersChanged': None,
                'WorkerEnterUnresponsive': {'session': 'AccountId'},
                'WorkerExitUnresponsive': {'session': 'AccountId'},
                'WorkerReclaimed': {
                    'original_stake': 'u128',
                    'session': 'AccountId',
                    'slashed': 'u128',
                },
                'WorkerStarted': {
                    'init_p': 'u32',
                    'init_v': 'u128',
                    'session': 'AccountId',
                },
                'WorkerStopped': {'session': 'AccountId'},
            },
            'PhalaPhatContracts': {
                'ClusterCreated': {
                    'cluster': 'scale_info::12',
                    'system_contract': 'scale_info::12',
                },
                'ClusterDeployed': {
                    'cluster': 'scale_info::12',
                    'pubkey': '[u8; 32]',
                    'worker': '[u8; 32]',
                },
                'ClusterDeploymentFailed': {
                    'cluster': 'scale_info::12',
                    'worker': '[u8; 32]',
                },
                'ClusterDestroyed': {'cluster': 'scale_info::12'},
                'ClusterPubkeyAvailable': {
                    'cluster': 'scale_info::12',
                    'pubkey': '[u8; 32]',
                },
                'ContractPubkeyAvailable': {
                    'cluster': 'scale_info::12',
                    'contract': 'scale_info::12',
                    'pubkey': '[u8; 32]',
                },
                'Instantiated': {
                    'cluster': 'scale_info::12',
                    'contract': 'scale_info::12',
                    'deployer': 'scale_info::12',
                },
                'Instantiating': {
                    'cluster': 'scale_info::12',
                    'contract': 'scale_info::12',
                    'deployer': 'AccountId',
                },
                'Transfered': {
                    'account': 'scale_info::12',
                    'amount': 'u128',
                    'cluster': 'scale_info::12',
                },
                'WorkerAddedToCluster': {
                    'cluster': 'scale_info::12',
                    'worker': '[u8; 32]',
                },
                'WorkerRemovedFromCluster': {
                    'cluster': 'scale_info::12',
                    'worker': '[u8; 32]',
                },
            },
            'PhalaPhatTokenomic': {
                'ContractDepositChanged': {
                    'cluster': (None, 'scale_info::12'),
                    'contract': 'scale_info::12',
                    'deposit': 'u128',
                },
                'UserStakeChanged': {
                    'account': 'AccountId',
                    'cluster': (None, 'scale_info::12'),
                    'contract': 'scale_info::12',
                    'stake': 'u128',
                },
            },
            'PhalaRegistry': {
                'GatekeeperAdded': {'pubkey': '[u8; 32]'},
                'GatekeeperLaunched': None,
                'GatekeeperRemoved': {'pubkey': '[u8; 32]'},
                'InitialScoreSet': {'init_score': 'u32', 'pubkey': '[u8; 32]'},
                'MasterKeyRotated': {
                    'master_pubkey': '[u8; 32]',
                    'rotation_id': 'u64',
                },
                'MasterKeyRotationFailed': {
                    'gatekeeper_rotation_id': 'u64',
                    'rotation_lock': (None, 'u64'),
                },
                'MinimumPRuntimeVersionChangedTo': ('u32', 'u32', 'u32'),
                'PRuntimeConsensusVersionChangedTo': 'u32',
                'WorkerAdded': {
                    'attestation_provider': (None, 'scale_info::139'),
                    'confidence_level': 'u8',
                    'pubkey': '[u8; 32]',
                },
                'WorkerUpdated': {
                    'attestation_provider': (None, 'scale_info::139'),
                    'confidence_level': 'u8',
                    'pubkey': '[u8; 32]',
                },
            },
            'PhalaStakePool': (),
            'PhalaStakePoolv2': {
                'Contribution': {
                    'amount': 'u128',
                    'as_vault': (None, 'u64'),
                    'pid': 'u64',
                    'shares': 'u128',
                    'user': 'AccountId',
                },
                'OwnerRewardsWithdrawn': {
                    'amount': 'u128',
                    'pid': 'u64',
                    'user': 'AccountId',
                },
                'PoolCapacitySet': {'cap': 'u128', 'pid': 'u64'},
                'PoolCommissionSet': {'commission': 'u32', 'pid': 'u64'},
                'PoolCreated': {
                    'cid': 'u32',
                    'owner': 'AccountId',
                    'pid': 'u64',
                    'pool_account_id': 'AccountId',
                },
                'PoolSlashed': {'amount': 'u128', 'pid': 'u64'},
                'PoolWorkerAdded': {
                    'pid': 'u64',
                    'session': 'AccountId',
                    'worker': '[u8; 32]',
                },
                'PoolWorkerRemoved': {'pid': 'u64', 'worker': '[u8; 32]'},
                'RewardDismissedDust': {'amount': 'u128', 'pid': 'u64'},
                'RewardDismissedNoShare': {'amount': 'u128', 'pid': 'u64'},
                'RewardDismissedNotInPool': {
                    'amount': 'u128',
                    'worker': '[u8; 32]',
                },
                'RewardReceived': {
                    'pid': 'u64',
                    'to_owner': 'u128',
                    'to_stakers': 'u128',
                },
                'RewardToDistributionDismissedDust': {
                    'amount': 'u128',
                    'pid': 'u64',
                },
                'RewardToOwnerDismissedDust': {'amount': 'u128', 'pid': 'u64'},
                'SlashSettled': {
                    'amount': 'u128',
                    'pid': 'u64',
                    'user': 'AccountId',
                },
                'WorkerReclaimed': {'pid': 'u64', 'worker': '[u8; 32]'},
                'WorkingStarted': {
                    'amount': 'u128',
                    'pid': 'u64',
                    'worker': '[u8; 32]',
                },
            },
            'PhalaVault': {
                'Contribution': {
                    'amount': 'u128',
                    'pid': 'u64',
                    'shares': 'u128',
                    'user': 'AccountId',
                },
                'ForceShutdown': {'pid': 'u64', 'reason': 'scale_info::145'},
                'OwnerSharesClaimed': {
                    'pid': 'u64',
                    'shares': 'u128',
                    'user': 'AccountId',
                },
                'OwnerSharesGained': {
                    'checkout_price': 'u128',
                    'pid': 'u64',
                    'shares': 'u128',
                },
                'PoolCreated': {
                    'cid': 'u32',
                    'owner': 'AccountId',
                    'pid': 'u64',
                    'pool_account_id': 'AccountId',
                },
                'VaultCommissionSet': {'commission': 'u32', 'pid': 'u64'},
            },
            'PhalaWrappedBalances': {
                'DustRemoved': {'amount': 'u128', 'user': 'AccountId'},
                'Unwrapped': {'amount': 'u128', 'user': 'AccountId'},
                'Voted': {
                    'aye_amount': 'u128',
                    'nay_amount': 'u128',
                    'user': 'AccountId',
                    'vote_id': 'u32',
                },
                'Wrapped': {'amount': 'u128', 'user': 'AccountId'},
            },
            'PhragmenElection': {
                'CandidateSlashed': {
                    'amount': 'u128',
                    'candidate': 'AccountId',
                },
                'ElectionError': None,
                'EmptyTerm': None,
                'MemberKicked': {'member': 'AccountId'},
                'NewTerm': {'new_members': [('AccountId', 'u128')]},
                'Renounced': {'candidate': 'AccountId'},
                'SeatHolderSlashed': {
                    'amount': 'u128',
                    'seat_holder': 'AccountId',
                },
            },
            'PolkadotXcm': {
                'AssetsClaimed': {
                    'assets': 'scale_info::90',
                    'hash': 'scale_info::12',
                    'origin': 'scale_info::51',
                },
                'AssetsTrapped': {
                    'assets': 'scale_info::90',
                    'hash': 'scale_info::12',
                    'origin': 'scale_info::51',
                },
                'Attempted': {'outcome': 'scale_info::48'},
                'FeesPaid': {'fees': ['scale_info::66'], 'paying': 'scale_info::51'},
                'InvalidQuerier': {
                    'expected_querier': 'scale_info::51',
                    'maybe_actual_querier': (None, 'scale_info::51'),
                    'origin': 'scale_info::51',
                    'query_id': 'u64',
                },
                'InvalidQuerierVersion': {
                    'origin': 'scale_info::51',
                    'query_id': 'u64',
                },
                'InvalidResponder': {
                    'expected_location': (None, 'scale_info::51'),
                    'origin': 'scale_info::51',
                    'query_id': 'u64',
                },
                'InvalidResponderVersion': {
                    'origin': 'scale_info::51',
                    'query_id': 'u64',
                },
                'Notified': {
                    'call_index': 'u8',
                    'pallet_index': 'u8',
                    'query_id': 'u64',
                },
                'NotifyDecodeFailed': {
                    'call_index': 'u8',
                    'pallet_index': 'u8',
                    'query_id': 'u64',
                },
                'NotifyDispatchError': {
                    'call_index': 'u8',
                    'pallet_index': 'u8',
                    'query_id': 'u64',
                },
                'NotifyOverweight': {
                    'actual_weight': 'scale_info::9',
                    'call_index': 'u8',
                    'max_budgeted_weight': 'scale_info::9',
                    'pallet_index': 'u8',
                    'query_id': 'u64',
                },
                'NotifyTargetMigrationFail': {
                    'location': 'scale_info::104',
                    'query_id': 'u64',
                },
                'NotifyTargetSendFail': {
                    'error': 'scale_info::45',
                    'location': 'scale_info::51',
                    'query_id': 'u64',
                },
                'ResponseReady': {
                    'query_id': 'u64',
                    'response': 'scale_info::72',
                },
                'ResponseTaken': {'query_id': 'u64'},
                'Sent': {
                    'destination': 'scale_info::51',
                    'message': ['scale_info::63'],
                    'message_id': '[u8; 32]',
                    'origin': 'scale_info::51',
                },
                'SupportedVersionChanged': {
                    'location': 'scale_info::51',
                    'version': 'u32',
                },
                'UnexpectedResponse': {
                    'origin': 'scale_info::51',
                    'query_id': 'u64',
                },
                'VersionChangeNotified': {
                    'cost': ['scale_info::66'],
                    'destination': 'scale_info::51',
                    'message_id': '[u8; 32]',
                    'result': 'u32',
                },
                'VersionNotifyRequested': {
                    'cost': ['scale_info::66'],
                    'destination': 'scale_info::51',
                    'message_id': '[u8; 32]',
                },
                'VersionNotifyStarted': {
                    'cost': ['scale_info::66'],
                    'destination': 'scale_info::51',
                    'message_id': '[u8; 32]',
                },
                'VersionNotifyUnrequested': {
                    'cost': ['scale_info::66'],
                    'destination': 'scale_info::51',
                    'message_id': '[u8; 32]',
                },
            },
            'Preimage': {
                'Cleared': {'hash': 'scale_info::12'},
                'Noted': {'hash': 'scale_info::12'},
                'Requested': {'hash': 'scale_info::12'},
            },
            'Proxy': {
                'Announced': {
                    'call_hash': 'scale_info::12',
                    'proxy': 'AccountId',
                    'real': 'AccountId',
                },
                'ProxyAdded': {
                    'delay': 'u32',
                    'delegatee': 'AccountId',
                    'delegator': 'AccountId',
                    'proxy_type': 'scale_info::36',
                },
                'ProxyExecuted': {'result': 'scale_info::31'},
                'ProxyRemoved': {
                    'delay': 'u32',
                    'delegatee': 'AccountId',
                    'delegator': 'AccountId',
                    'proxy_type': 'scale_info::36',
                },
                'PureCreated': {
                    'disambiguation_index': 'u16',
                    'proxy_type': 'scale_info::36',
                    'pure': 'AccountId',
                    'who': 'AccountId',
                },
            },
            'RmrkCore': {
                'CollectionCreated': {
                    'collection_id': 'u32',
                    'issuer': 'AccountId',
                },
                'CollectionDestroyed': {
                    'collection_id': 'u32',
                    'issuer': 'AccountId',
                },
                'CollectionLocked': {
                    'collection_id': 'u32',
                    'issuer': 'AccountId',
                },
                'IssuerChanged': {
                    'collection_id': 'u32',
                    'new_issuer': 'AccountId',
                    'old_issuer': 'AccountId',
                },
                'NFTAccepted': {
                    'collection_id': 'u32',
                    'nft_id': 'u32',
                    'recipient': 'scale_info::159',
                    'sender': 'AccountId',
                },
                'NFTBurned': {
                    'collection_id': 'u32',
                    'nft_id': 'u32',
                    'owner': 'AccountId',
                },
                'NFTRejected': {
                    'collection_id': 'u32',
                    'nft_id': 'u32',
                    'sender': 'AccountId',
                },
                'NFTSent': {
                    'approval_required': 'bool',
                    'collection_id': 'u32',
                    'nft_id': 'u32',
                    'recipient': 'scale_info::159',
                    'sender': 'AccountId',
                },
                'NftMinted': {
                    'collection_id': 'u32',
                    'nft_id': 'u32',
                    'owner': 'scale_info::159',
                },
                'PrioritySet': {'collection_id': 'u32', 'nft_id': 'u32'},
                'PropertiesRemoved': {
                    'collection_id': 'u32',
                    'maybe_nft_id': (None, 'u32'),
                },
                'PropertyRemoved': {
                    'collection_id': 'u32',
                    'key': 'Bytes',
                    'maybe_nft_id': (None, 'u32'),
                },
                'PropertySet': {
                    'collection_id': 'u32',
                    'key': 'Bytes',
                    'maybe_nft_id': (None, 'u32'),
                    'value': 'Bytes',
                },
                'ResourceAccepted': {
                    'collection_id': 'u32',
                    'nft_id': 'u32',
                    'resource_id': 'u32',
                },
                'ResourceAdded': {
                    'collection_id': 'u32',
                    'nft_id': 'u32',
                    'resource_id': 'u32',
                },
                'ResourceRemoval': {
                    'collection_id': 'u32',
                    'nft_id': 'u32',
                    'resource_id': 'u32',
                },
                'ResourceRemovalAccepted': {
                    'collection_id': 'u32',
                    'nft_id': 'u32',
                    'resource_id': 'u32',
                },
                'ResourceReplaced': {
                    'collection_id': 'u32',
                    'nft_id': 'u32',
                    'resource_id': 'u32',
                },
            },
            'RmrkEquip': {
                'BaseCreated': {'base_id': 'u32', 'issuer': 'AccountId'},
                'BaseIssuerChanged': {
                    'base_id': 'u32',
                    'new_issuer': 'AccountId',
                    'old_issuer': 'AccountId',
                },
                'EquippablesUpdated': {'base_id': 'u32', 'slot_id': 'u32'},
                'SlotEquipped': {
                    'base_id': 'u32',
                    'item_collection': 'u32',
                    'item_nft': 'u32',
                    'slot_id': 'u32',
                },
                'SlotUnequipped': {
                    'base_id': 'u32',
                    'item_collection': 'u32',
                    'item_nft': 'u32',
                    'slot_id': 'u32',
                },
            },
            'RmrkMarket': {
                'MarketFeePaid': {
                    'amount': 'u128',
                    'collection_id': 'u32',
                    'marketplace_owner': 'AccountId',
                    'nft_id': 'u32',
                    'sender': 'AccountId',
                },
                'OfferAccepted': {
                    'buyer': 'AccountId',
                    'collection_id': 'u32',
                    'nft_id': 'u32',
                    'owner': 'AccountId',
                },
                'OfferPlaced': {
                    'collection_id': 'u32',
                    'nft_id': 'u32',
                    'offerer': 'AccountId',
                    'price': 'u128',
                },
                'OfferWithdrawn': {
                    'collection_id': 'u32',
                    'nft_id': 'u32',
                    'sender': 'AccountId',
                },
                'RoyaltyFeePaid': {
                    'amount': 'u128',
                    'collection_id': 'u32',
                    'nft_id': 'u32',
                    'royalty_owner': 'AccountId',
                    'sender': 'AccountId',
                },
                'TokenListed': {
                    'collection_id': 'u32',
                    'nft_id': 'u32',
                    'owner': 'AccountId',
                    'price': 'u128',
                },
                'TokenPriceUpdated': {
                    'collection_id': 'u32',
                    'nft_id': 'u32',
                    'owner': 'AccountId',
                    'price': (None, 'u128'),
                },
                'TokenSold': {
                    'buyer': 'AccountId',
                    'collection_id': 'u32',
                    'nft_id': 'u32',
                    'owner': 'AccountId',
                    'price': 'u128',
                },
                'TokenUnlisted': {
                    'collection_id': 'u32',
                    'nft_id': 'u32',
                    'owner': 'AccountId',
                },
            },
            'Scheduler': {
                'CallUnavailable': {
                    'id': (None, '[u8; 32]'),
                    'task': ('u32', 'u32'),
                },
                'Canceled': {'index': 'u32', 'when': 'u32'},
                'Dispatched': {
                    'id': (None, '[u8; 32]'),
                    'result': 'scale_info::31',
                    'task': ('u32', 'u32'),
                },
                'PeriodicFailed': {
                    'id': (None, '[u8; 32]'),
                    'task': ('u32', 'u32'),
                },
                'PermanentlyOverweight': {
                    'id': (None, '[u8; 32]'),
                    'task': ('u32', 'u32'),
                },
                'Scheduled': {'index': 'u32', 'when': 'u32'},
            },
            'Session': {'NewSession': {'session_index': 'u32'}},
            'SygmaAccessSegregator': {
                'AccessGranted': {
                    'extrinsic_name': 'Bytes',
                    'pallet_index': 'u8',
                    'who': 'AccountId',
                },
            },
            'SygmaBasicFeeHandler': {
                'FeeSet': {
                    'amount': 'u128',
                    'asset': 'scale_info::67',
                    'domain': 'u8',
                },
            },
            'SygmaBridge': {
                'AllBridgePaused': {'sender': 'AccountId'},
                'AllBridgeUnpaused': {'sender': 'AccountId'},
                'BridgePaused': {'dest_domain_id': 'u8'},
                'BridgeUnpaused': {'dest_domain_id': 'u8'},
                'Deposit': {
                    'deposit_data': 'Bytes',
                    'deposit_nonce': 'u64',
                    'dest_domain_id': 'u8',
                    'handler_response': 'Bytes',
                    'resource_id': '[u8; 32]',
                    'sender': 'AccountId',
                    'transfer_type': 'scale_info::166',
                },
                'FailedHandlerExecution': {
                    'deposit_nonce': 'u64',
                    'error': 'Bytes',
                    'origin_domain_id': 'u8',
                },
                'FeeCollected': {
                    'dest_domain_id': 'u8',
                    'fee_amount': 'u128',
                    'fee_asset_id': 'scale_info::67',
                    'fee_payer': 'AccountId',
                    'resource_id': '[u8; 32]',
                },
                'ProposalExecution': {
                    'data_hash': '[u8; 32]',
                    'deposit_nonce': 'u64',
                    'origin_domain_id': 'u8',
                },
                'RegisterDestDomain': {
                    'chain_id': 'scale_info::131',
                    'domain_id': 'u8',
                    'sender': 'AccountId',
                },
                'Retry': {
                    'deposit_on_block_height': 'u128',
                    'dest_domain_id': 'u8',
                    'sender': 'AccountId',
                },
                'UnregisterDestDomain': {
                    'chain_id': 'scale_info::131',
                    'domain_id': 'u8',
                    'sender': 'AccountId',
                },
            },
            'SygmaFeeHandlerRouter': {
                'FeeHandlerSet': {
                    'asset': 'scale_info::67',
                    'domain': 'u8',
                    'handler_type': 'scale_info::168',
                },
            },
            'SygmaPercentageFeeHandler': {
                'FeeRateSet': {
                    'asset': 'scale_info::67',
                    'domain': 'u8',
                    'fee_lower_bound': 'u128',
                    'fee_upper_bound': 'u128',
                    'rate_basis_point': 'u32',
                },
            },
            'SygmaWrapper': {
                'AssetTransfered': {
                    'asset': 'scale_info::66',
                    'dest': 'scale_info::51',
                    'origin': 'scale_info::51',
                },
            },
            'System': {
                'CodeUpdated': None,
                'ExtrinsicFailed': {
                    'dispatch_error': 'scale_info::25',
                    'dispatch_info': 'scale_info::22',
                },
                'ExtrinsicSuccess': {'dispatch_info': 'scale_info::22'},
                'KilledAccount': {'account': 'AccountId'},
                'NewAccount': {'account': 'AccountId'},
                'Remarked': {'hash': 'scale_info::12', 'sender': 'AccountId'},
            },
            'TechnicalCommittee': {
                'Approved': {'proposal_hash': 'scale_info::12'},
                'Closed': {
                    'no': 'u32',
                    'proposal_hash': 'scale_info::12',
                    'yes': 'u32',
                },
                'Disapproved': {'proposal_hash': 'scale_info::12'},
                'Executed': {
                    'proposal_hash': 'scale_info::12',
                    'result': 'scale_info::31',
                },
                'MemberExecuted': {
                    'proposal_hash': 'scale_info::12',
                    'result': 'scale_info::31',
                },
                'Proposed': {
                    'account': 'AccountId',
                    'proposal_hash': 'scale_info::12',
                    'proposal_index': 'u32',
                    'threshold': 'u32',
                },
                'Voted': {
                    'account': 'AccountId',
                    'no': 'u32',
                    'proposal_hash': 'scale_info::12',
                    'voted': 'bool',
                    'yes': 'u32',
                },
            },
            'TechnicalMembership': (
                'MemberAdded',
                'MemberRemoved',
                'MembersSwapped',
                'MembersReset',
                'KeyChanged',
                'Dummy',
            ),
            'Tips': {
                'NewTip': {'tip_hash': 'scale_info::12'},
                'TipClosed': {
                    'payout': 'u128',
                    'tip_hash': 'scale_info::12',
                    'who': 'AccountId',
                },
                'TipClosing': {'tip_hash': 'scale_info::12'},
                'TipRetracted': {'tip_hash': 'scale_info::12'},
                'TipSlashed': {
                    'deposit': 'u128',
                    'finder': 'AccountId',
                    'tip_hash': 'scale_info::12',
                },
            },
            'TransactionPayment': {
                'TransactionFeePaid': {
                    'actual_fee': 'u128',
                    'tip': 'u128',
                    'who': 'AccountId',
                },
            },
            'Treasury': {
                'Awarded': {
                    'account': 'AccountId',
                    'award': 'u128',
                    'proposal_index': 'u32',
                },
                'Burnt': {'burnt_funds': 'u128'},
                'Deposit': {'value': 'u128'},
                'Proposed': {'proposal_index': 'u32'},
                'Rejected': {'proposal_index': 'u32', 'slashed': 'u128'},
                'Rollover': {'rollover_balance': 'u128'},
                'SpendApproved': {
                    'amount': 'u128',
                    'beneficiary': 'AccountId',
                    'proposal_index': 'u32',
                },
                'Spending': {'budget_remaining': 'u128'},
                'UpdatedInactive': {
                    'deactivated': 'u128',
                    'reactivated': 'u128',
                },
            },
            'Uniques': {
                'ApprovalCancelled': {
                    'collection': 'u32',
                    'delegate': 'AccountId',
                    'item': 'u32',
                    'owner': 'AccountId',
                },
                'ApprovedTransfer': {
                    'collection': 'u32',
                    'delegate': 'AccountId',
                    'item': 'u32',
                    'owner': 'AccountId',
                },
                'AttributeCleared': {
                    'collection': 'u32',
                    'key': 'Bytes',
                    'maybe_item': (None, 'u32'),
                },
                'AttributeSet': {
                    'collection': 'u32',
                    'key': 'Bytes',
                    'maybe_item': (None, 'u32'),
                    'value': 'Bytes',
                },
                'Burned': {
                    'collection': 'u32',
                    'item': 'u32',
                    'owner': 'AccountId',
                },
                'CollectionFrozen': {'collection': 'u32'},
                'CollectionMaxSupplySet': {
                    'collection': 'u32',
                    'max_supply': 'u32',
                },
                'CollectionMetadataCleared': {'collection': 'u32'},
                'CollectionMetadataSet': {
                    'collection': 'u32',
                    'data': 'Bytes',
                    'is_frozen': 'bool',
                },
                'CollectionThawed': {'collection': 'u32'},
                'Created': {
                    'collection': 'u32',
                    'creator': 'AccountId',
                    'owner': 'AccountId',
                },
                'Destroyed': {'collection': 'u32'},
                'ForceCreated': {'collection': 'u32', 'owner': 'AccountId'},
                'Frozen': {'collection': 'u32', 'item': 'u32'},
                'Issued': {
                    'collection': 'u32',
                    'item': 'u32',
                    'owner': 'AccountId',
                },
                'ItemBought': {
                    'buyer': 'AccountId',
                    'collection': 'u32',
                    'item': 'u32',
                    'price': 'u128',
                    'seller': 'AccountId',
                },
                'ItemPriceRemoved': {'collection': 'u32', 'item': 'u32'},
                'ItemPriceSet': {
                    'collection': 'u32',
                    'item': 'u32',
                    'price': 'u128',
                    'whitelisted_buyer': (None, 'AccountId'),
                },
                'ItemStatusChanged': {'collection': 'u32'},
                'MetadataCleared': {'collection': 'u32', 'item': 'u32'},
                'MetadataSet': {
                    'collection': 'u32',
                    'data': 'Bytes',
                    'is_frozen': 'bool',
                    'item': 'u32',
                },
                'OwnerChanged': {
                    'collection': 'u32',
                    'new_owner': 'AccountId',
                },
                'OwnershipAcceptanceChanged': {
                    'maybe_collection': (None, 'u32'),
                    'who': 'AccountId',
                },
                'Redeposited': {
                    'collection': 'u32',
                    'successful_items': ['u32'],
                },
                'TeamChanged': {
                    'admin': 'AccountId',
                    'collection': 'u32',
                    'freezer': 'AccountId',
                    'issuer': 'AccountId',
                },
                'Thawed': {'collection': 'u32', 'item': 'u32'},
                'Transferred': {
                    'collection': 'u32',
                    'from': 'AccountId',
                    'item': 'u32',
                    'to': 'AccountId',
                },
            },
            'Utility': {
                'BatchCompleted': None,
                'BatchCompletedWithErrors': None,
                'BatchInterrupted': {
                    'error': 'scale_info::25',
                    'index': 'u32',
                },
                'DispatchedAs': {'result': 'scale_info::31'},
                'ItemCompleted': None,
                'ItemFailed': {'error': 'scale_info::25'},
            },
            'Vesting': {
                'VestingCompleted': {'account': 'AccountId'},
                'VestingUpdated': {'account': 'AccountId', 'unvested': 'u128'},
            },
            'XTransfer': {
                'Deposited': {
                    'memo': 'Bytes',
                    'what': 'scale_info::66',
                    'who': 'scale_info::51',
                },
                'Forwarded': {
                    'memo': 'Bytes',
                    'what': 'scale_info::66',
                    'who': 'scale_info::51',
                },
                'Withdrawn': {
                    'memo': 'Bytes',
                    'what': 'scale_info::66',
                    'who': 'scale_info::51',
                },
            },
            'XcmBridge': {
                'AssetTransfered': {
                    'asset': 'scale_info::66',
                    'dest': 'scale_info::51',
                    'origin': 'scale_info::51',
                },
            },
            'XcmpQueue': {
                'BadFormat': {'message_hash': '[u8; 32]'},
                'BadVersion': {'message_hash': '[u8; 32]'},
                'Fail': {
                    'error': 'scale_info::45',
                    'message_hash': '[u8; 32]',
                    'message_id': '[u8; 32]',
                    'weight': 'scale_info::9',
                },
                'OverweightEnqueued': {
                    'index': 'u64',
                    'required': 'scale_info::9',
                    'sender': 'u32',
                    'sent_at': 'u32',
                },
                'OverweightServiced': {
                    'index': 'u64',
                    'used': 'scale_info::9',
                },
                'Success': {
                    'message_hash': '[u8; 32]',
                    'message_id': '[u8; 32]',
                    'weight': 'scale_info::9',
                },
                'XcmpMessageSent': {'message_hash': '[u8; 32]'},
            },
        },
        'phase': {
            'ApplyExtrinsic': 'u32',
            'Finalization': None,
            'Initialization': None,
        },
        'topics': ['scale_info::12'],
    },
]
```
---------
### ExecutionPhase
 The execution phase of the block.

#### Python
```python
result = substrate.query(
    'System', 'ExecutionPhase', []
)
```

#### Return value
```python
{'ApplyExtrinsic': 'u32', 'Finalization': None, 'Initialization': None}
```
---------
### ExtrinsicCount
 Total extrinsics count for the current block.

#### Python
```python
result = substrate.query(
    'System', 'ExtrinsicCount', []
)
```

#### Return value
```python
'u32'
```
---------
### ExtrinsicData
 Extrinsics data for the current block (maps an extrinsic&#x27;s index to its data).

#### Python
```python
result = substrate.query(
    'System', 'ExtrinsicData', ['u32']
)
```

#### Return value
```python
'Bytes'
```
---------
### LastRuntimeUpgrade
 Stores the `spec_version` and `spec_name` of when the last runtime upgrade happened.

#### Python
```python
result = substrate.query(
    'System', 'LastRuntimeUpgrade', []
)
```

#### Return value
```python
{'spec_name': 'Str', 'spec_version': 'u32'}
```
---------
### Number
 The current block number being processed. Set by `execute_block`.

#### Python
```python
result = substrate.query(
    'System', 'Number', []
)
```

#### Return value
```python
'u32'
```
---------
### ParentHash
 Hash of the previous block.

#### Python
```python
result = substrate.query(
    'System', 'ParentHash', []
)
```

#### Return value
```python
'scale_info::12'
```
---------
### UpgradedToTripleRefCount
 True if we have upgraded so that AccountInfo contains three types of `RefCount`. False
 (default) if not.

#### Python
```python
result = substrate.query(
    'System', 'UpgradedToTripleRefCount', []
)
```

#### Return value
```python
'bool'
```
---------
### UpgradedToU32RefCount
 True if we have upgraded so that `type RefCount` is `u32`. False (default) if not.

#### Python
```python
result = substrate.query(
    'System', 'UpgradedToU32RefCount', []
)
```

#### Return value
```python
'bool'
```
---------
## Constants

---------
### BlockHashCount
 Maximum number of block number to block hash mappings to keep (oldest pruned first).
#### Value
```python
1200
```
#### Python
```python
constant = substrate.get_constant('System', 'BlockHashCount')
```
---------
### BlockLength
 The maximum length of a block (in bytes).
#### Value
```python
{'max': {'mandatory': 5242880, 'normal': 3932160, 'operational': 5242880}}
```
#### Python
```python
constant = substrate.get_constant('System', 'BlockLength')
```
---------
### BlockWeights
 Block &amp; extrinsics weights: base values and limits.
#### Value
```python
{
    'base_block': {'proof_size': 0, 'ref_time': 390584000},
    'max_block': {'proof_size': 5242880, 'ref_time': 500000000000},
    'per_class': {
        'mandatory': {
            'base_extrinsic': {'proof_size': 0, 'ref_time': 124414000},
            'max_extrinsic': None,
            'max_total': None,
            'reserved': None,
        },
        'normal': {
            'base_extrinsic': {'proof_size': 0, 'ref_time': 124414000},
            'max_extrinsic': {'proof_size': 3670016, 'ref_time': 349875586000},
            'max_total': {'proof_size': 3932160, 'ref_time': 375000000000},
            'reserved': {'proof_size': 0, 'ref_time': 0},
        },
        'operational': {
            'base_extrinsic': {'proof_size': 0, 'ref_time': 124414000},
            'max_extrinsic': {'proof_size': 4980736, 'ref_time': 474875586000},
            'max_total': {'proof_size': 5242880, 'ref_time': 500000000000},
            'reserved': {'proof_size': 1310720, 'ref_time': 125000000000},
        },
    },
}
```
#### Python
```python
constant = substrate.get_constant('System', 'BlockWeights')
```
---------
### DbWeight
 The weight of runtime database operations the runtime can invoke.
#### Value
```python
{'read': 25000000, 'write': 100000000}
```
#### Python
```python
constant = substrate.get_constant('System', 'DbWeight')
```
---------
### SS58Prefix
 The designated SS58 prefix of this chain.

 This replaces the &quot;ss58Format&quot; property declared in the chain spec. Reason is
 that the runtime should know about the prefix in order to make use of it as
 an identifier of the chain.
#### Value
```python
30
```
#### Python
```python
constant = substrate.get_constant('System', 'SS58Prefix')
```
---------
### Version
 Get the chain&#x27;s current version.
#### Value
```python
{
    'apis': [
        ('0xdd718d5cc53262d4', 1),
        ('0xdf6acb689907609b', 4),
        ('0x37e397fc7c91f5e4', 2),
        ('0x40fe3ad401f8959a', 6),
        ('0xd2bc9897eed08f15', 3),
        ('0xf78b278be53f454c', 2),
        ('0xab3c0572291feb8b', 1),
        ('0xbc9d89904f5b923f', 1),
        ('0x37c8bb1350a9a2a8', 4),
        ('0x3e43e696bccaa34a', 1),
        ('0xea93e3f16f3d6962', 2),
        ('0x643365445941c5cb', 1),
        ('0x7ee4fdd3f4b9d4d0', 1),
        ('0xfbc577b9d747efd6', 1),
    ],
    'authoring_version': 1,
    'impl_name': 'phala',
    'impl_version': 0,
    'spec_name': 'phala',
    'spec_version': 1263,
    'state_version': 0,
    'transaction_version': 5,
}
```
#### Python
```python
constant = substrate.get_constant('System', 'Version')
```
---------
## Errors

---------
### CallFiltered
The origin filter prevent the call to be dispatched.

---------
### FailedToExtractRuntimeVersion
Failed to extract the runtime version from the new runtime.

Either calling `Core_version` or decoding `RuntimeVersion` failed.

---------
### InvalidSpecName
The name of specification does not match between the current runtime
and the new runtime.

---------
### NonDefaultComposite
Suicide called when the account has non-default composite data.

---------
### NonZeroRefCount
There is a non-zero reference count preventing the account from being purged.

---------
### SpecVersionNeedsToIncrease
The specification version is not allowed to decrease between the current runtime
and the new runtime.

---------